# Converting between APIs

This document explains to how switch from one API to another

####Switching from boObject to XEOModelBase

```java
boObject demoObj = XEO.load(SOME_BOUI);
Demo demo = (Demo) XEOApplication.wrapModel(demoObj);
```





#### Switching from XEOModelBase to boObject

```java
Demo demo = //get demo from somewhere
boObject demoObj = demo.unwrap();
```

