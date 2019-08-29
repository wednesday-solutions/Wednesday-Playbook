# Emberjs Styleguide

We love Ember. It is one of the most opinionated frameworks we have used.

* [Project Structure](#project-structure)
* Nomenclature
  * Class Names
  * Function Names
  * Variable Names
  * Destructuring

## Project Structure

This is one of the most fundamental questions on any project. How are the files laid out? The ember framework supports two types of structures:

* Classic structure: Modules are organised at the top by type i.e. controllers, templates, routes etc.
* Pod structure: Here modules are organised by namespace, then name and then type.

We prefer to use a hybrid approach. We have found with experience that following this approach makes things easy to read.

**Except models, serializers, adapters everything else is a pod.** 

_Note: With the module unification_ [_RFC_](https://github.com/emberjs/rfcs/pull/143) _being merged it seems the larger audience also prefers the pods  type approach as well. When this is available in Ember we will move to use this file structure._

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

### Destructuring

Use object destructing when accessing and using multiple properties of an object. This will save you from creating temporary references to properties.

**Preferred**

`function getCompanyDetails(company) {

    let { name, address } = company;

    return ${name} ${address};

}`

Better than the above

`function getCompanyDetails({ name, address }) {

    return ${name} ${address};

}`

**Not Preferred**

`function getCompanyDetails(company) {

    let name = company.name;

    let address = company.address;

    return ${name} ${address}

}`

### Strings

Use single quotes for strings. This applies to strings in your javascript code along with strings in your moustache templates.

**Preferred**

`let name = 'Wednesday Solutions';`

**Not preferred**

`let name = "Wednesday Solutions";`

Strings that extend 120 characters should **NOT** be split into multiple lines. It is extremely difficult to read. This however, does not apply to code.

**Preferred**

`let loremIpsum = Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley';`

**Not Preferred**

`let loremIpsum = 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.' +
'Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown' +
'printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five';`

### // fix below this

### **Architecture decisions**

### **Tests**

### **Continuous Deployment and Integration**

\*\*\*\*



