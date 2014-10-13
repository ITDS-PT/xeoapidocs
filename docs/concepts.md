# XEO API 2.0 Concepts

## Summary
- Requires the XEOAPI20.jar in the ModulesLibs folder
- Activated in the Project Properties -> XEO Studio -> Use new XEO API style
- Generates Base classes in .src-internal (do not write code here)
- Generetes classes in -src-xeogen (by default) once created are not touched anymore, you can write your own code in them 
- Strongly typed attributes in getters and setters (include Lovs)

## Long version

This document explains how the XEOAPI 2.0 works in broad concepts.

### Instalation

To install the XEOAPI you require two things:
* Add the xeoapi20.jar to the classpath (for instance to the base_lib/modules_libs folder)
* Install XEO Studio version 1.X or superior
* Activate the new API by going to Project Properties -> XEO Studio and check the  **Use XEO Studio New Style API** checkbox
* In the XEO Studio Builder view you can check the status of each build (whenever you save an XEOModel file, it triggers the new api build)

### Source Folders

