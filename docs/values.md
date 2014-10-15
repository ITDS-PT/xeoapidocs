# Attribute Values

Accessing attributes is very easy, now you have a get/set method for each attribute with the corresponding name a value. Meaning that for the Demo.xemodel you would have:

#### Getters (Single Value)

```java
Demo demo = DemoFactory.get().load(SOME_BOUI);

String name = demo.getName();
long age = demo.getAge();
BigDecimal height = demo.getHeight();
boolean play = demo.getPlateValidation();
java.util.Date birth = demo.getDateBirth();
netgest.io.iFile picture = demo.getPicture();
StateLov state = demo.getState();
Demo bestFriend = demo.getBestFriend();
XEOAttributeCollection<Demo> family = demo.getFamily();

```

#### Getters (Collections) - Iterating through a collection attribute 
```java
Demo demo = DemoFactory.get().load(SOME_BOUI);
XEOAttributeCollection<Demo> family = demo.getFamily();
for (Demo familyMember : family){
	System.out.println(familyMember.getName());
}
```

As for setters

#### Setters (Single Value)

```java
Demo demo = DemoFactory.get().load(SOME_BOUI);

demo.setName("John");
demo.setAge(23);
demo.setHeight(new BigDecimal(124.2));
java.util.Date date = new java.util.Date(System.currentTimeMilis());
demo.setDateBirth(date);

java.io.File picture = //load from file;
demo.setPicture(picture);

netgest.io.iFile pictureIFile = //load from an existing XEO File
demo.setPicture(pictureIFile);

demo.setState(StateLov.SINGLE);

Demo newBestFriend = DemoFactory.get().create();
newBestFriend.setName("My Friend");
demo.setBestFriend(newBestFriend);

```

#### Setters (Collections)
```java
Demo demo = DemoFactory.get().load(SOME_BOUI);
Demo newFamily = DemoFactory.get().create();

XEOAttributeCollection<Demo> family = demo.getFamily();
family.add(newFamily);

```




