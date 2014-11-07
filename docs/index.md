XEO API 2.0
======

Welcomo the XEO API Documentation, this respository contains documentation and examples for the 2.0 version API of the XEO Framework (www.xeoframework.org)

This documentation is split in several pages, namely:

* [Concepts and base API](concepts)
* [Creating and Loading Instances](instances)
* [Accessing/Changing atribute values](values)
* [Lists of Objects](lists)
* [Attribute Metadata (Valid, Label, Required, Value Change, etc.)](metadata)
* [Converting between old API and new API](switching)


## Example Object

For the purpose of this documentation assume the existence of a Demo.xemodel file with the following attributes:
* name (String)
* age (number)
* height (number, with decimals)
* playSports (boolean)
* dateBirth (date)
* picture (binaryData)
* bestFriend (object - Relation to Demo)
* family (collection - Relation to Demo)
* state (lov - stateLov)

StateLov has the following values
* Single
* Married


Please check each of the pages for further information

