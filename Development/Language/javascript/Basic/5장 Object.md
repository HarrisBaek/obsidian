---
title: 5장 Object
date: 2023-09-04
type:  blog
author: harris baek
email: baekjh09@naver.com
---
tags: #language #javascript 


```javascript
'use strict';
// Objects
// one of the JavaScript's data types.
// a collection of related data and/or functionality.
// Nearly all objects in JavaScript are instances of Object
// object = { key : value };
const obj1 = {}; // 'object literal' syntax
const obj2 = new Object(); // 'object constructor' syntax

function print(person) {
  console.log(person.name);
  console.log(person.age);
}

const ellie = { name: 'ellie', age: 4 };
print(ellie);

// with JavaScript magic (dynamically typed language)
// can add properties later
ellie.hasJob = true;
console.log(ellie.hasJob);

// can delete properties later
delete ellie.hasJob;
console.log(ellie.hasJob);

// 2. Computed properties
// key should be always string
console.log(ellie.name);
console.log(ellie['name']);
ellie['hasJob'] = true;
console.log(ellie.hasJob);

function printValue(obj, key) {
  console.log(obj[key]);
}
printValue(ellie, 'name');
printValue(ellie, 'age');

// 3. Property value shorthand
const person1 = { name: 'bob', age: 2 };
const person2 = { name: 'steve', age: 3 };
const person3 = { name: 'dave', age: 4 };
const person4 = new Person('elile', 30);
console.log(person4);

// 4. Constructor Function
function Person(name, age) {
  // this = {};
  this.name = name;
  this.age = age;
  // return this;
}

// 5. in operator: property existence check (key in obj)
console.log('name' in ellie);
console.log('age' in ellie);
console.log('random' in ellie);
console.log(ellie.random);
// 6. for..in vs for..of
// for (key in obj)
console.clear();
for (let key in ellie) {
  console.log(key);
}

// for (value of iterable)
const array = [1, 2, 4, 5];
for (let value of array) {
  console.log(value);
}

// 7. Fun cloning
// Object.assign(dest, [obj1, obj2, obj3...])
const user = { name: 'ellie', age: '20' };
const user2 = user;
console.log(user);

// old way
const user3 = {};
for (let key in user) {
  user3[key] = user[key];
}
console.clear();
console.log(user3);

const user4 = Object.assign({}, user);
console.log(user4);

// another example
const fruit1 = { color: 'red' };
const fruit2 = { color: 'blue', size: 'big' };
const mixed = Object.assign({}, fruit1, fruit2);
console.log(mixed.color);
console.log(mixed.size);

```


### 생성자 함수

```javascript
//생성자 함수는 첫글자 대문자가 기본
function User(name, age){
	//아래 생략됨
	// this = {}
	this.name = name;
	this.age = age;
	this.sayName = fuinction(){
		console.log(this.name);
	}
	//return this;
}

let user5 = new User('test',13);

//new 없으면 그냥 함수 실행이라 리턴이 없다.
let user4 = User('no',10);

user5.sayName();
```


### Computed property

```javascript
let a = 'age';

const user = {
	name :'Mike',
	[a] : 30
}
```


### Methods
#### 1. Object.assign()

```javascript
const newUser = Object.assign({},user);
const newUser = Object.assign({gender:'mail'},user);
const mergeUser = Object.assign(user1,user2); // merge 
```

#### 2. Object.keys()
```javascript
const user = {
	name : 'Mike',
	age : 30,
	gender : 'male'
}

Object.keys(user);
//["name","age","gender"]
```

#### 3. Object.values()
```javascript
const user = {
	name : 'Mike',
	age : 30,
	gender : 'male'
}

Object.values(user);
//["Mike",30,"male"]
```
#### 4. Object.entries()
```javascript
const user = {
	name : 'Mike',
	age : 30,
	gender : 'male'
}

Object.entries(user);
//[
	["name","Mike"],
	["age",30],
	["gender","male"]
]
```


#### 5. Object.fromEntries()
```javascript
const arr = {
	["name" : 'Mike'],
	["age" : 30],
	["gender" : 'male']
}

Object.entries(user);
//{
	name : 'Mike',
	age : 30,
	gender : 'male'
}
```


### Symbol

```javascript
// 다른 개발자가 만들어 놓은 객체
const user = {
	name: "mike",
	age: 30
}

// 내가 작업
// user.showName = function (){};
const showName = Symbol("show name");
user[showName] = function (){
	console.log(this.name);
}
user[showName]();

// 사용자가 접속하면 보는 메세지
for (let key in user){
	console.log(`His ${key} is ${user[key]}.`);
}

```