# A Brief Intro to the Qa-Framework and Object-Orientated Java Programming

#### by David

## Contents

[Basics](#basics)

[Intellij](#intellij)

[Object-Orientated Java](#object-orientated-java)

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

```
An apple is an object; so is a mug. Each has its unique **identity**.
It's possible to have two mugs that look identical,
but they are still separate, unique objects.
```

Objects also have **characteristics**, which are used to describe them. 
For example, a car can be red or blue, a mug can be full or empty, and so on. These characteristics are also called **attributes**. An attribute describes the current state of an object.
In the real world, each object behaves in its own way. The car moves, the phone rings, and so on.
The same applies to objects: **behaviour** is specific to the object's type.

```
In summary, each object has three dimensions:
**identity**, **attributes**, and **behaviour**. 
Attributes describe the object's current state,
and what the object is capable of doing is demonstrated through the object's behaviour.
```

A **class** describes what the object will be, but is separate from the object itself. 
In other words, classes can be described as blueprints, descriptions, or definitions for an object. You can use the same class as a blueprint for creating multiple objects. The first step is to define the class, which then becomes a blueprint for object creation.

Each class has a name, and each is used to define **attributes** and **behaviour**.
Some examples of attributes and behaviour: