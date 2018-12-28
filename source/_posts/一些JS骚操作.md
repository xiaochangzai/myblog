---
title: 一些JS骚操作
---

## 一、强制类型转换
##### 1.1 string强制转换为数字
```
//可以用*1来转化为数字((实际上是调用.valueOf方法) 然后使用Number.isNaN来判断是否为NaN，或者使用 a !== a 来判断是否为NaN)
'32' * 1            // 32
'ds' * 1            // NaN
null * 1            // 0
undefined * 1    // NaN
1  * { valueOf: ()=>'3' }        // 3
//使用+来转化字符串为数字
+ '123'            // 123
+ 'ds'               // NaN
+ ''                    // 0
+ null              // 0
+ undefined    // NaN
+ { valueOf: ()=>'3' }    // 3
```
##### 1.2 使用Boolean过滤数组中的所有假值
```
const compact = arr => arr.filter(Boolean)
compact([0, 1, false, 2, '', 3, 'a', 'e' * 23, NaN, 's', 34]) 
```
##### 1.3 数值取整 --去除小数点后面的值
```
~~2.33
2.33 | 0
2.33 >> 0
//Math.floor()向下取整,值永远只会变小
```
##### 1.4 判断奇偶数,负数同样适用
```
const num=3;
!!(num & 1)                    // true
!!(num % 2)                    // true
//以上两种形式返回true的都是奇数
```
#####  JS|| && 妙用 多重if else 选择情况
```
/**
假设对成长速度显示规定如下:
成长速度为5显示1个箭头
成长速度为10显示2个箭头
成长速度为12显示3个箭头
成长速度为15显示4个箭头
其他显示为0个箭头
*/
//一般代码
var add_level = 0; 
if(add_step == 5){ 
add_level = 1; 
} 
else if(add_step == 10){ 
add_level = 2; 
} 
else if(add_step == 12){ 
add_level = 3; 
} 
else if(add_step == 15){ 
add_level = 4; 
} 
else { 
add_level = 0; 
} 

//好一点的switch
var add_level = 0; 
switch(add_step){ 
    case 5 : add_level = 1; 
    break; 
    case 10 : add_level = 2; 
    break; 
    case 12 : add_level = 3; 
    break; 
    case 15 : add_level = 4; 
    break; 
    default : add_level = 0; 
    break; 
}

//更好一点的
var add_level = (add_step==5 && 1) || (add_step==10 && 2) || (add_step==12 && 3) || (add_step==15 && 4) || 0; 

//还有更好的
var add_level={'5':1,'10':2,'12':3,'15':4}[add_step] || 0; 
```
## 二、函数
##### 2.1 惰性载入函数
```
//这个判断依据在整个项目运行期间一般不会变化，所以判断分支在整个项目运行期间只会运行某个特定分支，那么就可以考虑惰性载入函数
function foo(){
    if(a !== b){
        console.log('aaa')
    }else{
        console.log('bbb')
    }
}

// 优化后
function foo(){
    if(a != b){
        foo = function(){
            console.log('aaa')
        }
    }else{
        foo = function(){
            console.log('bbb')
        }
    }
    return foo();
}
```
##### 2.2 动态添加js
```javascript
//动态添加js
document.write("<script src='" + context.path + "/resource/apps/logger.js'></script>");

/**
 * 动态添加JS
 * @param {Object} js
 */
function loadJs(js) {
    var s = document.createElement('script');
    s.setAttribute('type', 'text/javascript');
    s.setAttribute('src', js);
    var content = document.getElementById("container-fluid");
    content.appendChild(s);
}
```
## 三、数组
##### 3.1 reduce方法同时实现map和filter
```javascript
const numbers = [10, 20, 30, 40];
const doubledOver50 = numbers.reduce((finalList, num,currentIndex,numbers) => {
  
  console.log(finalList);
  console.log(num);
  console.log(currentIndex);
  console.log(numbers);
  num = num * 2;
  if (num > 50) {
    finalList.push(num);
  }
  return finalList;
}, []);
```
##### 五种方法实现值交换
```javascript

1. var temp = a; a = b; b = temp; //(传统，但需要借助临时变量)
 
2. a ^= b; b ^= a; a ^= b; //(需要两个整数)
 
3. b = [a, a = b][0] //(借助数组)
 
4. [a, b] = [b, a]; //(ES6，解构赋值)
 
5. a = a + b; b = a - b; a = a - b; //(小学奥赛题)
```
##### 去掉小数部分
```
parseInt(num)
 
~~num
 
num >> 0
 
num | 0
```
##### 判断x是否是整数
```

function isInt(x) {
 
  return (x ^ 0) === x
 
}
 
// return Math.round(x) === x
 
// return (typeof x === 'number') && (x % 1 === 0)
 
// ES6 -> Number.isInteger()
```
##### 数组去重
```
// ES6
 
Array.from(new Set(arr))
 
 
 
// ES5
 
arr.filter(function(ele, index, array){
 
    return index===array.indexOf(ele)
 
})
```
##### 数组最大值
```
function maxArr(arr) {
 
 return Math.max.apply(null, arr)
 
}

```
##### 数组最小值
```
function minArr(arr) {
 
 return Math.min.apply(null, arr)
 
}

```
##### 随机获取数组的一个成员
```
function randomOne(arr) {
 
 return arr[Math.floor(Math.random() * arr.length)]
 
}

```
##### 产生随机颜色
```
function getRandomColor() {
 
    return `#${Math.random().toString(16).substr(2, 6)}`
 
}

```
##### 随机生成指定长度字符串
```
function randomStr(n) {
    let standard = 'abcdefghijklmnopqrstuvwxyz9876543210'
    let len = standard.length
    let result = ''

    for (let i = 0; i < n; i++) {
        result += standard.charAt(Math.floor(Math.random() * len))
  }
  return result
}
```
##### 深拷贝
```
JSON.parse(JSON.stringify(obj))
```
##### 