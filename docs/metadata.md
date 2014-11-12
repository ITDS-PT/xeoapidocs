#Attribute Metadata

If you want to access attribute metadata (label, disabled state, etc...) you must use the **attributes()** API, like the following:

#### Get a reference to the XEO Attribute
```java
	Demo demo = //load object
	XEOAttribute<String> name = demo.attributes().getName();
    XEOAttribute< Long > age = demo.attributes().getAge();
    XEOAttribute< BigDecimal > height = demo.attributes().getHeight();
    XEOAttribute< Boolean > playsSport = demo.attributes().playsSports();
    XEOAttribute< Date > dateBirth = demo.attributes().getDateBirth();
    XEOAttributeFile picture = demo.attributes().getPicture();
    XEOAttributeObject< Demo > bestFriend = demo.attributes().getBestFriend();
    XEOAttributeCollection< Demo > family = demo.attributes().getFamily();
    
```

Each type of attribute (String, Long, etc...) may have its own set of properties and methods, but they all the following:

#### Common attribute metadata (example with name attribute)
```java
	XEOAttribute<String> name = demo.attributes().getName();
    String label = name.getLabel(); //Returns the attribute label
    String attributeName = name.getName(); //Returns the attribute name (as defined in the .xeomodel)
    String value = name.getValue(); //Return the current value of the attribute, if the value was changed you get that value, see bellow for the value stored in the database
    String persistedValue = name.getPersistedValue(); //Return the value of the attribute as persisted in the database
    boolean required = name.isRequired() //Whether or not the attribute is required
    boolean disabled = name.isDisabled() //Whether or not the attribute is disabled
    boolean visible = name.isVisible() //Whether or not the attribute is visible
    boolean recommended = name.isRecommended() //Whether or not the attribute is recommended
    boolean valid = name.isValid() //whether the attribute is valid or not
    boolean validate = name.validate() //Validates the attribute and returns its valid state
    String invalidMessage = name.getInvalidMessage();

```

#### Dealing with value changes

You can check the current and the persisted value of an attribute as well as checking if the value was changed:

```java
	XEOAttribute<String> name = demo.attributes().getName();
    String currentValue = name.getValue(); //or demo.getName();
    String persistedValue = name.getPersistedValue(); //Get the value in the database
    boolean wasChanged = name.wasChanged();
```

#### Checking for the presence of value

You can also check if an attribute has a value or not, like the following:

```java
	XEOAttribute<String> name = demo.attributes().getName();
    if (name.isNull()){
    	//Name attribute value is null
    }
    
    if (name.isEmpty()){
    	//Name attribute value could be null or empty string
    }
    

```

**Notice that, most types of attributes don't have a notion of "empty". Only Strings can be empty.**

#### Metadata of specific types of attributes

In the following sections we show specific methods of certain types of attributes

##### XEOAttributeObject (relation with another object)
```java
	XEOAttributeObject<Demo> best = demo.attributes().getBestFriend();
    long boui = demo.getBoui();

```

##### XEOAttributeFile (binary data)

```java
	XEOAttributeFile picture = demo.attributes().getPicture();
    File file = new java.io.File("path/to/file.pdf");
    picture.setValue(file);
    
    //Reading the content
    InputStream is = picture.getInputStream();

```

##### XEOAttributeDecimal
```java
	XEOAttribute<BigDecimal> height = demo.attributes().getHeight();
    int minDecimals = height.getMinDecimals();
    int maxDecimals = height.getMaxDecimals();
```

##### XEOAttributeCollection Operations

######Getting the list total
```java
	XEOAttributeCollection<Demo> family = demo.attributes().getFamily();
    int recordCount = family.getRecordCount();

```
######Filtering the collection
If you want to the filter the collection using a given criteria do the following (similar to the java [FileFilter](http://docs.oracle.com/javase/8/docs/api/java/io/FileFilter.html))

```java
demo.attributes().getFamily().filter( 
	new XEOCollectionFilter< Demo >() {
	
    @Override
	public boolean accept( Demo o ) {
		// Check for some condition
		return false;
	}
} );

```

