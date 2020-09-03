## Basics

describe('The object literal allows for new shorthands', () => {
const x = 1;
const y = 2;
describe('with variables', () => {
it('the short version for `{x: x}` is {x}', () => {
const short = {y};
assert.deepEqual(short, {y: y});
});
it('works with multiple variables too', () => {
const short = {x, y};
assert.deepEqual(short, {x: x, y: y});
});
});
describe('with methods', () => {
const func = () => func;
it('using the name only uses it as key', () => {
const short = {func};
assert.deepEqual(short, {func: func});
});
it('a different key must be given explicitly, just like before ES6', () => {
const short = {otherKey: func};
assert.deepEqual(short, {otherKey: func});
});
it('inline functions, can written as `obj={func(){}}` instead of `obj={func:function(){}}`', () => {
const short = {
inlineFunc(){return 'I am inline'}
};
assert.deepEqual(short.inlineFunc(), 'I am inline');
});
});
});

## Computed Properties

describe('Object literal properties may be computed values', () => {
it('a computed property `x` needs to be surrounded by `[]`', () => {
const propertyName = 'x';
const obj = {[propertyName]: 1};
assert.equal(obj.x, 1);
});
it('can also get a function assigned', () => {
const key = 'func';
const obj = {[key]: () => 'seven'};
assert.equal(obj.func(), 'seven');
});
it('the key may also be the result of a function call', () => {
const getName = 'propertyName';
const obj = {[getName]() {return 'seven'}};
assert.equal(obj.propertyName(), 'seven');
});
it('the key can also be constructed by an expression', () => {
const what = 'tyName';
const obj = {['proper' + what]: null};
assert('propertyName' in obj);
});
it('accessor keys can be computed names too', () => {
const obj = {
get ['key']() {return 1},

    };
    assert.equal(obj.key, 1);

});
});

## Creation

describe('Class creation', () => {
it('is as simple as `class XXX {}`', function() {
class TestClass {}
const instance = new TestClass();
assert.equal(typeof instance, 'object');
});
it('a class is block scoped', () => {
class Outside {}
{class Inside {}}
assert.equal(typeof Inside, 'undefined');
});
it('the `constructor` is a special method', function() {
class User {
constructor(id) {
this.id = id;
}
}
const user = new User(42);
assert.equal(user.id, 42);
});
it('defining a method by writing it inside the class body', function() {
class User {
writesTests() {
return false;
}
}
const notATester = new User();
assert.equal(notATester.writesTests(), false);
});
it('multiple methods need no commas (opposed to object notation)', function() {
class User {
wroteATest() { this.everWroteATest = true; }
isLazy() {
return !this.everWroteATest
}
}
const tester = new User();
assert.equal(tester.isLazy(), true);
tester.wroteATest();
assert.equal(tester.isLazy(), false);
});
it('anonymous class', () => {
const classType = typeof it
assert.equal(classType, 'function');
});
});

## Statics:

describe('Inside a class you can use the `static` keyword', () => {
describe('for methods', () => {
class UnitTest {}
it('a static method just has the prefix `static`', () => {
class TestFactory {
static makeTest() { return new UnitTest(); }
}
assert.ok(TestFactory.makeTest() instanceof UnitTest);
});
it('the method name can be dynamic/computed at runtime', () => {
const methodName = 'createTest';
class TestFactory {
static [methodName]() { return new UnitTest(); }
}
assert.ok(TestFactory.createTest() instanceof UnitTest);
});
});
describe('for accessors', () => {
it('a getter name can be static, just prefix it with `static`', () => {
class UnitTest {
static get testType() { return 'unit'; }
}
assert.equal(UnitTest.testType, 'unit');
});
it('even a static getter name can be dynamic/computed at runtime', () => {
const type = 'test' + 'Type';
class IntegrationTest {
static get [type]() { return 'integration'; }
}
assert.ok('testType' in IntegrationTest);
assert.equal(IntegrationTest.testType, 'integration');
});
});
});

## Extends:

describe('Classes can inherit from another using `extends`', () => {
describe('the default super class is `Object`', () => {
it('a `class A` is an instance of `Object`', () => {
class A {}
assert.equal(new A() instanceof Object, true);
});
it('when B extends A, B is also instance of `Object`', () => {
class A {}
class B extends A {}
assert.equal(new B() instanceof A, true);
assert.equal(new B() instanceof Object, true);
});
it('a class can extend `null`, and is not an instance of Object', () => {
class NullClass extends Object {
constructor() {
return Object.create(null);
}
}
let nullInstance = new NullClass();
assert.equal(nullInstance instanceof Object, false);
});
});
describe('instance of', () => {
it('when B inherits from A, `new B()` is also an instance of A', () => {
class A {}
class B extends A {}
assert.equal(new B() instanceof A, true);
});
it('extend over multiple levels', () => {
class A {}
class B extends A {}
class C extends B {}
assert.equal(new C instanceof A, true);
});
});
});

