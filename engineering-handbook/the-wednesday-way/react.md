# React Styleguide

React is the fastest growing web framework. It has an amazing community of developers and we try are best to keep up with all the updates.

* [Setup](react.md#setup)
* [Project Structure](react.md#project-structure)
* [Nomenclature](react.md#nomenclature)
  * [Class Names](react.md#class-names)
  * [Function Names](react.md#function-names)
  * [Variable Names](react.md#variables-names)
  * [Variable Assignment](react.md#variable-assignment)
  * [Destructuring](react.md#destructuring)
  * [Strings](react.md#strings)
  * [Functions](react.md#functions)
  * [Classes](react.md#classes)
  * [Class Structure](react.md#class-structure)
* [Best Practices](react.md#best-practices)

## Setup

At Wednesday we rely heavily on the following battle tested libraries while building React projects.

* [Redux Sauce](https://github.com/infinitered/reduxsauce) for global state management.
* [Redux-Saga](https://redux-saga.js.org/docs/introduction/BeginnerTutorial.html) to make handling side effects easier.
* [Reselect](https://github.com/reduxjs/reselect) to make it easier to select state from redux.
* [React Router](https://github.com/ReactTraining/react-router) for routing of your SPA.
* [Api Sauce](https://github.com/infinitered/apisauce#readme) for making API calls.
* [Styled Components](https://www.styled-components.com/) for styling.
* [React Intl](https://github.com/formatjs/react-intl/tree/master/docs) for localisation and formatting text.
* [Ant Design](https://ant.design/) for beautiful components cause we don't believe in reinventing the wheel.

Use the following linting libraries:

* [ES Lint](https://eslint.org/) 
* [Prettier-standard](https://github.com/sheerun/prettier-standard)

Use the following testing libraries:

* [Jest](http://facebook.github.io/jest/) 
* [React Testing Library](https://github.com/testing-library/react-testing-library)
* [React Generator](https://github.com/wednesday-solutions/react-generator): A tool to generate tests for components, containers and more. (This is all us! Pull requests are always welcome)!

## Project Structure

Code organization is one of the most important things in a project and plays a paramount role in writing well architected, organized and easy to maintain code.

* Write the application code in the ```app``` folder.
  * We use the container/component architecture. Components are just presentational without any side-effects. They are not connected to the Redux store and do not produce side effects either.
  * Container components are connected to the Redux store and perform side effects.
  * Container components are responsible for the business logic whereas the components are only responsible for visuals.
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

Use `lowerCamelCase` for all variable names.
Values that changed should be assigned to `let`. For all other purposes use `const`

If you have an application constant use `UPPER_SNAKE_CASE`

For example

```const MEANING_OF_LIFE = "https://wednesday.is"```

If you have an application constant that is an Object then the Object will be in `UPPER_SNAKE_CASE` and the properties will be in `lowerCamelCase`

```
const COMPANY_DETAILS = {
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

String concatenation, Here, we want to add a space after a name so we use interpolation `${variable}` so this will help us directly inject variables into a string.

**Preferred**

`let name = 'Wednesday';`

`let description = 'is Awesome';`

console.log(`${name} ${description}`);

**Not Preferred**

`console.log(name + ' ' + description);`


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
2. Define all lifecycle methods
3. Define other methods
4. dispatchStateToProps and mapStateToProps
5. Compose component with all the injections, HoCs
6. Export component

## Best Practices

### Side effect free component

* Components should be free of side-effects. Containers should be responsible for modifications to the redux store

### Localisation

* No string literals should be used in components, all displayed text should come through translations
  
  Eg:

    * `intl.formatMessage({id: 'search_details'});`
    * `<FormattedMessage id={'repo_details'} values={{repoName}} />`    

### Routing

* All routes should be in `kebab-case`
  
  Eg: [https://wednesday.is/awesome/partners-with-fanjam/](https://wednesday.is/awesome/partners-with-fanjam/)

### Actions

* When dispatching an for an API call the action will always be preceeded with a `REQUEST`

    Eg: `REQUEST_GET_GITHUB_REPOS`

* If the API is successful the dipatched action will be preceeded with `SUCCESS`

    Eg: `SUCCESS_GET_GITHUB_REPOS`

* If the API is successful the dipatched action will be preceeded with `FAILURE`

    Eg: `FAILURE_GET_GITHUB_REPOS`

### Test Practices

Add a `tests` folder to each of the component folder.
Eg:
```
...
    containers/
        SampleContainer/
            tests/
                index.test.js
                saga.test.js
                reducer.test.js
                selectors.test.js
            ...
        ...
    ...
...
```

*  **Unit Tests**

  Write unit tests for all the helper methods, components, containers, reducers, and sagas.

* **Integration tests**

  Write integration tests that ensure a component works correctly under different input criteria. Also ensure you test all the actions a component sends.

* **Acceptance tests**

  Every feature you build needs acceptance tests. Some areas that you need to mandatorily test for are:

  * API requests: Ensure that a page is sending the right API requests.
  * Test for all business conditions a feature should support.
  * Test any local data that needs to be stored and if it is stored correctly.