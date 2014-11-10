# List of Values

With the 2.0 API lists are always strongly typed with a specific object. To create a new list you have to get a reference to the specific object factory. Like the following:

#### Get all instances
```java
XEOCOllection<Demo> demos = DemoFactory.get().list();
for (Demo demo : demos){
	System.out.println(demo.getName());
}

```
The ==XEOCOllection== type is an implementation of ==java.util.Collection== which means you can use all the collection methods available in the API (the following examples will use the java Collection type)

**Note, lists in the new API will iterate through ALL pages**

#### List with a given query (no arguments)

```java
Collection<Demo> demos = DemoFactory.get().list("creator = CTX_PERFORMER_BOUI");

```

#### List with a given query and arguments (mode 1, " ? parameters")

```java
String name = "John";
StateLov state = StateLov.SINGLE;
Demo bestFriend = DemoFactory.get().load(SOME_BOUI);
Collection<Demo> demos = DemoFactory.get().list("name = ? and state = ? and bestFriend = ?", name, state, bestFriend);

```
Note the use of StateLov and Demo instances directly, you could also use the following
```java
String name = "John";
StateLov state = StateLov.SINGLE;
Demo bestFriend = DemoFactory.get().load(SOME_BOUI);
Collection<Demo> demos = DemoFactory.get().list("name = ? and state = ? and bestFriend = ?", name, state.getValue(), bestFriend.getBoui());
```


#### List with a given query and arguments (mode 2, " {} parameters")

In this mode you can reference the same argument multiple time by specifying its order inside brackets (like {1})

```java
String name = "John";
StateLov state = StateLov.SINGLE;
StateLov state2 = StateLov.MARRIED;
Demo bestFriend = DemoFactory.get().load(SOME_BOUI);
Collection<Demo> demos = DemoFactory.get().list(" (name = {1} and state = {2}) or (name = {1} and state = {3}) , name, state, state2 );

```

#### List created by specifying list options (fluent interface)

You can also create a list like the following,  by specifying the set of options you want to apply to the list

```java
Collection<Demo> demo = DemoFactory.get().listBuilder( "WHERE_CLAUSE" ) //Create the builder with a specific where clause
			.cache( true ) //Boolean, use cache or not, defaults to true
			.fetchSize( 40 ) //Page size (defaults to 50)
			.fullText( "SOMETHING" ) //Fulltext search query to use (defaults to "")
			.args( new Object[0] ) //Arguments as an array of objects
			.argsList( "arg1", "arg2", "argN" ) //Arguments as a list of objects
			.security( true ) //Whether to use security or not (defaults to true
			.orderBy( "name DESC" ) //Order results by an attribute (defaults to "")
			.execute(); //Create the List
	.
```

#### Generic List (any kind of model and specifying the full query)

This type of query is usefull when you need to perform queries like ==select Demo.family where age > 10==. You can use it like the following:

```java

Collection< Demo > results =  XEOApplication.ql( Demo.class , "select Demo.family where name = ? " ).argsList("John").execute();

```

The ==XEOApplication.ql== method return a ==XEOQLBuilder== instance which allows you to customize the query just like with the ==listBuilder== method in factory classes.