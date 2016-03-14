## Summary ##

**FaCT++** is a DL reasoner. It supports OWL DL and (partially) OWL 2 DL

### FaCT++ is moved to BitBucket ###

All further development will be performed at https://bitbucket.org/dtsarkov/factplusplus

## Versions ##
The latest version available form here is **1.6.3**, released 30 May 2014.

FaCT++ is implemented in C++ and uses optimised tableaux algorithms.

## Download ##
**Important** Since January 2014 it is not possible to use Download option in Google Code sites. You can download FaCT++ from [Google Drive](https://drive.google.com/folderview?id=0B688Ilel_jz_OVktYU5SdGpsek0&usp=sharing) site instead.

## Detailed description and future plans ##
FaCT++ is partially supporting OWL 2 DL. The missing bits are:
  * No support for **keys**
  * Partial **datatype** support. At the moment, the only supported datatypes are _Literal_, _string_, _anyURI_, _boolean_, _float_, _double_, _integer_, _int_, _nonNegativeInteger_, _dateTime_.

The 1.4.0 release **is** the last one that support **DIG** interface.

The 1.4.0 release **is** the last one that supports **OWL API v2** interface.

The 1.4.1 release **is** the last one that supports **OWL API v3.0** interface

If you are lost in all the FaCT++ and/or APIs versions supported please check the [WhichVersionDoINeed](WhichVersionDoINeed.md) page.

## Related Projects ##

  * **JFact** is a java port of FaCT++. It is available from http://sourceforge.net/projects/jfact/ under LGPL.
  * **owlcpp** is a C++ library for parsing, querying, and reasoning with OWL 2 ontologies. It is available from http://owl-cpp.sourceforge.net/ under Boost Software License.
## Release History ##

| Version | Date | Comment | #Downloads | #Downloads total |
|:--------|:-----|:--------|:-----------|:-----------------|
| 1.6.3   | 30 May 2014 | Bug-fix release, add incremental reasoning facility | 1013`**`   | 126978           |
| 1.6.2   | 19 February 2013 | Bug-fix release | 18321      | 126978           |
| 1.6.1   | 26 October 2012 | Bug-fix release | 15729      | 108657           |
| 1.6.0   | 9 July 2012 | Bug fixes, implementation of module extraction and Atomic Decomposition | 11703      | 92928            |
| 1.5.3   | 7 December 2011 | Bug fixes, Top/Bottom properties implementation, improved fresh entities support | 26069      | 81225            |
| 1.5.2   | 12 April 2011 | Some speedup, implement _dateTime_ datatype support | 7520       | 55156            |
| 1.5.1   | 18 January 2011 | Bug and stability fixes | 2003       | 47636            |
| 1.5.0   | 5 October 2010 | OWL API 3.1 support | 2318       | 45633            |
| 1.4.1   | 7 September 2010 | Bug and stability fixes | 481        | 43315            |
| 1.4.0   | 29 April 2010 | Initial support of OWL 2 using OWL API 3; stability fixes | 5960`*`    | 42834            |
| 1.3.0   | 29 May 2009 | Incremental reasoning implementation | 7507       | 36874            |
| 1.2.3   | 05 March 2009 | Bug-fix release | 9832       | 29367            |
| 1.2.2   | 14 January 2009 | Bug-fix release, some speedup | 5499       | 19535            |
| 1.2.1   | 20 November 2008 | Bug-fix release, some speedup | 612        | 14036            |
| 1.2.0   | 25 September 2008 | Bug-fix release, some speedup | 2379       | 13424            |
| 1.1.11  | 28 March 2008 | Bug-fix release, some speedups in ABox reasoning | 3355       | 11045            |
| 1.1.10  | 30 November 2007 | Bug-fix release | 2403       | 7690             |
| 1.1.9   | 04 October 2007 | Bug-fix release; floating point datatypes now supported | 1320       | 5287             |
| 1.1.8   | 12 July 2007 | Bug-fix release, improve performance | 3457       | 3967             |
| 1.1.7   | 11 May 2007 | Bug-fix release | 186        | 510              |
| 1.1.6   | 30 April 2007 | Bug-fixes, prepare the movement to Google Code. | 324        | 324              |
| 1.1.5   | 12 March 2007 | Bug-fix release. | N/A        | N/A              |
| 1.1.4   | 07 December 2006 | SROIQ logic (OWL 1.1) is supported now. | N/A        | N/A              |
| 1.1.3   | 05 April 2006 | Bug-fixes, stability improvements. | N/A        | N/A              |
| 1.1.2   | 08 March 2006 | Bug-fix release. | N/A        | N/A              |
| 1.1.1   | 20 February 2006 | Improve performance. | N/A        | N/A              |
| 1.1.0   | 16 January 2006 | DataTypes (like String and Integer) support added. | N/A        | N/A              |
| 1.0.0   | 17 November 2005 | Reasoning in SHOIQ (a.k.a. OWL DL) is supported. | N/A        | N/A              |

`*` -- without Protege 4.0 plugin, which is non-deprecated
`**` -- and counting
