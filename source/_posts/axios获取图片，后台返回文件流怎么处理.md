---
title: axios获取图片，后台返回文件流怎么处理
---
#### 今天调一个返回图片的接口，图片是以文件流的格式返回的。

##### 如何才能正确的显示图片呢？
#### 1. 请求时在header设置返回类型。指定返回类型为 ==blob==
```
  /**
   * 
   * @param {tai} string 生成订阅号海报
   */
  static getSubscriptionPicture ({
    tai
  }: {tai: string}) {
    return http.post({
      url: this.subscription,
      data: {},
      config: {
        requiresAuth: true,
        params: {
          tai
        },
        responseType: 'blob'
      }
    })
  }
```
#### 2. 使用原生js自带的 ==URL.createObjectURL== 函数。
```
this.card = URL.createObjectURL(res.data)
```
##### 这样将==this.card==放在img的src上面就行了