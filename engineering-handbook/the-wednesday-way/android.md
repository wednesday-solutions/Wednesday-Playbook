# Android

---
description: >-
  If you believe in openness, if you will believe in choice, if you believe in
  innovation from everyone then welcome to Android. Today, it is the most
  popular mobile operating system in the world.
---

# Android Style Guide

* [Architecture](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#architecture)
* [The Stack](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#the-stack)
* [Project Structure](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#project-structure)
* [Nomenclature](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#nomenclature)
  * [Class Names](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#class-names)
  * [Function Names](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#function-names)
  * [Variable Names](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#variables-names)
  * [Expressions](./)
  * [Destructuring](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#destructuring)
  * [Strings](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#strings)
  * [Functions](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#functions)
  * [Classes](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#classes)
  * [Class Structure](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#class-structure)
* [Best Practices](https://github.com/wednesday-solutions/Wednesday-Playbook/blob/master/engineering-handbook/the-wednesday-way/android.md#best-practices)

### Architecture

At Wednesday we follow Android Architecture Components that help us integrated all the exciting features provided by Google. Making an Android app in itself is not all that hard once you get the basics right. Making a **maintainable** app is a whole different story. Let's understand the blueprint of our application.

**Model-View-ViewModel** You should always adhere to the reference below. 

![](.gitbook/assets/mvvm-architecture-complete-overview.png)

Separation of concerns is a beautiful thing and every single design pattern tries to do the best that it can to achieve it. In case of MVVM, there are 3 inherent parts which help in accomplishing the separation of concerns: models, views and view models. You can also add a repository which acts as a single source of truth for all the data

**View** Views handle only the immediate interaction with the user. What does this mean? Well, you simply don’t put any business logic like communicating with a database inside your Activities or Fragments.

**ViewModel** ViewModel doesn’t have any clue about which Views are using the data. A ViewModel is like a glue between a View and business logic. It provides data for the view by getting it from the repository. A View already has a reference to its ViewModel, so it can simply observe some data which the ViewModel exposes. When the data changes, all of the Views which are observing it will be notified about this change.

**Model** Model is where you put all the business specific code. These operate on your app’s data and fetch it from the local database or from the network.

### The Stack

The Wednesday way is to follow the best practices from the community. And yes we do love [Kotlin programming language](https://developer.android.com/kotlin). Seriously it's does boost your productivity and increase your developer happiness.   
Kotlin is also modern & expressive which means it allow you to focus on expressing your ideas and write less boilerplate code. Less code written also means less code to test and maintain.  
Also is designed to be interoperable with Java.   
  
Though it is required to understand the Core Java fundamentals and principles.

Apart from that, we use a some important third-party libraries.

**Android JetPack** Android Jetpack components are a collection of libraries that are individually adoptable and built to work together while taking advantage of Kotlin language features that make you more productive. Use them all or mix and match!

* [Android Jetpack](https://developer.android.com/jetpack)

**Dependency Injection** It says that a class should get its dependencies from outside. In simple words, no class should instantiate another class but should get the instances from a configuration class.

* [Dagger](https://dagger.dev/)
* [Kodein](https://kodein.org/Kodein-DI/)

**HTTP client**

* [Retrofit](https://square.github.io/retrofit/)

**Image Loading Library**

* [Glide](https://bumptech.github.io/glide/).

**Android Design Guidelines**

* \[[https://material.io/design/](https://material.io/design/)\] We use the recommended material design guidelines.

### Nomenclature

#### **Class Names**

Written in UpperCamelCase 

{% tabs %}
{% tab title="Java" %}
```text
class MainActivity { }
```
{% endtab %}

{% tab title="Kotlin" %}
```text
class MainActivity { }
```
{% endtab %}
{% endtabs %}

#### **Variable Names**

{% tabs %}
{% tab title="Java" %}
Fields should be defined at the top of the file and they should follow the naming rules listed below.

Private, non-static field names start with m.   
****Private, static field names start with s.   
Other fields start with a lower case letter.  
Static final fields \(constants\) are ALL\_CAPS\_WITH\_UNDERSCORES.

For example

`MEANING_OF_LIFE = "https://wednesday.is"`

If you have an application constant that is an Object then the Object will be in UPPER\_SNAKE\_CASE and the properties will be in lowerCamelCase

`public class MyClass {   
  public static final String MEANING_OF_LIFE = "MEANING_OF_LIFE";   
  public int   
  publicField;   
  private static   
  MyClass sSingleton;   
  int mPackagePrivate;   
  private int mPrivate;   
  protected int mProtected;  
}`
{% endtab %}

{% tab title="Kotlin" %}
Non-constant names are written in camelCase. These apply to instance properties, local properties, and parameter names. We don't specify the access modifier because by default it is public.  


```text
val publicField = "var"
```

When a [backing property](https://kotlinlang.org/docs/reference/properties.html#backing-properties) is needed, its name should exactly match that of the real property except prefixed with an underscore.

```text
 val id: Int = _id
        get() = field
```
{% endtab %}
{% endtabs %}

#### **Expressions**

{% tabs %}
{% tab title="Java" %}

{% endtab %}

{% tab title="Kotlin" %}
An `if/else` conditional that is used as an expression may omit braces _only_ if the entire expression fits on one line.

```text
val value = if (string.isEmpty()) 0 else 1  // Okay
```

```text
val value = if (string.isEmpty()) { // Okay
    ...
    ...
} else {
    ...
    ...
}
```
{% endtab %}
{% endtabs %}

\*\*\*\*

