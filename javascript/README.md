## Javascript code standards

[all rules are automatically enforced by `.eslintrc`](./.eslintrc)

Installing inline jscs checks in sublime
--------

+ go to package control (cmd + shift + p)
+ `install`
+ `SublimeLinter`
+ `SublimeLinter-contrib-eslint`


The following code standards should be applied to all javascript projects. These standards are intended  to keep the code base clean and readable both for human readability and the autogeneration of the documentation.

in order to enforce these you will need:

+ [the eslintrc file](./.eslintrc)
+ "babel-eslint": "^6.1.2",
+ "eslint": "^3.4.0",
+ "eslint-loader": "^1.5.0",
+ "eslint-plugin-react": "^6.2.0",

example with all rules
------

```javascript
/**
 * ## exampleClass
 *
 * a class created for this example
 *
 * @param {Object} props properties to pass
 *
 * @return {Class} instance of exampleClass
 */
class exampleClass extends anotherClass
{
    /**
     * ## constructor
     *
     * creates the instance and binds person and moon to this
     *
     * @param {Object} props properties to pass
     */
    constructor( props )
    {
        super( props );

        this.moon = props.moon;
        this.person = new Person();

        exampleFunction( props[ 'moon' ], props[ 3 ] );
    }


    /**
     * ## exampleFunction
     *
     * gets called by the constructor. probably doesnt actually do anything
     *
     * @param {Number} paramOne The first number
     * @param {Number} paramTwo The second number
     *
     * @return {Array} the newly mapped array
     */
   exampleFunction( paramOne, paramTwo )
    {
        /* ## helper
         *
         * a helper function that adds 1
         *
         * @param {Number} val the number to be added to
         *
         * @return {Number} val + 1
         */
        function helper( val )
        {
            val = val + 1;

            return val;
        }


        let self = this;

        let arr     = [ 'doge', 'gir', 'nyan' ];
        const arr2  = [
            'doge',
            'gir',
            'nyan'
        ];

        const obj = {
            moon            : 'doge',
            alfredoSauce    : 'such food'
        };

        let i = 0;
        arr = arr.map( team =>
        {
            const team2 = arr2[ i ];
            i++;

            if ( !team2 )
            {
                console.error( `no team2, so ${team}` );

                return team;
            }
            else if ( !( /foo/ ).test( team2 ) )
            {
                return 'bar!';
            }

            return team2;
        } );

        return arr;
    }
};

```


RULES
-----

some rules are covered by extensions.  we currently use:

+ eslint:recommended
+ plugin:react/recommended


# array-bracket-spacing

### requires one or more spaces or newlines inside array brackets