## Array Destructuring

describe('Destructuring arrays makes shorter code', () => {
it('extract value from array, e.g. extract 0 into x like so `let [x] = [0];`', () => {
let [firstValue] = [1];
assert.strictEqual(firstValue, 1);
});
it('get the last item from array', () => {
let [x, y, lastValue] = [1, 2, 3];
assert.strictEqual(lastValue, 3);
});
it('swap two variables, in one operation', () => {
let [x, y] = ['ax', 'why'];
[x, y] = [y, x];
assert.deepEqual([x, y], ['why', 'ax']);
});
it('leading commas', () => {
const all = ['ax', 'why', 'zet'];
const [,,z] = all;
assert.equal(z, 'zet');
});
it('extract from nested arrays', () => {
const user = [['Some', 'One'], 23];
const [[firstName, surname], age] = user;
const expected = 'Some One = 23 years';
assert.equal(`${firstName} ${surname} = ${age} years`, expected);
});
it('chained assignments', () => {
let c, d;
let [a, b] = [c, d] = [1, 2];
assert.deepEqual([a, b, c, d], [1, 2, 1, 2]);
});
it('in for-of loop', () => {
for (var [c, a, b] of [[0, 1, 2]]) {}
assert.deepEqual([a, b], [1, 2]);
});
});

## String Destructuring

describe('Destructuring also works on strings', () => {
it('destructure every character, just as if the string was an array', () => {
let [a, b, c] = 'abc';
assert.deepEqual([a, b, c], ['a', 'b', 'c']);
});
it('missing characters are undefined', () => {
const [a, b, c] = 'ab';
assert.equal(c, void 0);
});
it('unicode character work too', () => {
const [space, coffee] = ',☕';
assert.equal(coffee, '\u{2615}');
});
});

## Object Destructuring

describe('Destructure objects', () => {
it('by surrounding the left-hand variable with `{}`', () => {
const {x} = {x: 1};
assert.equal(x, 1);
});
describe('nested', () => {
it('multiple objects', () => {
const magic = {first: 23, second: 42};
const {second} = magic;
assert.equal(second, 42);
});
it('object and array', () => {
const {z:[,x]} = {z: [23, 42]};
assert.equal(x, 42);
});
it('array and object', () => {
const [,{lang}] = [null, {env: 'browser', lang: 'ES6'}];
assert.equal(lang, 'ES6');
});
});
describe('interesting', () => {
it('missing refs become undefined', () => {
const {z} = {x: 1, y: 2};
assert.equal(z, void 0);
});
it('destructure from builtins (string)', () => {
const {substr} = String();
assert.equal(substr, String.prototype.substr);
});
});
});

## Destructuring with Defaults

describe('When destructuring you can also provide default values', () => {
it('just assign a default value, like so `a=1`', () => {
const [a=1] = [];
assert.equal(a, 1);
});
it('for a missing value', () => {
const [,b=2] = [1,,3];
assert.equal(b, 2);
});
it('in an object', () => {
const [a, b=2] = [{a: 1}];
assert.equal(b, 2);
});
it('if the value is undefined', () => {
const {a, b=2} = {a: 1, b: void 0};
assert.strictEqual(b, 2);
});
it('also a string works with defaults', () => {
const [a, b=2] = '1';
assert.equal(a, '1');
assert.equal(b, 2);
});
});

## Destructuring with Parameters

describe('Destructuring function parameters', () => {
describe('destruct parameters', () => {
it('multiple params from object', () => {
const fn = ({id, name}) => {
assert.equal(id, 42);
assert.equal(name, 'Wolfram');
};
const user = {name: 'Wolfram', id: 42};
fn(user);
});
it('multiple params from array/object', () => {
const fn = ([,{name}]) => {
assert.equal(name, 'Alice');
};
const users = [{name: 'nobody'}, {name: 'Alice', id: 42}];
fn(users);
});
});
describe('default values', () => {
it('for simple values', () => {
const fn = (id=23, name='Bob') => {
assert.strictEqual(id, 23);
assert.strictEqual(name, 'Bob');
};
fn(23);
});
it('for a missing array value', () => {
const defaultUser = {id: 23, name: 'Joe'};
const fn = ([user=defaultUser]) => {
assert.deepEqual(user, defaultUser);
};
fn([]);
});
it('mix of parameter types', () => {
const fn = (id=1, [arr=2], {obj=3}) => {
assert.equal(id, 1);
assert.equal(arr, 2);
assert.equal(obj, 3);
};
fn(void 0, [], {});
});
});
});

## Destructuring with Alias

describe('Assign object property values to new variables while destructuring', () => {
describe('for simple objects', function() {
it('use a colon after the property name, like so `propertyName: newName`', () => {
const {x: y} = {x: 1};
assert.equal(y, 1);
});
it('assign a new name and give it a default value using `= <default value>`', () => {
const {x: y=42} = {y: 23};
assert.equal(y, 42);
});
});
describe('for function parameter names', function() {
it('do it the same way, with a colon behind it', () => {
const fn = ({x:y}) => {
assert.equal(y, 1);
};
fn({x: 1});
});
it('giving it a default value is possible too, like above', () => {
const fn = ({x: y=3}) => {
assert.equal(y, 3);
};
fn({});
});
});
});

## Rest as a Parameter

describe('Rest parameters in functions', () => {
it('must be the last parameter', () => {
const fn = (...rest) => {
assert.deepEqual(rest, [1, 2]);
};
fn(1, 2);
});
it('can be used to get all other parameters', () => {
const fn = (firstParam, secondParam, ...rest) => {
assert.deepEqual(rest, [3,4]);
};
fn(null, 2, 3, 4);
});
it('makes `arguments` obsolete', () => {
const fn = (...args) => {
assert.deepEqual(args, [42, 'twenty three', 'win']);
};
fn(42, 'twenty three', 'win');
});
it('eliminate `arguments`!!!', () => {
const fn = (...args) => args;
const [firstArg, ...rest] = fn(1, 2, 3);
assert.deepEqual(rest, [2, 3]);
});
});

## Rest while Destructuring

describe('Rest parameters with destructuring', () => {
it('must be last', () => {
const [...all] = [1, 2, 3, 4];
assert.deepEqual(all, [1, 2, 3, 4]);
});
it('assign rest of an array to a variable', () => {
const [, ...all] = [1, 2, 3, 4];
assert.deepEqual(all, [2, 3, 4]);
});
// the following are actually using `spread` ... oops, to be fixed #TODO
it('concat differently', () => {
const theEnd = [3, 4];
const allInOne = [1, 2, ...[...theEnd]];
assert.deepEqual(allInOne, [1, 2, 3, 4]);
});
it('`apply` made simple, even for constructors', () => {
const theDate = [2015, 1, 1];
const date = new Date(...theDate);
assert.deepEqual(date, new Date(2015, 1, 1));
});
});

## Array Spread

describe('Spread syntax with arrays', () => {
describe('basically', () => {
it('expands the items of an array by prefixing it with `...`', function() {
const middle = [1, 2, 3];
const arr = [0, ...middle, 4];
assert.deepEqual(arr, [0, 1, 2, 3, 4]);
});
it('an empty array expanded is no item', function() {
const arr = [0, ...[], 1];
assert.deepEqual(arr, [0, 1]);
});
});
describe('is (in a way) the opposite to the rest syntax', function() {
it('both use `...` to either expand all items and collect them', function() {
const [...rest] = [...[1, 2, 3, 4, 5]];
assert.deepEqual(rest, [1, 2, 3, 4, 5]);
});
it('rest syntax must be last in an array, spread can be used in any place', function() {
const [a, b, ...rest] = [1, ...[2, 3], 4, 5];
assert.equal(a, 1);
assert.equal(b, 2);
assert.deepEqual(rest, [3, 4, 5]);
});
});
describe('used as function parameter', () => {
it('prefix with `...` to spread as function params', function() {
const magicNumbers = [1, 2];
const fn = (magicA, magicB) => {
assert.deepEqual(magicA, magicNumbers[0]);
assert.deepEqual(magicB, magicNumbers[1]);
};
fn(...magicNumbers);
});
it('pass an array of numbers to Math.max()', function() {
const max = Math.max(...[23, 0, 42, 15]);
assert.equal(max, 42);
});
});  
 describe('used as constructor parameter', () => {
it('just like in a function call (is not possible using `apply`)', () => {
class X {
constructor(a, b, c) { return [a, b, c]; }
}
const args = [1, 2, 3];
assert.deepEqual(new X(...args), [1, 2, 3]);
});
});
});

## Function Defaults

describe('Default parameters make function parameters more flexible', () => {
it('define it using an assignment to the parameter `function(param=1){}`', function() {
let aNumber = (int=0) => int;
assert.equal(aNumber(), 0);
});
it('it is used when `undefined` is passed', function() {
let aNumber = (int = 23) => int;
const param = undefined;
assert.equal(aNumber(param), 23);
});
it('it is not used when a value is given', function() {
function xhr() {
return 'POST';  
 }
assert.equal(xhr('POST'), 'POST');
});
it('it is evaluated at run time', function() {
let defaultValue;
function xhr(method = `value: ${defaultValue=42}`) {
return method;  
 }
assert.equal(xhr(), 'value: 42');
});
it('it can also be a function', function() {
const defaultValue = () => 'defaultValue';
function fn(value = defaultValue()) {
return value;  
 }
assert.equal(fn(), 'defaultValue');
});
});
