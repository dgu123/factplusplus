# Introduction #

At the moment there are too many tools/reasoner interfaces and corresponding versions of FaCT++ to easily deal with. If unsure, check this page -- it can help you find the most suitable version for you.

# Details #

The general idea to get the proper version of FaCT++ is as follows:

  * choose a version you need (see below);
  * for use with Protege -- just download appropriate plugin;
  * for a Java application (with or without OWLAPI) -- download the corresponding OWL API .jar;
    * then download precompiled binary of **the corresponding version**.
  * for using from C++ programs or a non-java application -- download corresponding binaries.

Now the choice depends on what are you going to use FaCT++ for:

## Protege ##
You should know the version of Protege you are using. If unsure, please check _About Protege..._ menu element (_org.protege.osgi.framework.Launcher_ in the main menu). You will find **Version** and **Build** information there. Knowing this, you have the following options:

  * Version 4.0. Use FaCT++ v1.4.0.1 plugin. The FaCT++ plugin will be updated automatically if you are using an older version of FaCT++. Note that support of this version is discontinued, and there would be no more FaCT++ releases that supports it.

  * Version 4.1 Alpha (release 100-103). Use FaCT++ v1.4.0.1 plugin. The FaCT++ plugin will be updated automatically if you are using an older version of FaCT++. Note that support of this version is discontinued, and there would be no more FaCT++ releases that supports it.

  * Version 4.1 Beta (Release 200-206). Use FaCT++ v1.4.1 plugin. Note that support of this version is discontinued, and there would be no more FaCT++ releases that supports it.

  * Version 4.1 Beta (Release 209 and up). Use the latest FaCT++ plugin.

  * Version 4.3, 4.2. Use the latest FaCT++ plugin.

## OWL API ##

  * OWL API v2.x. Use FaCT++ jar v1.4.0.1 with binaries for v1.4.0. Note that support of this version is discontinued, and there would be no more FaCT++ releases that supports it.

  * OWL API v3.0.x. Use FaCT++ jar v1.4.1 with binaries for v1.4.1. Note that support of this version is discontinued, and there would be no more FaCT++ releases that supports it.

  * OWL API v3.1.0. Use the latest FaCT++ jar with corresponding binaries.

  * OWL API v3.4.10. Use the latest FaCT++ jar with corresponding binaries.

## DIG 1.1 server ##
  * Use FaCT++ binaries v1.4.0. Note that support of this version is discontinued, and there would be no more FaCT++ releases that supports it.

## C++ code ##
  * Use the latest available version (usually you will see it on top of the all downloads) compiled for the appropriate platform. You might want to use a source distribution, or the latest SVN tree as well.

## LISP-like interface ##
  * Use FaCT++ v1.5.0. Note that there is only Linux precompiled version; you will need to compile a version for other operating systems yourself. Note that support of this language is likely to be discontinued after version 1.5.0; however, the translator to some version of OWL 2 would be provided.