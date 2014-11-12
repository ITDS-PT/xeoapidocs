# XEO API 2.0 - Creating Instances

Lets assume the Demo.xeomode refered in the Readme file

**Creating a new instance**

```java
Demo newDemo = DemoFactory.get().create();
```

**Creating a new instance with a parent**
```java
XEOModel parent = //loaded from somewhere
Demo newDemo = DemoFactory.get().create(parent);
```

**Loading an instance using the BOUI**
```java
long boui = 1111;
Demo loadedDemo = DemoFactory.get().load(boui);
```

As explained in the Concepts page, you can also include code in your Factory class. The main purpose of methods in the factory class would be either to create new instances, load existing instances or creating lists of instances. Such an example could be the following:


```java
	public class DemoFactory extends  DemoFactoryBase<Demo> {
		
        public void createMarriedAdult(){
        	Demo adult = create();
            adult.setState(StateLov.MARRIED);
            adult.setAge(18);
            //Set the birthdate to 18 years ago as well
            return adult;
        }
        
        public Collection<Demo> getAllMaried(){
        	return list("state = ?", StateLov.MARRIED); //Relies on existing list method
        }

	} 

```

**Loading a single instance with a BOQL Query**

If you want to load an instance using a BOQL query and you are certain that only that instance exists (i.e. that query will only return a single value). You can use the **uniqueResult** method:

```java

Demo singleInstance = DemoFactory.get().uniqueResult("name = ? ", "John");
if (singleInstance != null){
    //Proceed
} else {
    //Warning such instance does not exist
}

```

or with a query without arguments

```java

Demo singleInstance = DemoFactory.get().uniqueResult("name = 'John'");
if (singleInstance != null){
    //Proceed
} else {
    //Warning such instance does not exist
}
```

Notice that the **uniqueResult method will return NULL** when the query returns no results.
