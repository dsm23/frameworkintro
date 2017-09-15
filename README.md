# A Brief Intro to the Qa-Framework and Object-Orientated Java Programming

#### by David

## Contents

[Basics](#basics)

[Intellij](#intellij)

[Object-Orientated Java](#object-orientated-java)

[camelCase](#camelcase)

[Feature Files](#feature-files)

## Basics

#### Directory Tree

* src/
	* main/
		* java/
			* dependencies/
				* bdd-framework-utilities/
				* bdd-jira-zephyr-plugin/
			* example/
				* Test1/
					* Pages/
						* HomePage.java
						* etc...
				* Test2/
					* Pages
						* HomePage.java
						* etc...
				* etc...
		* resources/
			* local.properties
			* log4j.properties
	* test/
		* java/
			* example/
				* stepDefinitions/
					* Test1/
						* Test1StepDefs.java
					* Test2/
						* Test2StepDefs.java
				* stepLibraries/
					* Test1/
						* Test1StepLibs.java
					* Test2/
						* Test2StepLibs.java
		* resources/
			* features/
				* Test1.feature
				* Test2.feature
			* json/
				* cucumber-serenity-runner.vm
* target/
* pom.xml
* readme.md
* serenity.properties

* External Libraries/

## Intellij

Unlike other 

View -> Tools Window -> Maven Projects

## Object-Orientated Java

(The following has been copied and pasted from the Java course on the site [Sololearn](https://www.sololearn.com). I am placing it here because I think it is a succinct explanation as to the difference between an object and a class in OOP and why we use them)

Java uses Object-Oriented Programming (OOP), a programming style that is intended to make thinking about programming closer to thinking about the real world.
In OOP, each object is an independent unit with a **unique identity**, just as objects in the real world are.

> An apple is an object; so is a mug. Each has its unique **identity**.
It's possible to have two mugs that look identical,
but they are still separate, unique objects.

Objects also have **characteristics**, which are used to describe them. 
For example, a car can be red or blue, a mug can be full or empty, and so on. These characteristics are also called **attributes**. An attribute describes the current state of an object.
In the real world, each object behaves in its own way. The car moves, the phone rings, and so on.
The same applies to objects: **behaviour** is specific to the object's type.


> In summary, each object has three dimensions:
**identity**, **attributes**, and **behaviour**. 
Attributes describe the object's current state,
and what the object is capable of doing is demonstrated through the object's behaviour.

A **class** describes what the object will be, but is separate from the object itself. 
In other words, classes can be described as blueprints, descriptions, or definitions for an object. You can use the same class as a blueprint for creating multiple objects. The first step is to define the class, which then becomes a blueprint for object creation.

Each class has a name, and each is used to define **attributes** and **behaviour**.
Some examples of attributes and behaviour:

| Attributes | Behaviour |
|:----------:|:--------:|
| name 		 | walk		|
| height	 | run 		|
| weight	 | jump		|
| gender	 | speak 	|
| age		 | sleep 	|

#### Syntax

```java
public class Person {
	public String name;
	public int height;
	public String gender
	public int age;
	private int weight;
	
	public void walk(){
		//some function
	}
	public void run(){
		//some function
	}
	public void jump(){
		//some function
	}
	public String speak(){
		//some function
	}
	public void sleep(){
		//some function
	}
	public boolean checkThirst(boolean thirsty){
		//somefunction
	}
}
```
To make an object an instance of a class must be declared:
```java
Person David = new Person();
```
now, the data members of object David can be set or the object can do some method and thus have a behaviour:
```java
David.name = "David";
David.gender = "male";
David.age = 24;
David.height = 180;

David.walk();
David.run();
David.jump();
David.speak();
David.sleep();
David.checkThirst(true);
```

However, in our framework, we don't need to manipulate a new object, we merely need the reference of the class i.e.
```java
Person David = new Person();
```
is the same as:
```java
Person David;
David = new Person();
```
In the first line, `David` is not declared as an object but rather a reference variable allowing us to find the location of the methods and data members within the class that it is referencing but we can't instantiate `David` without the second line.

#### camelCase

| Identifier 	| Standard Convention |
|:------------:	|:-----------------:|
| package	 	| somepackage		|
| variable		| someVariable		|
| function/method | someFunction() 	|
| class/object	 | SomeObject		|
| constant	 	| SOME_CONSTANT 	|

## Feature Files

File -> Settings... -> Plugins -> Browse Repositories...

Install

* Gherkin
* Gauge
* Cucumber for Java

You should now be able to open .feature files in the cucumber editor. You will be able to identify the cucumber editor fromt he green rectangular speech bubble next to the name of the file in the editor.

If you do not see this green speech bubble and instead see a blue 'F'. Then you will need to

File -> Settings -> Editor - File Types -> Cucumber Scenario

and add '.feature' files to the Registered Patterns

```
@ui
@regression
Feature: Name of Feature
As a Belly user (Describe an initial context)
I want to know when I am hungry (Describe an event)
So that I can eat (Describe an expected outcome)

	Scenario: Growl when I am hungry
		Given I have '40' cukes in my belly
		When I wait '1' hour
		Then my belly should 'silent'
```

All descriptions in the feature file should be written in a way that a BA should be able to understand them that is to say an abstraction from code.




