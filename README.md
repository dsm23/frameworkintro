# A Brief Intro to the Qa-Framework and Object-Orientated Java Programming

#### by David

## Contents

[Basics](#basics)

[IntelliJ](#intellij)

[Object-Orientated Java](#object-orientated-java)

[camelCase](#camelcase)

[Feature Files](#feature-files)

[Step Definitions](#step-definitions)

[Step Libraries](#step-libraries)

[Pages](#pages)

[Serenity](#serenity)

[Jira](#jira)

[Zephyr](#zephyr)

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

#### bdd-framework-utilities

If you do not have bdd-framework-utilities/ within your dependencies/ then run:

```java
mvn install:install-file -Dfile=src/main/java/dependencies/bdd-framework-utilities/bdd-framework-utilities-1.0-SNAPSHOT.jar -DpomFile=src/main/java/dependencies/bdd-framework-utilities/pom.xml
```

## IntelliJ

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

camelCase is a recommendation, not a rule. It is generally accepted. It helps make your code more readable, maintainable, and reusable.

## Feature Files

File -> Settings... -> Plugins -> Browse Repositories...

Install

* Gherkin
* Gauge
* Cucumber for Java

You should now be able to open .feature files in the cucumber editor. You will be able to identify the cucumber editor from the green rectangular speech bubble next to the name of the file in the editor.

If you do not see this green speech bubble and instead see a blue 'F'. Then you will need to

File -> Settings -> Editor -> File Types -> Cucumber Scenario

and add '.feature' files to the Registered Patterns

```gherkin
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

Also, it is very important that within the scenario section that all statements written inline with Given, When, Then and And. For one of these statements

For more on Gherkin keywords, [Read More...](https://cucumber.io/docs/reference)

## Step Definitions

This is what a step-definition looks like:

```java
@Given("^I (?:want|would like) to buy (.*)$")
public void givenCustomerWantsToBuy(String product) throws Throwable {
	...
}
```

If the feature file has been setup and written correctly then you should see in IntelliJ that the IDE is attempting to highlight the descriptions next to the Gherkin keyword in the Scenario section.
Highlight that text with your mouse and then while holding the 'Alt' key hit 'Enter' and you should see the 'create step definition' sub-menu pop up.

From this sub-menu you can create a new step-definition in a current step-definition file or create a new file

You can also create step-definitions for every gherkin description in the .feature file.

However, it is worth noting that the generation step-definitions use double quotes and do not convert keywords declared in single quotes into variables in their step-definitions.

The simplest keyword declaration is `'(.*)'` in that:

```java
@Given("^I search for '(.*)'$")
public void searchForInput(String keyword) throws Throwable {
	...
}
```

Cheatsheet: http://agileforall.com/wp-content/uploads/2011/08/Cucumber-Regular-Expressions-Cheat-Sheet.pdf

`throws Throwable` is an exception handler. It is required to prevent a java program crash if an error is encountered. The auto-generated step-definitions also create a `throw new PendingException();` we do not use this exception handler so it is ideal if you could delete it.

## The Sequential Order

In executing the tests, the framework will start from the feature files. These step definitions allow us to link the .feature gherkin file to a java class file. In my opinion, it is reasonable to ascert that this is the start of a sequential order

↡ Feature files

↡ StepDefinitions

↡ StepLibraries

↠ Page Object Model

## Step Libraries

In an attempt to remove clutter, it is advised to write all methods executed in tests in the stepLibraries/ folder.

To access the written methods in step Libraries, it is import to have

```java
import example.steplibs.test1.somesteplibrariesjavaclass;
```
placed at the top of step Definitions file below the package declaration and above the class declaration.

## Pages

@DefaultUrl goes outside the class declaration

```java
@DefaultUrl("https://www.google.com")
public class HomePage extends PageObject {}
```

@FindBy([id, className, etc...](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/support/FindBy.html))
```java
@FindBy(id="generic")
public WebElementFacade webElement;
```
## Serenity

GUI representation of tests passing/failing/erroneous. Accompanied with breakdowns, screenshots and links to issues on Jira.

http://localhost:63342/<ProjectName>/target/site/serenity/index.html

can also be found at

C:\Users\<User>\<ProjectName>\target\site\serenity\index.html

## Jira

[Download](https://www.atlassian.com/software/jira/download)

to run, double click 
C:\Program Files\Atlassian\JIRA\bin\startup.bat

To use, uncomment in serenity.properties. I advise following the gitlab wiki.

## Zephyr

