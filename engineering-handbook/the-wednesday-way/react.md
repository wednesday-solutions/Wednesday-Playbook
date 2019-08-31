# React Styleguide

We love React. It's one of the msot performant and fastest growing web frameworks, it's got an amazing, super helpful community who are always ready to help.

* [The Stack](react.js.md#the-stack)
* [Project Structure](react.js.md#project-structure)
* [Nomenclature](react.js.md#nomenclature)
  * [Class Names](react.js.md#class-names)
  * [Function Names](react.js.md#function-names)
  * [Variable Names](react.js.md#variables-names)
  * [Variable Assignment](react.js.md#variable-assignment)
  * [Destructuring](react.js.md#destructuring)
  * [Strings](react.js.md#strings)
  * [Functions](react.js.md#functions)
  * [Classes](react.js.md#classes)
  * [Class Structure](react.js.md#class-structure)
* [Best Practices](react.js.md#best-practices)

## The Stack

At Wednesday we rely heavily on the following battle tested libraries while building React projects.

* [Redux](https://redux.js.org/introduction/getting-started) for global state management.
* [Redux-Saga](https://redux-saga.js.org/docs/introduction/BeginnerTutorial.html) to make handling side effects easier.
* [Reselect](https://github.com/reduxjs/reselect) to make it easier to select state from redux.
* [React Router](https://github.com/ReactTraining/react-router) for routing of your SPA.
* [Api Sauce](https://github.com/infinitered/apisauce#readme) for making API calls.
* [Styled Components](https://www.styled-components.com/) for styling.
* [React Intl](https://github.com/formatjs/react-intl/tree/master/docs) for localisation and formatting text.
* [Ant Design](https://ant.design/) for beautiful components cause we don't believe in reinventing the wheel.

At Wednesday building top quality code is the number one priority.
In order to be able to produce **readable**, **well documented** and **maintainable code** confidently we use the following linters and testing frameworks

The following libraries are used for linting:

* [ES Lint](https://eslint.org/) 
* [Prttier-standard](https://github.com/sheerun/prettier-standard)
* [Jest](http://facebook.github.io/jest/) 
* [React Testing Library](https://github.com/testing-library/react-testing-library)
* [React Generator](https://github.com/wednesday-solutions/react-generator): Our very own home-bred cli tool to generate tests, components, containers and more!

## Project Structure

Code organisation is one of the most important things in a project and plays a paramount role in writing well architected scalable projects.

* The application code is writen in the ```app``` folder.
  * We follow the container/component architecture where components are basically dumb React components. They are not connected to the Redux store and do not produce side effects either.
  * Container components are connected to the Redux store and perform side effects. 
  * Container components are responsible for the business logic whereas the dumb components are only responsible for visuals.
  * Example project structure
    ```
    app/
        components/
            SampleComponent/
                index.js
                tests/
                    index.test.js
        containers/
            SampleContainer/
                index.js
                action.js  (if required)
                reducer.js  (if required)
                saga.js  (if required)
                selectors.js (if required)
        assets/
            sample-image.png
        translations/
            en.json
    ```

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

Use lower camel case for all variable names. 
For variables who's value doesn't change we use the kyeword `const` and for those variables that have changing values we use `let`

If you have an application constant use UPPER_SNAKE_CASE

For example

```MEANING_OF_LIFE = "https://wednesday.is"```

If you have an application constant that is an Object then the Object will be in UPPER_SNAKE_CASE and the properties will be in lowerCamelCase

```
COMPANY_DETAILS = {
    name: "Wednesday",
    properties: ["Passionate", "dedicated", "and", "hardworking", "team",
                 "producing", "quality", "software"],
    workWthUs: "hello@wednesday.is"
}
```
**Preferred**

`let myVar;`

`const myConst`

`export const MEANING_OF_LIFE="https://wednesday.is"`

**Not Preferred**

`let my_var;`

`var myVar;`

`const my_var;`

### Variable Assignment

* Don't chain variable assignment

**Preferred**

`let a = 1;`

`let b = a;`

**Not Preferred**

`let a = 1, b = a;`

* Always define variables in a new line

**Preferred**

`let a = 1;`

`let b = 2;`

**Not Preferred**

`let a = 1, b = 2;`

### Strings

Use single quotes for strings. This applies to strings in your javascript code along with strings in your moustache templates.

**Preferred**

`let name = 'Wednesday Solutions';`

**Not preferred**

`let name = "Wednesday Solutions";`

Strings that extend 120 characters should **NOT** be split into multiple lines. It is extremely difficult to read. This however, does not apply to code.

**Preferred**

```text
let loremIpsum = Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley';
```

**Not Preferred**

```text
let loremIpsum = 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.' + 
'Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown' + 
'printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five';
```

### Functions

* Use named functions

  **Preferred**

  `export const myFunc = function() {}`

  **Not Preferred**

  `export default function() {}`

* Use default parameter syntax rather than mutating function arguments

  **Preferred**

  `function myFunc(name='Ali') {}`

  **Not Preferred**

  ```text
  function myFunc(name) {
    `name = name | 'Ali;`
    ...
  }
  ```

* Always put default parameters last

  **Preferred**

  `function myFunc(lastName, name = 'Ali') {}`

  **Not Preferred**

  `function myFunc(name='Ali', lastName) {}`

* When using anonymous functions always use arrow functions

  **Preferred**

  `array.mapBy((item) => {})`

  **Not Preferred**

  `array.mapBy(function(item) {})`

### Classes

* Decstructing the props

    `const { name, companyName, handleOnClick } = this.props`

### Class Structure

Every class should follow the following order

1. Define all variables that the classes uses first
2. Define all computed properties next
3. Define all lifecycle methods
4. Define other methods
5. dispatchStateToProps and mapStateToProps
6. Compose component with all the injections
7. Export component

## Best Practices

### Side effect free component

* All of the components need to be side effect free. Any and all interaction with the redux store or the sagas must take place in containers

### Localisation

* No string literals should be used in components, all displayed text should come through translations

### Test Practices

Testing with react is pretty straight forward.
We add a `tests` folder to each of the component folder.
For example
```
...
    containers/
        SampleContainer/
            tests/
                index.test.js
                saga.test.js
                reducer.test.js
                actions.test.js
                selectors.test.js
            ...
        ...
    ...
...
```

* Unit Tests

  Write unit tests for all the helper methods, components, comtainers, reducers, actions and sagas.

* Integration tests

  Write integration tests that ensure a component works correctly under different input criteria. Also ensure you test all the actions a component sends.

* Acceptance tests

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