+ [http://eslint.org/docs/rules/array-bracket-spacing](http://eslint.org/docs/rules/array-bracket-spacing)
+ Throws: error

bad

```javascript
const arr = ['foo', 'bar'];
const arr = ['foo', 'bar' ];
const arr = [ ['foo'], 'bar' ];
```

good

```javascript
const arr = [];
const arr = [ 'foo', 'bar', 'baz' ];
const arr = [ [ 'foo' ], 'bar', 'baz' ];
```

# arrow-spacing

### requires a space before and after an arrow function’s arrow

+ [http://eslint.org/docs/rules/arrow-spacing](http://eslint.org/docs/rules/arrow-spacing)
+ Throws: error

bad

```javascript
a=>a;
() =>{};
a =>{};
```

good

```javascript
() => {};
a => {};
a => a;
() => {'\n'};
```

# block-spacing

### enforce at least one space inside of single line blocks

+ [http://eslint.org/docs/rules/block-spacing](http://eslint.org/docs/rules/block-spacing)
+ Throws: error

bad

```javascript
function foo() {return true;}
if (foo) { bar = 0;}
```

good

```javascript
function foo() { return true; }
if ( foo ) { bar = 0; }
```

# brace-style

### enforces Allman style braces

+ [http://eslint.org/docs/rules/brace-style](http://eslint.org/docs/rules/brace-style)
+ Throws: error

bad

```javascript
function foo() {
  return true;
}

try
{
  somethingRisky();
} catch(e)
{
  handleError();
}

if (foo) {
  bar();
} else {
  baz();
}
```

good

```javascript
function foo()
{
  return true;
}


if ( foo )
{
  bar();
}
else
{
  baz();
}

try
{
  somethingRisky();
}
catch ( e )
{
  handleError();
}
```

# camelcase

### Require Camelcase

+ [http://eslint.org/docs/rules/camelcase](http://eslint.org/docs/rules/camelcase)
+ Throws: error

bad

```javascript

import { no_camelcased } from "external-module"

const my_favorite_color = "#112C85";

function do_something() {
    // ...
}
```

good

```javascript
import { no_camelcased as camelCased } from "external-module";

const myFavoriteColor   = "#112C85";

function doSomething()
{
    // ...
}
```

# comma-dangle

### disallows trailing commas

+ [http://eslint.org/docs/rules/comma-dangle](http://eslint.org/docs/rules/comma-dangle)
+ Throws: error

bad

```javascript
const arr = [1,2,];

foo({
  bar: "baz",
  qux: "quux",
});
```

good

```javascript
const arr = [1,2];

foo({
  bar: "baz",
  qux: "quux"
});
```

# comma-spacing

### requires one or more spaces after commas, no spaces before one

+ [http://eslint.org/docs/rules/comma-spacing](http://eslint.org/docs/rules/comma-spacing)
+ Throws: error

bad

```javascript
const arr = [ 1 , 2];
const obj = { foo: 'bar' ,baz: 'qur'};
new Foo( a ,b );
```

good

```javascript
const arr = [ 1, 2 ];
const obj = { foo: 'bar', baz: 'qur' };
new Foo( a, b );
```

# comma-style

### requires a comma after and on the same line as an array element, or object property

+ [http://eslint.org/docs/rules/comma-style](http://eslint.org/docs/rules/comma-style)
+ Throws: error

bad

```javascript
const foo = ["apples"
           , "oranges"];

function bar() {
    return {
        "a": 1
        ,"b:": 2
    };
}
```

good

```javascript
const foo = [ "apples",
           "oranges" ];

function bar()
{
    return {
        "a"  : 1,
        "b:" : 2
    };
}
```

# computed-property-spacing

### requires one or more spaces inside computed property brackets

+ [http://eslint.org/docs/rules/computed-property-spacing](http://eslint.org/docs/rules/computed-property-spacing)
+ Throws: error

bad

```javascript
obj[foo]
const x = { [b] : a }
obj[ foo]
obj['foo' ]
```

good

```javascript
obj[ foo ]
obj[ 'foo' ]
const x = { [ b ] : a }
```

# consistent-this

### ensures that `self` is used consistently throughout the application as a stand in for `this`

+ [http://eslint.org/docs/rules/consistent-this](http://eslint.org/docs/rules/consistent-this)
+ Throws: error

bad

```javascript
const self = 42;
const that = this;

that = 42;
self = this;
```

good

```javascript
const that = 42;
const self = this;

that = 42;
self = this;
```

# constructor-super

### This rule checks whether or not there is a valid super() call.

+ [http://eslint.org/docs/rules/constructor-super](http://eslint.org/docs/rules/constructor-super)
+ Throws: error

bad

```javascript
class A {
    constructor()
    {
        super();  // This is a SyntaxError.
    }
}

class A extends B
{
    constructor()
    {}  // Would throw a ReferenceError.
}
```

good

```javascript
class A {
    constructor()
    {}
}

class A extends B
{
    constructor()
    {
        super();
    }
}
```

# eol-last

### Require file to end with single newline

+ [http://eslint.org/docs/rules/eol-last](http://eslint.org/docs/rules/eol-last)
+ Throws: error

bad

```javascript
function doSmth()
{
    const foo = 2;
}
```

good

```javascript
function doSmth()
{
    const foo = 2;
}


```

# func-call-spacing

### disallows spacing between function identifiers and their invocations

+ [http://eslint.org/docs/rules/func-call-spacing](http://eslint.org/docs/rules/func-call-spacing)
+ Throws: error

bad

```javascript

fn ();

fn
();
```

good

```javascript
fn();
```

# func-style

### enforces the consistent use of function declarations

+ [http://eslint.org/docs/rules/func-style](http://eslint.org/docs/rules/func-style)
+ Throws: error

bad

```javascript

const foo = function() {
    // ...
};

const foo = () => {};
```

good

```javascript
function foo() {
    // ...
}

// Methods (functions assigned to objects) are not checked by this rule
SomeObject.foo = function() {
    // ...
};
```

# indent

### enforces consistent 4 space indentation

+ [http://eslint.org/docs/rules/indent](http://eslint.org/docs/rules/indent)
+ Throws: error

bad

```javascript
if ( a )
{
 b=c;
  function foo( d )
  {
  e=f;
  }
}
```

good

```javascript
if ( a )
{
    b=c;
    function foo( d )
    {
        e=f;
    }
}
```

# jsx-quotes

### enforces the consistent use of double quotes in JSX attributes

+ [http://eslint.org/docs/rules/jsx-quotes](http://eslint.org/docs/rules/jsx-quotes)
+ Throws: error

bad

```javascript
<a b='c' />
```

good

```javascript
<a b="c" />
<a b='"' />
```

# key-spacing

### enforce consistent spacing between keys and values in object literal properties

+ [http://eslint.org/docs/rules/key-spacing](http://eslint.org/docs/rules/key-spacing)
+ Throws: error

bad

```javascript
call( {
    foobar: 42,
    bat:    2 * 2
} );
```

good

```javascript
call( {
    foobar : 42,
    bat    : 2 * 2
} );
```

# keyword-spacing

### enforce consistent spacing before and after keywords

+ [http://eslint.org/docs/rules/keyword-spacing](http://eslint.org/docs/rules/keyword-spacing)
+ Throws: error

bad

```javascript

if(foo) {
    //...
}else if(bar) {
    //...
}else{
    //...
}
```

good

```javascript

if (foo) {
    //...
} else if (bar) {
    //...
} else {
    //...
}
```

# linebreak-style

### enforce consistent unix style linebreak

+ [http://eslint.org/docs/rules/linebreak-style](http://eslint.org/docs/rules/linebreak-style)
+ Throws: error

bad

```javascript

const a = 'a'; // \r\n
```

good

```javascript
const a = 'a'; // \n
```

# max-len

### enforces a max line length of 80 characters.  urls are exempt from this rule

+ [http://eslint.org/docs/rules/max-len](http://eslint.org/docs/rules/max-len)
+ Throws: error

bad

```javascript
const foo = { "bar": "This is a bar.", "baz": { "qux": "This is a qux" }, "difficult": "to read" };
```

good

```javascript

const foo = {
  "bar": "This is a bar.",
  "baz": { "qux": "This is a qux" },
  "easier": "to read"
};
```

# max-statements

### enforce a maximum number of 60 statements allowed in function blocks

+ [http://eslint.org/docs/rules/max-statements](http://eslint.org/docs/rules/max-statements)
+ Throws: error

`no example because it would just be really long`

# new-cap

### require constructor names to begin with a capital letter

+ [http://eslint.org/docs/rules/new-cap](http://eslint.org/docs/rules/new-cap)
+ Throws: error

bad

```javascript
const friend = new person();
```

good

```javascript
const friend = new Person();
```

# new-parens

### require parentheses when invoking a constructor with no arguments

+ [http://eslint.org/docs/rules/new-parens](http://eslint.org/docs/rules/new-parens)
+ Throws: error

bad

```javascript
const friend = new Person;
```

good

```javascript
const friend = new Person();
```

# newline-before-return

### require an empty line before return statements

+ [http://eslint.org/docs/rules/newline-before-return](http://eslint.org/docs/rules/newline-before-return)
+ Throws: error

bad

```javascript
  if ( !bar )
  {
    bar = baz;
    return bar;
  }
```

good

```javascript
  if ( !bar )
  {
    bar = baz;

    return bar;
  }
```

# no-console

### disallow the use of console.log

+ [http://eslint.org/docs/rules/no-console](http://eslint.org/docs/rules/no-console)
+ Throws: error

bad

```javascript
console.log( 'moon' );
```

good

```javascript
console.warn( 'that shouldnt happen' );
console.error( 'something seriously wrong' );
```

# no-const-assign

### Disallow modifying constiables that are declared using const

+ [http://eslint.org/docs/rules/no-const-assign](http://eslint.org/docs/rules/no-const-assign)
+ Throws: error

bad

```javascript
const a = 0;
++a;
```

good

```javascript
const a = 0;
```

# no-else-return

### Disallow return before else

+ [http://eslint.org/docs/rules/no-else-return](http://eslint.org/docs/rules/no-else-return)
+ Throws: error

bad

```javascript
function foo()
{
    if ( x )
    {
        return y;
    }
    else
    {
        return z;
    }
}
```

good

```javascript
function foo()
{
    if ( x )
    {
        return y;
    }

    return z;
}
```

# no-extra-parens

### disallows unnecessary parentheses

+ [http://eslint.org/docs/rules/no-extra-parens](http://eslint.org/docs/rules/no-extra-parens)
+ Throws: error

bad

```javascript
a = (b * c);
(a * b) + c;
typeof (a);
```

good

```javascript
a = b * c;
a * b + c;
typeof a;
```

# no-extra-semi

### disallow unnecessary semicolons

+ [http://eslint.org/docs/rules/no-extra-semi](http://eslint.org/docs/rules/no-extra-semi)
+ Throws: error

bad

```javascript
const x = 5;;

function foo()
{
    // code
};
```

good

```javascript

const x = 5;

function foo()
{
    // code
}
```

# no-find-dom-node

### this rule, though normally enabled with react/recommended is causing problems for now and has been disabled

# no-lonely-if

###

+ [http://eslint.org/docs/rules/no-lonely-if](http://eslint.org/docs/rules/no-lonely-if)
+ Throws: error

bad

```javascript
if ( condition )
{
    // ...
}
else
{
    if ( anotherCondition )
    {
        // ...
    }
}
```

good

```javascript
if ( condition )
{
    // ...
}
else if ( anotherCondition )
{
    // ...
}
```

# no-this-before-super

### Disallows use of this/super before calling super() in constructors

+ [http://eslint.org/docs/rules/no-this-before-super](http://eslint.org/docs/rules/no-this-before-super)
+ Throws: error

bad

```javascript
class A extends B {
    constructor() {
        this.a = 0;
        super();
    }
}
```

good

```javascript
class A extends B {
    constructor() {
        super();
        this.a = 0; // OK, this is after `super()`.
    }
}
```

# no-trailing-spaces

### disallow trailing whitespace at the end of lines

+ [http://eslint.org/docs/rules/no-trailing-spaces](http://eslint.org/docs/rules/no-trailing-spaces)
+ Throws: error

bad

```javascript
const foo = 0;•••••
const baz = 5;••
•••••
```

good

```javascript
const foo = 0;
const baz = 5;
```

# no-underscore-dangle

### disallow dangling underscores in identifiers

+ []()
+ Throws: error

bad

```javascript
const foo_;
const __proto__ = {};
foo._bar();
```

good

```javascript
const foo;
const proto = {};
foo.bar();
```

# no-unneeded-ternary

### disallow ternary operators when simpler alternatives exist

+ [http://eslint.org/docs/rules/no-unneeded-ternary](http://eslint.org/docs/rules/no-unneeded-ternary)
+ Throws: error

bad

```javascript
const a = x === 2 ? true : false;

const a = x ? true : false;
```

good

```javascript
const a = x === 2;

const a = !!x;
```

# no-useless-rename

### Disallow renaming import, export, and destructured assignments to the same name

+ [http://eslint.org/docs/rules/no-useless-rename](http://eslint.org/docs/rules/no-useless-rename)
+ Throws: error

bad

```javascript
import { foo as foo } from "bar";
export { foo as foo };
let { foo: foo } = bar;
```

good

```javascript
import { foo } from "bar";
export { foo };
let { foo } = bar;
```

# no-var

### require let or const instead of var

+ [http://eslint.org/docs/rules/no-var](http://eslint.org/docs/rules/no-var)
+ Throws: error

bad

```javascript
var x = "y";
var CONFIG = {};
```

good

```javascript
let x = "y";
const CONFIG = {};
```

# no-whitespace-before-property

### isallow whitespace before properties

+ [http://eslint.org/docs/rules/no-whitespace-before-property](http://eslint.org/docs/rules/no-whitespace-before-property)
+ Throws: error

bad

```javascript
foo. bar
foo .bar
foo. bar. baz
```

good

```javascript
foo.bar
foo.bar.baz
```

# object-curly-newline

### enforce consistent line breaks inside braces

+ [http://eslint.org/docs/rules/object-curly-newline](http://eslint.org/docs/rules/object-curly-newline)
+ Throws: error

bad

```javascript
let b = {foo: 1};
```

good

```javascript
let b = {
    foo: 1
};
```

# object-curly-spacing

### enforce consistent spacing inside braces

+ [http://eslint.org/docs/rules/object-curly-spacing](http://eslint.org/docs/rules/object-curly-spacing)
+ Throws: error

bad

```javascript
const obj = {'foo': 'bar'};
const obj = {'foo': {'bar': 'baz'}, 'qux': 'quxx'};
```

good

```javascript
const obj = { 'foo': 'bar' };
const obj = { baz: { 'foo': 'qux' }, bar };
```

# object-property-newline

### enforce placing object properties on separate lines

+ [http://eslint.org/docs/rules/object-property-newline](http://eslint.org/docs/rules/object-property-newline)
+ Throws: error

bad

```javascript
const obj = { foo: "foo", bar: "bar", baz: "baz" };

const obj2 = {
    foo: "foo", bar: "bar", baz: "baz"
};
```

good

```javascript
const obj = {
    foo: "foo",
    bar: "bar",
    baz: "baz"
};
```

# one-var

### require newlines around var declarations

+ [http://eslint.org/docs/rules/one-var-declaration-per-line](http://eslint.org/docs/rules/one-var-declaration-per-line)
+ Throws: error

bad

```javascript
var foo, bar, baz = '';
```

good

```javascript
let foo;
let bar;
const baz = '';
```

# prefer-arrow-callback

###

+ [http://eslint.org/docs/rules/prefer-arrow-callback](http://eslint.org/docs/rules/prefer-arrow-callback)
+ Throws: error

bad

```javascript
foo( function( a ) { return a; } );
foo( function() { return this.a; }.bind( this ) );
```

good

```javascript
foo( a => a );
```

# prefer-const

### Suggest using const

+ [http://eslint.org/docs/rules/prefer-const](http://eslint.org/docs/rules/prefer-const)
+ Throws: error

bad

```javascript
let a = 3;
console.log(a);

let a;
a = 0;
console.log(a);
```

good

```javascript
const a = 0;
```

# prefer-template

### use template literals instead of string concatenation

+ [http://eslint.org/docs/rules/prefer-template](http://eslint.org/docs/rules/prefer-template)
+ Throws: error

bad

```javascript
const str = "Hello, " + name + "!";
const str = "Time: " + (12 * 60 * 60 * 1000);
```

good

```javascript
const str = `Hello, ${name}!`;
const str = `Time: ${12 * 60 * 60 * 1000}`;
```

# quotes

### enforce the consistent use of single quotes

+ [http://eslint.org/docs/rules/quotes](http://eslint.org/docs/rules/quotes)
+ Throws: error

bad

```javascript
const double = "double";
```

good

```javascript
const single = 'single';
```

# require-jsdoc

### require JSDoc comments

+ [http://eslint.org/docs/rules/require-jsdoc](http://eslint.org/docs/rules/require-jsdoc)
+ Throws: error

bad

```javascript
function getHeadlineWeight( headline )
{
    const words = headline.split( ' ' );

    return headline.length < 10 || words.length <= 3 ? 0 : 1;
}
```

good

```javascript
/**
 * checks the length of the headline to see how large it must be
 */
function getHeadlineWeight( headline )
{
    const words = headline.split( ' ' );

    return headline.length < 10 || words.length <= 3 ? 0 : 1;
}
```

# semi

### requires semicolons instead of ASI

+ [http://eslint.org/docs/rules/semi](http://eslint.org/docs/rules/semi)
+ Throws: error

bad

```javascript
const words = headline.split( ' ' )
```

good

```javascript
const words = headline.split( ' ' );
```


# space-before-function-paren

### disallow a space before function parenthesis

+ [http://eslint.org/docs/rules/space-before-function-paren](http://eslint.org/docs/rules/space-before-function-paren)
+ Throws: error

bad

```javascript
function withSpace (x)
{
    // ...
}
```

good

```javascript
function withoutSpace(x)
{
    // ...
}
```

# space-in-parens

### enforce spaces inside of parentheses

+ [http://eslint.org/docs/rules/space-in-parens](http://eslint.org/docs/rules/space-in-parens)
+ Throws: error

bad

```javascript
foo('bar');
const x = (1 + 2) * 3;
```

good

```javascript
foo( 'bar' );
const x = ( 1 + 2 ) * 3;
```

# space-infix-ops

### Require Spaces Around Infix Operators

+ [http://eslint.org/docs/rules/space-infix-ops](http://eslint.org/docs/rules/space-infix-ops)
+ Throws: error

bad

```javascript
a+b
a+ b
```

good

```javascript
a + b
```

# space-unary-ops

### Require spaces before & after unary operators

+ [http://eslint.org/docs/rules/space-unary-ops](http://eslint.org/docs/rules/space-unary-ops)
+ Throws: error

bad

```javascript
void{foo:0};
new[foo][0];
typeof!foo;
```

good

```javascript
void { foo : 0 };
new  [ foo ][ 0 ];
typeof !foo;
```

# template-curly-spacing

### Discourage Usage of Spacing in Template Strings

+ [http://eslint.org/docs/rules/template-curly-spacing](http://eslint.org/docs/rules/template-curly-spacing)
+ Throws: error

bad

```javascript
`hello, ${ people.name}!`;
`hello, ${people.name }!`;
```

good

```javascript
let hello = `hello, ${people.name}!`;
```

# valid-jsdoc

### enforce valid JSDoc comments

+ [http://eslint.org/docs/rules/valid-jsdoc](http://eslint.org/docs/rules/valid-jsdoc)
+ Throws: error

bad

```javascript
function add( num1, num2 )
{
    return num1 + num2;
}
```

good

```javascript
/**
 * ## add
 *
 * Add two numbers.
 *
 * @param {Number} num1 The first number
 * @param {Number} num2 The second number
 *
 * @return {Number} The sum of the two numbers.
 */
function add( num1, num2 )
{
    return num1 + num2;
}
```

# wrap-regex

### Require Regex Literals to be Wrapped

+ [http://eslint.org/docs/rules/wrap-regex](http://eslint.org/docs/rules/wrap-regex)
+ Throws: error

bad

```javascript
function a()
{
    return /foo/.test( 'bar' );
}
```

good

```javascript
function a()
{
    return ( /foo/ ).test( 'bar' );
}
```
