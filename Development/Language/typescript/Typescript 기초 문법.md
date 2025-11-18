	

## 1. 타입스크립트를 쓰는 이유?

- 브라우저는 TS를 인식하지 못한다. (결국 JS로 변경후 사용가능)
- 그렇다면 왜? 
-> JS는 런타임에 타입이 결정되어 에러가 분명함에도 컴파일 타임에 알수가 없으므로 디버깅이 힘들다.

``` javascript
function add(num1, num2){
	console.log(num1 +num2);
}

add (); //NaN :  JS는 노티를 주지 않음
add (1); //NaN :  JS는 노티를 주지 않음
add (1,2); //NaN :  JS는 노티를 주지 않음
add (1,2,3); //12 :  JS는 노티를 주지 않음
add ('hello','world'); //NaN :  JS는 노티를 주지 않음

```


## 2. 기본 타입

```typescript

// # 기본 타입
// 타입 안써도 타입추론에 의해 자동으로 String할당
let car:String ='bmw';
car =3;

let age:number=30;
//multi type
let isAdult:boolean | string =true;
let a:number[] = [1,2,3];
let a2:Array<number> = [1,2,3]; 

let week1:string[] = ['mon', 'tue','wed'];
let week2:Array<string> =['mon','tue','wed']; 

week1.push()

/*************************************************************/
// 튜플(Tuple)
let b:[string, number];
b=['z',1];
// b=[1,'z'] > error  

b[0].toLowerCase();
b[1].toLowerCase(); //error  

/*************************************************************/
//void :반환값이 없을때
function sayHello():void{
	console.log('test')
}

/*************************************************************/
//never : 영원히 반환되지 않을때
function showError():never{
	throw new Error();
}
function infLoop():never{
	while(true){
		//do something..
	}
}

/*************************************************************/
//enum
//기본으로는 0~2까지 지정
//하나값을 뒤로 지정하면 그뒤는 자동지정됨
// Os[Window] = 0, Os[0]= 'Window'
enum Os{
	Window, //0
	Ios, //1
	Android //2
}

let myOs:Os;
myOs = Os.Window
/*************************************************************/

//null, undefined
let a:null = null;
let c:undefined = undefined;

/*************************************************************/

```


## 3. 인터페이스 (Interface)

```typescript
let user:object;
user = {
	name:'xx',
	age:30
}
console.log(user.age) // error(구조가 없다)

type Score ='A'| 'B'|'C'|'D'|'E'|'F';//값의 제한

interface User{
	name:string;
	age:number;
	gender?:string있어도 되고 없어도됨
	readonly birth:number; //생성에만 할당 가능
	[grade:number]re;
}

let user1:User = {
	name:'xx',
	age:30,
	birthYear :20,
	1: 's', // s is not in Score
	2: 'C' // valid
}

user1.age = 10;
user1.gender = 'male'
user1.birthYear = 10 //read only error  

////////////////////////////////////////////////

//함수 구조도 정의 가능

interface Add{
	(num1:number, num2:number):number;
}
  
const addFunc :Add = function(x,y){
	return x+y;
}

add(10,'20') // error 

////////////////////////////////////////////////
 
interface IsAdult{
	(age:number):boolean;
}

const a:IsAdult = (age)=>{
	return age>19;
}

a(33) // return true  

////////////////////////////////////////////////

//Class 정의
interface Car{
	color:string;
	wheels:number;
	start(): void;
}

class Bmw implements Car{
	color;
	wheels=4;
	constructor(c:string){
	this.color =c;
	start(){
		console.log('go..');
	}
}

const b= new Bmw('green');
console.log(b)
b.start()

//extends
interface Benz extends Car{
	door:number;
	stop(): void;
}
  
const benz:Benz = {
	//extends 하면 전체 다 적어줘야 함
	door:5,
	color:'black',
	wheels:4,
	start(){
		console.log('go..');
	},

	stop(){
		console.log('stop');
	}
}

////////////////////////////////////////////////
// 여러개 사용가능
interface Car{
	color:String;
	wheels:number;
	start():void;
}
  
interface Toy{
	name: string;
}
 
interface ToyCar extends Toy, Car{
	price: number;
}

```


## 4. 함수 - function 

```typescript
// 함수

function add(num1: number, num2: number):void{
// return num1 +num2;
	console.log(num1 +num2);
}
 
function isAdult( age : number ): boolean {
	return age > 19;
}  

//Optional parameter
function hello(name?: string){ //Optional로 없을수도 있다라고 알려줌
	return `Hello ${name || "world"}`;
}  

// function hello(name = "world"){ //Optional로 없을수도 있다라고 알려줌
// return `Hello ${name}`;
// }  

const result = hello();
const result2 = hello("Sam");
// const result3 = helll(20); //error

  //Optional parameter->옵셔널은 젤 마지막
function hello2(name:string, age?: number):string{
	if(age !== undefined){
		return`Hello, ${name}. You are ${age}.`;
	}else{
		return `Hello, ${name}`;
	}
}

  

//Multiple vargs
function add1(...nums:number[]){
	return nums.reduce((result, num)=>result+ num,0);
}

interface User{
	name:string;
}

const Sam:User = {name:'Sam'}  

function showName(this:User, age:number, gender:'m'|'f'){
	console.log(this.name,age, gender);
}

const a = showName.bind(Sam);
a(30,'m');


//function Overroad
interface User{
	name:string;
	age: number;
}  


function join(name:string, age:string):string; //age가 string이면 string
function join(name:string, age:number):User; //age가 number이면 User
function join(name:string, age:number|string):User|string{
	if(typeof age ==="number"){
		return {
			name,
			age,
		}
	}else{
		return "나이는 숫자로 입력해주세요.";
	}
}  

const sam:User = join ("Sam",30);
const jane:string = join("Jane",30);

```


