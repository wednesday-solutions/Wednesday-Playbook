# Emberjs Styleguide

We love Ember. It is one of the most opinionated frameworks we have used.

* [Project Structure](emberjs.md#project-structure)
* [Nomenclature](emberjs.md#nomenclature)
  * [Class Names](emberjs.md#class-names)
  * [Function Names](emberjs.md#function-names)
  * [Variable Names](emberjs.md#variables-names)
  * [Variable Assignment](emberjs.md#variable-assignment)
  * [Destructuring](emberjs.md#destructuring)
  * [Strings](emberjs.md#strings)
  * [Functions](emberjs.md#functions)
  * [Classes](emberjs.md#classes)
  * [Class Structure](emberjs.md#class-structure)
  * [Get and Set notation](emberjs.md#get-and-set-notation)
* [Best Practices](emberjs.md#best-practices)

## Project Structure

This is one of the most fundamental questions on any project. How are the files laid out? The ember framework supports two types of structures:

* Classic structure: Modules are organised at the top by type i.e. controllers, templates, routes etc.
* Pod structure: Here modules are organised by namespace, then name and then type.

We prefer to use a hybrid approach. We have found with experience that following this approach makes things easy to read.

**Except models, serializers, adapters everything else is a pod.**

_Note: With the module unification_ [_RFC_](https://github.com/emberjs/rfcs/pull/143) _being merged it seems the larger audience also prefers the pods type approach as well. When this is available in Ember we will move to use this file structure._

## Nomenclature

### Class Names

Use upper camel case for class names.

**Preferred**

`class MyClass {}`

**Not Preferred**

`class myClass {}`

`class my_class {}`

### **Function Names**

Use lower camel case for function names.

**Preferred**

`function myFunction()`

**Not preferred**

`function my_function()`

`function _myFunction()`

### **Variable Names**

Use lower camel case for all variable names. Declare all variables with `let`

**Preferred**

`let myVar;`

**Not Preferred**

`let my_var;`

`var myVar;`

`const my_var;`

### Variable Assignment

1. Don't chain variable assignment

**Preferred**

`let a = 1;`

`let b = a;`

**Not Preferred**

`let a = 1, b = a;`

2. Always define variables in a new line

**Preferred**

`let a = 1;`

`let b = 2;`

**Not Preferred**

`let a = 1, b = 2;`

### Destructuring

Use object destructing when accessing and using multiple properties of an object. This will save you from creating temporary references to properties.

**Preferred**

```
function getCompanyDetails(company) {
  let { name, address } = company;
  return ${name} ${address};
}
```

**Best**

```
function getCompanyDetails({ name, address }) {
  return ${name} ${address};
}
```

**Not Preferred**

```
function getCompanyDetails(company) {
  let name = company.name;
  let address = company.address;
  return ${name} ${address}
}
```

### Strings

Use single quotes for strings. This applies to strings in your javascript code along with strings in your moustache templates.

**Preferred**

`let name = 'Wednesday Solutions';`

**Not preferred**

`let name = "Wednesday Solutions";`

Strings that extend 120 characters should **NOT** be split into multiple lines. It is extremely difficult to read. This however, does not apply to code.

**Preferred**

```
let loremIpsum = Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley';
```

**Not Preferred**

```
let loremIpsum = 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.' + 
'Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown' + 
'printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five';
```

### Functions

1. Use named functions

**Preferred**

`export const myFunc = function() {}`

**Not Preferred**

`export default function() {}`

2. Use default parameter syntax rather than mutating function arguments

**Preferred**

`function myFunc(name='Ali') {}`

**Not Preferred**

```
function myFunc(name) {
  `name = name | 'Ali;`
  ...
}
```

3. Always put default parameters last

**Preferred**

`function myFunc(lastName, name = 'Ali') {}`

**Not Preferred**

`function myFunc(name='Ali', lastName) {}`

4. When using anonymous functions always use arrow functions

**Preferred**

`array.mapBy((item) => {})`

**Not Preferred**

`array.mapBy(function(item) {})`

### Classes

1. Avoid manipulating the prototype or defining variables in the prototype

**Preferred**

```
EmberObject.extend({
  variable: null,
  init() {
    this.variable = EmberObject.create();
  }
});
```

**Not Preferred**

```
EmberObject.extend({
  variable: EmberObject.create()
});
```

1. Always declare variables that the class uses

**Preferred**

```
EmberObject.extend({
  variable: null,

  testFunction() {
    ... this.variable.get('#something');
  }
});
```

**Not Preferred**

```
EmberObject.extend({
  testFunction() {
    ... this.variable.get('#something');
}
```

`});`

### Class Structure

Every class should follow the following order

1. Define all variables that the classes uses first
2. Define all computed properties next
3. Define all lifecycle methods
4. Define other methods
5. Define actions

### Get and Set Notation

Always use set to update the value of a property on an object.

Although, the get notation is not needed we still find ourselves using it for proxy objects. So if you pass an array of objects to a component where a property can be a proxy use get. If there is ever a doubt stick to using get.

## Best Practices

### Data Down Actions Up

A large number of new ember enhancements have got quite a resemblance with concepts used in frameworks like React.

What React calls _Uni-Directional Data Flow_ is what Ember calls _Data Down Actions Up_. As your application grows and the state that is managed increases managing dependencies becomes very difficult.

Prefer to always use a data down actions up approach. Here are some things to keep in mind:

1. Data passed to a component should not be modified with in it. Raise an action to tell the consumer about the modification.
2. It's okay to raise multiple actions if your component has multiple child components.
3. Use actions to communicate between parent and child routes.

### Test Practices

Testing is a joy with Emberjs. Ember enables you to write deterministic tests. We expect every emberjs application to have a minimum of 70% code-coverage.

1. Unit Tests

Write unit tests for all the helper methods, macros and template helpers you write.

1. Integration tests

Write integration tests that ensure a component works correctly under different input criteria. Also ensure you test all the actions a component sends.

1. Acceptance tests

Every feature you build needs acceptance tests. Some areas that you need to mandatorily test for are:

* API requests: Ensure that a page is sending the right API requests.
* Test for all business conditions a feature should support.
* Test any local data that needs to be stored and if it is stored correctly.

### Continuous Integration and Deployment

Every project we build should use Circle CI to automate builds and tests. The integration process should have these steps:

* Test if the application can be built
* Test if the application passes all lint checks
* Test if the entire test suite passes

When a branch is merged to develop it should trigger a deployment.

