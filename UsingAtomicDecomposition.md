# Atomic Decomposition usage #

Atomic Decomposition (AD) is a method to partition an ontology into pieces called _atoms_. Atom is a set of axioms that appears in every module all together (or none of them). They could be viewed as a smallest pieces of modules.

FaCT++ provides 3 methods to create and work with an AD:
  * `int getAtomicDecompositionSize(boolean useSemanticLocality, int moduleType);` creates the AD of the ontology already loaded into reasoner according to parameters. After the AD is created, it returns size of the AD. All the atoms can be accessed via index.
  * `Set<OWLAxiom> getAtomAxioms(int atomIndex);` returns all the axioms of an atom with index `atomIndex`
  * `int[] getAtomDependents(int atomIndex);` returns all the atoms on which an atom with index `atomIndex` _directly depends_. That is, it represents the part of transitively reduced dependency relation that starts on a given atom and has depth 1. See below in the code how to get all the dependencies of a given atom.

# Code example #

Here is the usage example of the methods described above. There are 2 methods in this example:
  * `PrintAtomicDecomposition();` just creates an AD of a given ontology and prints it;
  * `PrintAxiomModule();` creates an AD and uses it to determine a module of a given axiom.


```
import java.util.*;

import org.semanticweb.owlapi.model.*;
import org.semanticweb.owlapi.reasoner.OWLReasoner;

import uk.ac.manchester.cs.factplusplus.owlapiv3.*;

public class FaCTPlusPlusTutorial {

	/**
	 * A method to show the work with Atomic Decomposition interface.
	 * 
	 * Prints the whole AD of an ontology O. AD is performed according to
	 * parameters.
	 * 
	 * @param o
	 *            An ontology to be decomposed
	 * @param useSemanticLocality
	 *            if true, use semantic locality checking for axioms; if false,
	 *            use syntactic locality checker. In the FaCT++ implementation
	 *            semantic locality checking is 3-5 times slower than syntactic
	 *            with very small influence. If in doubt, use syntactic one.
	 * @param moduleType
	 *            Defines a type of an atomic decomposition. 0 means BOTTOM, 1
	 *            means TOP, 2 means STAR. The choice of a type depends very
	 *            much on an application. In general, STAR generates the
	 *            smallest modules, while BOTTOM are usually the fastest (and
	 *            rather small as well). If in doubt, use BOTTOM.
	 */
	void PrintAtomicDecomposition(OWLOntology o, boolean useSemanticLocality, int moduleType) {
		// create FaCT++ reasoner with the ontology loaded
		OWLReasoner reasoner = new FaCTPlusPlusReasonerFactory().createReasoner(o);

		// cast a reasoner as OWLReasoner interface does not provide atomic
		// decomposition ability
		FaCTPlusPlusReasoner fpp = (FaCTPlusPlusReasoner) reasoner;

		// decompose an ontology O using given parameters.
		// get the number of atoms in the AD.
		int nAtoms = fpp.getAtomicDecompositionSize(useSemanticLocality, moduleType);

		for (int i = 0; i < nAtoms; i++) {
			// get all the axioms of a given the atom
			System.out.println("Atom " + i + " has axioms: " + fpp.getAtomAxioms(i));
			// get all the atoms a given one depends on
			System.out.println("Atom " + i + " depends on: " + fpp.getAtomDependents(i));
		}
	}

	/**
	 * A method to show the work with Atomic Decomposition interface.
	 * 
	 * Prints a module of an ontology O for a given axiom A
	 * 
	 * @param o
	 *            An ontology to be decomposed
	 * @param a
	 *            An axiom to determine the module for
	 * @param useSemanticLocality
	 *            if true, use semantic locality checking for axioms; if false,
	 *            use syntactic locality checker. In the FaCT++ implementation
	 *            semantic locality checking is 3-5 times slower than syntactic
	 *            with very small influence. If in doubt, use syntactic one.
	 * @param moduleType
	 *            Defines a type of an atomic decomposition. 0 means BOTTOM, 1
	 *            means TOP, 2 means STAR. The choice of a type depends very
	 *            much on an application. In general, STAR generates the
	 *            smallest modules, while BOTTOM are usually the fastest (and
	 *            rather small as well). If in doubt, use BOTTOM.
	 */
	void PrintAxiomModule(OWLOntology o, OWLAxiom a, boolean useSemanticLocality, int moduleType) {
		// only logical axioms can appear in a module
		if (!a.isLogicalAxiom()) {
			System.out.println("Axiom " + a + " is non-logical; no module for it");
			return;
		}

		// create FaCT++ reasoner with the ontology loaded
		OWLReasoner reasoner = new FaCTPlusPlusReasonerFactory().createReasoner(o);

		// cast a reasoner as OWLReasoner interface does not provide atomic
		// decomposition ability
		FaCTPlusPlusReasoner fpp = (FaCTPlusPlusReasoner) reasoner;

		// decompose an ontology O using given parameters.
		// get the number of atoms in the AD.
		int nAtoms = fpp.getAtomicDecompositionSize(useSemanticLocality, moduleType);

		// determine an atom which contain given axiom
		int axAtom;
		for (axAtom = 0; axAtom < nAtoms; axAtom++) {
			if (fpp.getAtomAxioms(axAtom).contains(a))
				break;
		}

		// if there is no such atom, then the axiom is a tautology
		if (axAtom == nAtoms) {
			System.out.println("Axiom " + a + " is a tautology; no module for it");
			return;
		}

		// here axAtom is an index of an atom with A in it.

		// Use a helper to build all dependencies of a given atom
		Set<Integer> Deps = buildDependenciesOfAtom(fpp, axAtom);

		// now module is just a union of all axioms of dependencies
		Set<OWLAxiom> Module = new HashSet<OWLAxiom>();

		for (int i : Deps) {
			Module.addAll(fpp.getAtomAxioms(i));
		}

		// print the module
		System.out.println("Minimal module for axiom " + a + " is: " + Module);
	}

	/**
	 * A helper method that, given the atom, returns all the dependencies of it.
	 * As long as method getAtomDependents() returns only *direct* dependents,
	 * there is a need to traverse an AD graph.
	 * 
	 * @param fpp
	 *            a reasoner with already built AD
	 * @param atomIndex
	 *            index of an atom in an AD
	 * @return set of atom indices contain all dependencies of a given atom
	 */
	protected Set<Integer> buildDependenciesOfAtom(FaCTPlusPlusReasoner fpp, int atomIndex) {
		// start with a given atom
		Set<Integer> toReturn = new HashSet<Integer>(atomIndex);

		// now add all dependencies for the directly dependent atoms
		for (int i : fpp.getAtomDependents(atomIndex)) {
			toReturn.addAll(buildDependenciesOfAtom(fpp, i));
		}

		// here toReturn contains all the atoms that are dependencies of a given
		// one
		return toReturn;
	}
}

```