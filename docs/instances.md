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