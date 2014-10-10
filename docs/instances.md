# XEO API 2.0 - Creating Instances

Lets assume the Demo.xeomode refered in the Readme file

**Creating a new instance**

```java
Demo newDemo = DemoFactory.get().create();
```

** Creating a new instance with a parent**
```java
XEOModel parent = //loaded from somewhere
Demo newDemo = DemoFactory.get().create(parent);
```

** Loading an instance using the BOUI **
```java
long boui = 1111;
Demo loadedDemo = DemoFactory.get().load(boui);
```