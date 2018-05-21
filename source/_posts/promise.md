---
title: Promise基础知识
date: 2018-05-21 22:03:37
tags: [javascript,l2,异步]
---

1. 为什么出现Promise
    * 解决了回调地狱的难以理解、编写、修改的问题
2. 特点
    * 一旦建立，立即执行，无法取消
    * 链式调用`.then`
    * 可以捕捉错误`.then(null, onRejected)`或者`.catch()`
3. 状态
    1. pedding - 进行中
    2. fulfilled - 已成功
    3. rejected - 已失败
    * 其中，`fulfilled`和`rejected`都是已定型状态`resolved`，一旦定型就不会改变
4. 使用方法
    ```
    // new Promise()的参数是一个函数
    // 该函数的两个参数是回调函数resolve和reject
    const name = 'cross';
    const promise = new Promise((resolve, reject) => {
        if(name === 'cross'){
            resolve(name);
        }else{
            reject();
        }
    })
    // .then(resolve, reject)，then接受两个参数，并执行？
    promise.then(value => {
        // success
        console.log('==================success=================', value);
        console.log(value);
    }, error => {
        // failure
        console.log('==================failure=================', error);
    })
    ```