## 5. 리터럴 타입, 유니온/교차 타입

```typescript
//Literal types

const userName = "bob";
let userName2: string | number ="Tom";
userName2 = 3; //error

type Job = "police"| "developer"| "teacher";
interface User{
	name: string;
	job :Job;
} 

const user:User={
	name: "Bob",
	job:"student" //error
}

//UnionType :식별 가능한 유니온 타입
interface Car{
	name:"car";
	color:string;
	start(): void;
}
interface Mobile{
	name:"mobile";
	color:string;
	call():void;
}
function getGift(gift:Car | Mobile){
	console.log(gift.color);
	if(gift.name ==="car"){
		gift.start();
	}else{
		gift.call();
	}
} 

//Intersection Types :교차 타입
interface Car1{
	name:string;
	start(): void;
}

interface Toy1{
	name:string;
	color:string;
	price:number;
}
	
const toyCar: Toy1 & Car1 = {
	//모두다 정의해 줘야 한다.
	name:"Tayo",
	start(){},
	color:"Red",
	price:10
}
```


## 6. 클래스 Class
```typescript
class Car{
	color:string;
	constructor(color:string){
	this.color = color;
}
	start(){
		console.log("start");
	}
}

  

//ES6는 접근제한자 못씀
//접근 제한자(Access modifier) - public, private, protected
class Car2{
// private name:string="car"
// #name:string="car";//# === private
	readonly name:string ="car";
	protected protectedName:string = "car"
	color:string;
	
	constructor(color:string){	
		this.color = color;	
	}

		start2(){	
		console.log("Start)")	
		console.log(this.#name);	
		console.log(this.protectedName);
	}
}

  

class Bmw extends Car2{
	constructor(color:string){
		super(color);
	}

	showName(){
		//can not access in child class
		console.log(super.#name);
		console.log(super.protectedName);
	}
}


const z4 = new Bmw("black");
z4.name = "zzz4";

```


## 6. 제네릭 Generics

```typescript
//클래스, 함수, 인터페이스를 다양한 타입으로 재사용이 가능하다.
//정의만 하고 사용할때 실제 타입을 정한다
function getSize<T>(arr:T[]):number{
	return arr.length;
}
 
const arr1= [1,2,3];
getSize<number>(arr1);  

const arr2 = ['a','b','c']
getSize<string>(arr2); 

const arr3 = [false, true, true]
getSize<boolean>(arr3);  

interface Mobile<T>{
	name:string;
	price:number;
	option: T;
}


const m1:Mobile<{color:string, coupon:boolean}>={
	name:"S21",
	price: 1000,
	option:{
		color: "Red",
		coupon: false,
	},
}  

const m2:Mobile<string> = {
	name:"s20",
	price:900,
	option:"good",
}
///////////////////////////////////////

interface User{
	name:string;
	age:number;
}

interface Car{
	name:string;
	color:string;
}

interface Book{
	price: number;
}

const user:User = {name:"a",age:10};
const car:Car = {name:"bmw",color:"red"};
const book:Book = {price:3000};  

function showName<T extends {name:string}>(data:T): string{
	return data.name;
}
 

showName(user);
showName(car);
showName(book); //error
```


## 7. 유틸리티 타입 Utility Types

```typescript
//keyof

interface User{
	id:number;
	name: string;
	age:number;
	gender:'m'|'f';
}

type UserKey = keyof User; //'id'|'name'|'age'|'gender'
const uk:UserKey = "age"; 

//Partial<T>
interface User{
	id:number;
	name:string;
	age:number;
	gender:"m"|"f";
}

  //same as ? (optional)
let admin: Partial<User> ={
	id:1,
	name:"Bob"
}

//Required<T>
//?(optional)이 있더라도 무조건 채워야함
interface User2{
	id:number;
	name:string;
	age?:number;
}

  

let admin2:Required<User2>={
	id:1,
	name:"Bob",
	age:30
}

//Readonly
interface User3{
	id:number;
	name:string;
	age?:number;
}

let admin3: Readonly<User3> = {
	id:1,
	name:"Bob",
}

admin3.id = 4; //error  

//Record<K,T>
type Grade = "1" |"2"|"3" |"4";
type Score = "A" | "B" | "C" |"D"; 

const score: Record<Grade, Score> = {
	1:"A",2:"B",3:"C",4:"D"
}

interface User4{
	id:number;
	name:string;
	age: number;
}

function isValid(user:User4){
	const result:Record<keyof User4, boolean> = {
		id:user.id > 0,
		name: user.name !== '',
		age:user.age > 0
	}

	return result;
}

//Pick<T,K>
//Partial과 비슷하나 그냥 딱 저앻놓는거
interface User5{
	id:number;
	name:string;
	age: number;
	gender: "M"|"W";

}

const admin5: Pick<User5,"id"|"name"> = {
	id:0,
	name:"Bob",
}

//Omit<T,K>
interface User6{
	id:number;
	name:string;
	age: number;
	gender: "M"|"W";
}
  

const admin6: Omit<User6,"age"|"gender"> = {
	id:0,
	name:"Bob",
}
  

//Exclude<T1, T2>
type T1 = string | number | boolean;
type T2 = Exclude<T1, number | string>;  

//NonNullable<Type>
type T3 = string | null | undefined | void;
type T4 = NonNullable<T1>

```