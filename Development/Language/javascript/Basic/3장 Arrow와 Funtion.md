---
title: 3장 Arrow와 Funtion
date: 2023-09-04
type: blog
author: harris baek
email: baekjh09@naver.com
tags:
  - language
  - javascript
---
 


### 1. 함수 - Function 
- Input을 넣어 output을 내어주는것이 함수라고 한다.
- 재사용이 가능함
- JS에서는 함수는 오브젝트의 일종이다.
**하나의 함수는 하나의 일만 담당해야한다.**
```ad-note
title: 함수 선언
function name(param1, param2) {body ... return}
```

```javascript
"use strict";

// 1. Function

function printHello(){
	console.log('Hello');
}

function log(message){
	console.log(message);
}

log('Hello@');
log(1234);



// 1. Parameters
// premitive parameters : passed by value
// object parameters: passed by reference
function changeName(obj){
obj.name = 'coder';
}

const ellie = {name:'ellie'};

changeName(ellie);

console.log(ellie)

// 3. Default paramters (added in ES6)
function showMessage(messsage, from = 'unknown'){
	console.log('${message}by ${from}')
}

// 4. Rest parameters (added in ES6)
function printAll(...args){
	for(let i =0; i<args.length; i++){
		console.log(args[i]);
	}
	for (const arg of args){
		console.log(arg)
	}
args.forEach(arg=>console.log(arg));
}

// 5. Local scope
let globalMessage = 'global';
function printMessage(){
	let message  ='hello';
	console.log(message);
	console.log(globalMessage);
}

printAll('dream','coding','ellie');

```

