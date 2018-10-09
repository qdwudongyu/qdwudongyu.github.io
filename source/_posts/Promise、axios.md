---
title: Promise、axios
date: 2018-08-29 11:58:34
tags: Promise axios
---

# Promise
- JavaScript中，所有的代码都是单线程执行，导致JavaScript中所有网络操作，浏览器事件，都必须是异步操作。异步操作可以用回调函数实现。
- AJAX就是典型的异步操作-但代码不好看，且不利于代码复用
- Promise在ES6中被统一规范，由浏览器直接支持
- Promise最大的好处是**在异步执行的流程中，把执行代码和处理结果的代码清晰的分离了**`job1.then(job2).then(job3).catch(handleError);`
- 避免了回调函数造成的代码冗余，与后期维护的高额成本

# AJAX(Asynchromous JavaScript and XML)
- AJAX不是JavaScript的规范，意思是用JavaScript执行异步网络请求
- 由于form表单会在用户提交后，刷新页面-**一次HTTP请求对应一个页面**->AJAX实现不刷新页面 局部更新数据
- AJAX请求是异步执行-通过回调函数获得响应
- **写AJAX主要依靠XMLHttpRequest对象**
```javascript
    var request = new XMLHttpRequest(); // 新建XMLHttpRequest对象

    request.onreadystatechange = function () { // 状态发生变化时，函数被回调
        if (request.readyState === 4) { // 成功完成
            // 判断响应结果:
            if (request.status === 200) {
                // 成功，通过responseText拿到响应的文本:
                return success(request.responseText);
            } else {
                // 失败，根据响应码判断失败原因:
                return fail(request.status);
            }
        } else {
            // HTTP请求还在继续...
        }
    }

    // 发送请求:
    request.open('GET', '/api/categories');
    request.send();



    //执行多个并发请求
    function getUserAccount() {
      return axios.get('/user/12345');
    }

    function getUserPermissions() {
      return axios.get('/user/12345/permissions');
    }

    axios.all([getUserAccount(), getUserPermissions()])
      .then(axios.spread(function (acct, perms) {
        // 两个请求现在都执行完成 不写axios.spread(()=>{})也可以获取到对应数据 ，会将数据集成为数组
      }));
```
# async/await
- **ES7提出的async函数解决了JavaScript异步操作的回调函数问题**
- async函数是`Generator`函数的语法糖，使用关键字async来表示，在函数内部使用await来表示异步
- 相较于Generator，async函数的改进
  - 内置执行器。Generator函数的执行必须依靠执行器，而async函数自带执行器，调用方式跟普通函数的调用一致
  - 更好的语义。async和await相较于*和yield更加语义化
  - 更广的适用性。co模块约定，yield命令后面只能是Thunk函数或Promise对象。而**async函数的await命令后面则可以是Promise或则原始类型的值(Number,string,bookean,但这时等同于同步操作)**
  - 返回值是Promise。async函数返回值是Promise对象，比Generator函数返回的Iterator对象更方便，可以直接使用then()方法进行调用
  - **Promise 的方式虽然解决了 callback hell，但是这种方式充满了 Promise的 then() 方法，如果处理流程复杂的话，整段代码将充满 then。语义化不明显，代码流程不能很好的表示执行流程。**
  - async函数--流程清晰，直观、语义明显。操作异步流程就如同操作同步流程。同时 async 函数自带执行器，执行的时候无需手动加载。
  ```javascript
    // 正确的写法
    let a;
    async function correct() {
        try {
            await Promise.reject('error')
        } catch (error) {
            console.log(error);
        }
        a = await 1;
        return a;
    }
    //将可能会出错的代码放入try/catch中执行，当代码中出现错误时，catch会捕捉到错误，不会影响后续代码的正常执行
    correct().then(v => console.log(a)); // 1
  ```