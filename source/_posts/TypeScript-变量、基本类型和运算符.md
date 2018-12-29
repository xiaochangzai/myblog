---
title: TypeScript-变量、基本类型和运算符
---
基本类型    

 基本类型有`boolean`、`number`、`string`、`array`、`void`。所有类型在`TypeScript`中，都是一个唯一的顶层的`Any Type` 类型的自类型。`any`关键字代表这种类型。

| 类型          |  声明方式  |
| --------      | :----:     |
|boolean| 	var isDone:boolean=false|
|number| 	var height = 6;|
|string| 	var name:string="bob|
|array| 	var list:number[]=[1,2,3]|
|enum| 	enum Color {Red,Green,Blue}|
|any| 	var notsure:any = 4;notsure = "maybe a string instaed"; notsure = false;|

在TypeScript中，我们不能把null或undefind当作类型使用。
```
var testVar : null;//错误，类型错误
var testVar : undefined;//错误，找不到undefined
```
`var`、`let`和`const`

在TypeScript中，当声明一个变量时，可以使用var、let和const关键字
```
var mynum = 1;
let isValid:boolean = true;
const PI : number = 3.141592654;
```
联合类型
```
var path :string[]|string;
path  = '/temp/log.xml';
path = ['/temp/log.xml','/temp/error.xml'];
```
类型别名

`TypeScript`允许用`type`关键字声明类型别名
```
type PrimitiveArray = Array<string|number|boolean>;
type MyNumber = numbe;
type NgScope = ng.IScope;
type Callback = () => void;
```
函数

1.具名函数
```
function greet(name?:string):string{
 if(name){
  return "Hi," + name;
 }else{
  return "Hi!";
  }
}
```
2.匿名函数
```
var greet:(name?:string) => :string = function(name:string):string{
if(name){
  return "Hi," + name;
 }else{
  return "Hi!";
  }
}
```
类
```
class Character{
  fullname:string;
  constructor(firstname:string,lastname:string){
    this.fullname = firstname + "  " + lastname;
  }

 greet(name?:string){
   if(name){
     return "Hi!" + name + "!my name is "  + this.fullnamel;
    }else{
     return "Hi! my name is " + this fullname ;
    }
  }
}
var spark = new Character("Jacob","Keyes");
var msg = spark.greet();//"Hi! my name is Jocob Keyes";
var msg1 = spark.greet("Dr. Halsey");//"Hi!Dr. Hasey! my name is Jacob Keyes"
```