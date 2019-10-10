# React-Native

React-native is growing fast. We've been actively using the framework in production since the initial days. Here are a set of conventions we like to follow across all of our projects.

* [Setup](react-native.md#setup)
* [Project Structure](react-native.md#project-structure)
* [Nomenclature](react-native.md#nomenclature)
  * [Class Names](react-native.md#class-names)
  * [Function Names](react-native.md#function-names)
  * [Variable Names](react-native.md#variables-names)
  * [Variable Assignment](react-native.md#variable-assignment)
  * [Destructuring](react-native.md#destructuring)
  * [Strings](react-native.md#strings)
  * [Functions](react-native.md#functions)
  * [Classes](react-native.md#classes)
  * [Class Structure](react-native.md#class-structure)
* [Best Practices](react-native.md#best-practices)

## Setup

At Wednesday we rely on the following battle tested libraries.

* [Redux Sauce](https://github.com/infinitered/reduxsauce) for global state management.
* [Redux-Saga](https://redux-saga.js.org/docs/introduction/BeginnerTutorial.html) to make handling side effects easier.
* [Reselect](https://github.com/reduxjs/reselect) to make it easier to select state from redux.
* [React Navigation](https://reactnavigation.org/) for routing.
* [Api Sauce](https://github.com/infinitered/apisauce#readme) for making API calls.
* [Styled Components](https://www.styled-components.com/).
* [React Intl](https://github.com/formatjs/react-intl/tree/master/docs) for localisation and formatting text.
* [Ant Design Mobile](https://mobile.ant.design/) for beautiful components cause we don't believe in reinventing the wheel.

Use the following linting libraries:

- [ES Lint](https://eslint.org/)
- [Prettier-standard](https://github.com/sheerun/prettier-standard)

Use the following testing libraries:

* [Jest](http://facebook.github.io/jest/) 
* [Testing Library React Native](https://github.com/callstack/react-native-testing-library)

## Project Structure

How to group files, containers, components, API calls? Thinking about this plays an important role in building a project that stands the test of time.

* Write the application code in the ```app``` folder.
  * We use the container/component architecture. 
  * Components are just presentational without any side-effects. They are not connected to the Redux store and do not produce side effects.
  * Container components are connected to the Redux store and perform side effects.
  * Containers are where the business logic lives.
  * Example project structure



  ```text
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

Use `lowerCamelCase` for all variable names. Values that change should be assigned to `let`. For all other purposes use `const`

If you have an application constant use `UPPER_SNAKE_CASE`

For example

`const MEANING_OF_LIFE = "https://wednesday.is"`

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

- Don't chain variable assignment

**Preferred**

`let a = 1;`

`let b = a;`

**Not Preferred**

`let a = 1, b = a;`

- Always define variables in a new line

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

String interpolation, here, we want to add a space after a name so we use interpolation `${variable}` so this will help us directly inject variables into a string.

**Preferred**

`let name = 'Wednesday';`

`let description = 'is Awesome';`

console.log(`${name} ${description}`);

**Not Preferred**

`console.log(name + ' ' + description);`

### Functions

- Use named functions

**Preferred**

`export const myFunc = function() {}`

**Not Preferred**

`export default function() {}`

- Use default parameter syntax rather than mutating function arguments

**Preferred**

`function myFunc(name = 'Ali') {}`

**Not Preferred**

```text
function myFunc(name) {
  `name = name | 'Ali;`
  ...
}
```

- Always put default parameters last

  \*\*\*\*

**Preferred**

`function myFunc(lastName, name = 'Ali') {}`

**Not Preferred**

`function myFunc(name='Ali', lastName) {}`

* When using anonymous functions always use arrow functions

  \*\*\*\*

**Preferred**

`array.mapBy((item) => {})`

**Not Preferred**

`array.mapBy(function(item) {})`

### Class Structure

Every class should have the following order

1. All variables declarations
2. Lifecycle methods
3. Public methods
4. Private methods
5. `dispatchStateToProps` and `mapStateToProps`
6. Injections and HoCs declaration.
7. Export component

## Best Practices

### Side effect free component

- Components should be free of side-effects. Containers should be responsible for modifications to the redux store

### Localisation

- No string literals should be used in components, all displayed text should come through translations

  Eg:

  - `intl.formatMessage({id: 'search_details'});`
  - `<FormattedMessage id={'repo_details'} values={{repoName}} />`

### Routing

- All routes should be in `kebab-case`

  Eg: [https://wednesday.is/awesome/partners-with-fanjam/](https://wednesday.is/awesome/partners-with-fanjam/)

### Actions

* When dispatching an action for an API call the action will always be preceeded with a `REQUEST`

  Eg: `REQUEST_GET_GITHUB_REPOS`

* If the API is successful the dispatched action should be preceded with `SUCCESS`

  Eg: `SUCCESS_GET_GITHUB_REPOS`

* If the API is successful the dispatched action should be preceded with `FAILURE`

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

- **Unit Tests**

  Write unit tests for all the helper methods, components, containers, reducers, and sagas.

- **Integration tests**

  Write integration tests that ensure a component works correctly under different input criteria. Also, ensure you test all the actions a component sends.
