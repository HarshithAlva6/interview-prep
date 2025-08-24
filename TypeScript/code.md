Typescript: Statically typed, superset of JS by Microsoft. Address challenges of building large-scale JS applications by adding type annotations, classes, interfaces, namespaces etc.
Type Safety, Backwards Compatibility, Maintainability.
Detecting errors in code without running it is referred to as static checking.
TS vs JS - Optional type annotations vs dynamically typed, syntax, editor integration, type checking, code refactoring. 
TS and JS have interoperability wrt libraries, type definitions (primitive, complex, Type alias, interfaces), can compile TS to JS, type checking using @ts-check comment on top of file at compile time.
npm init, npm i --save-dev typescript (project dependency), tsconfig.json file having compilerOptions. npx tsc to compile TypeScript code.
OR tsc --target ES5 --module commonjs
Running TypeScript - tsc app.ts
Playground - https://www.typescriptlang.org/play
ts-node is TS execution and REPL(Read-Eval-Print Loop) for node.js
Simply run ts-node and you can execute TS script without compiling.
TypeScript types - 
number, string, boolean, any, unknown, void, null, undefined(strictNullChecks), never, object, symbol, enum(auto-increment), Tuple, Array, Union, Intersection, Type Aliases, Type Assertions(as, as const - read only), custom types.
Non-null assertion(!) allows compiler to understand value can't be null or undefined. Satisfies.
Type Inference - Determine type based on value.
Type Compatibility - Regardless of name, compatible as long as structure is same.
Combining types - 
1. Type Union: | helps combine two or more 
2. Intersection Types: & helps create new type by combining multiple existing types.
3. Type Aliases: Create new name for type. type Name = string;
4. keyof operator: Get union of keys from interface/object type.

Type Guards/Narrowing - The type of variable checked using following operators -
1. instanceof: Check if object is instance of class.
2. typeof: Check type of variable to return string.
3. equality: Check the common types in variables.
4. Truthiness: Checking if(strs)
5. Type Predicates: Functions that return boolean value.

TypeScript functions - Function declaration(function name) or function expression(let name = function)
Functions can be declared, arrow, or function type. 
Overloading - Multiple functions with the same name and different parameters.

Typescript interfaces - Define contract for type. Enforce structure for object, class, function argument. Not transpiled to JS, only used by TS at compile-time.
Types vs Interfaces: Types create type based on existing type, while interfaces describe structure of objects and classes.
Extending Interfaces: Using extends
Interface Declaration: With properties, methods as blueprint.
Hybrid Types: Combine multiple types into single type.  

Classes - Blueprint for creating objects
1. Constructor Params: Access modificers, type annotations form parameters assigned to properties of same name within constructor.
2. Access Modifiers: Keywords to control visibility and accessibility of class properties and methods. Public, Private, Protected.
3. Abstract: Not instantiated or having body, but subclassed.
4. Inheritance vs Polymorphism: Using extends, and Objects on diff classes can have diff forms if they have common interface.
5. Method Overriding: If subclass has new implmentation, hence new behaviour as long as signature matches.
6. Constructor Overloading: Multiple constructor definitions with diff paramater lists.

Generics - Code that works for multiple data types. Like a placeholder for the actual data type.
1. Types: <T>
2. Constraints: Specify requirements for type parameters, done using extends. eg - interface LengthWise {length: number;}. So <T extends LengthWise>

Decorators - Help modify behavior of class, property, method, parameter using additional functionality like logging, validation etc. eg: @Log

Utility Types - 
1. Partial: Optional properties
2. Readonly: <Type>
3. Pick: <Type, keys> Selective properties by string literal or union
4. Omit: <Type, Keys> selective properties
5. Exclude: Set difference between A and B. <UnionType, ExludedMembers>
6. Record: Property keys are keys, and values are Type. <Keys, type>
7. Extract: <Type, Union> Only ones from Type that are assignable to Union.
8. Awaited: Model operation like await in async operations, or .then() method on Promises that recursively unwrap it.
9. Parameters: Help construct a Tuple type, by sending function as its parameter and ONLY extracting its types in a tuple. 
type T6 = Parameters<string>;
// ^ Type 'string'
10. NonNullable: Exclude Null and undefined.
11. ReturnType: Construct type having return type of function called as parameter.
12. InstanceType: Constructor Function in Type

Advanced Types - More complex for safer, more maintaenable code.
1. Mapped: Declared using keyof operator and type that maps each property to new property.
2. Conditional: Select type based on condition. type Extends<T, U> = T extends U ? T : U;
3. Literal: Enforce value to be of specific type and value. let Age = 42; let age: Age = 43; // Error
4. Template Literal: Manipulate string values as types. type Name = `Mr. ${string}`;
5. Recursive: Define type that reference itself.

TypeScript Modules - 
1. Internal: Organize code within a file, called namespaces and defined using namespace keyword. Use 'namespace MyModule'
2. External: Organize code across multiple files, and defined using 'export' keyword in one file and "import" in another. 
3. Ambient Modules: Declare external modules from JS, or where no JS declaration exists. Use 'declare module 'my-module''.
4. Namespace Augmentation: Extend existing namespaces.
5. Global Augmentation: Extend built-in global objects.

Ecosystem - 
1. Formatting: Use Prettier.
2. Linter: ESLint impose coding standards.
3. Useful Packages: @article@zod is data validation library, @article@ts-node for execution
4. Build Tools: Webpack(midule bundler), tsup(zero-config TS build tool)


