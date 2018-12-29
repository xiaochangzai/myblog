---
title: 前端使用 jest 做单元测试
tags:
  - javascript
  - npm

---
### 1. 安装 Jest
```
npm install --save-dev jest
```
### 2. 在script里面加上下面一句：
```
/ 添加测试命令
{
  "scripts": {
    "test": "jest"
  }
}
```
### 3. 添加被测试文件
```
// 被测试文件 sum.js
function sum(a, b) {
  return a + b;
}
module.exports = sum;
```
### 4. 书写测试文件
```
// 测试文件 sum.test.js
const sum = require(‘./sum');
test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```
### 5. 控制台执行
```
npm test
// 或者
npm t
```

[vue+typescript+jest测试指南](https://blog.csdn.net/u011818572/article/details/81638872)