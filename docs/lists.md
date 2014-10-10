# List of Values

With the 2.0 API lists are always strongly typed with a specific object. To create a new list you have to get a reference to the specific object factory. Like the following

#### Get all instances
```java
XEOCollection<Demo> demos = DemoFactory.get().list();

for (Demo demo : demos){
	System.out.println(demo.getName());
}

```

**Note, lists in the new API will iterate through ALL pages**

#### List with a given query (no arguments)

```java
XEOCollection<Demo> demos = DemoFactory.get().list("select Demo where creator = CTX_PERFORMER_BOUI");

```

#### List with a given query and arguments (mode 1, " ? parameters")

```java
String name = "John";
StateLov state = StateLov.SINGLE;
Demo bestFriend = DemoFactory.get().load(SOME_BOUI);
XEOCollection<Demo> demos = DemoFactory.get().list("select Demo where name = ? and state = ? and bestFriend = ?", name, state, bestFriend);

```
Note the use of StateLov and Demo instances directly, you could also use the following
```java
String name = "John";
StateLov state = StateLov.SINGLE;
Demo bestFriend = DemoFactory.get().load(SOME_BOUI);
XEOCollection<Demo> demos = DemoFactory.get().list("select Demo where name = ? and state = ? and bestFriend = ?", name, state.getValue(), bestFriend.getBoui());
```


#### List with a given query and arguments (mode 2, " {} parameters")

In this mode you can reference the same argument multiple time by specifying its order inside brackets (like {1})

```java
String name = "John";
StateLov state = StateLov.SINGLE;
StateLov state2 = StateLov.MARRIED;
Demo bestFriend = DemoFactory.get().load(SOME_BOUI);
XEOCollection<Demo> demos = DemoFactory.get().list("select Demo where (name = {1} and state = {2}) or (name = {1} and state = {3}) , name, state, state2 );

```
