## 模拟call



第一个参数为null或者undefined时，this指向全局对象window，值为原始值的指向该原始值的自动包装对象，如 String、Number、Boolean
为了避免函数名与上下文(context)的属性发生冲突，使用Symbol类型作为唯一值
将函数作为传入的上下文(context)属性执行
函数执行完成后删除该属性
返回执行结果

```js
Function.prototype.myCall = function(context, ...args) {

    context =  (context ?? window) || new Object(context)

    const key = Symbol()

    context[key] = this

    const result = contextkey

    delete context[key]

    return result

}

```



注： 代码实现使用了ES2020新特性Null判断符 ??， 详细参考阮一峰老师的ECMAScript 6 入门

# 模拟apply



前部分与call一样
第二个参数可以不传，但类型必须为数组或者类数组

``` js
Function.prototype.myApply = function(context) {

    context =  (context ?? window) || new Object(context)

    const key = Symbol()

    const args = arguments[1]

    context[key] = this

    let result

    if(args) {

        result = contextkey

    } else {

        result = context[key]

    }

    delete context[key]

    return result

}

```


注：代码实现存在缺陷，当第二个参数为类数组时，未作判断（有兴趣可查阅一下如何判断类数组）

# 模拟bind#







使用 call / apply 指定 this
返回一个绑定函数
当返回的绑定函数作为构造函数被new调用，绑定的上下文指向实例对象
设置绑定函数的prototype 为原函数的prototype

```js
Function.prototype.myBind = function(context, ...args) {

    const fn = this

    const bindFn = function (...newFnArgs) {

        fn.call(

            this instanceof bindFn ? this : context,

            ...args, ...newFnArgs

        )

    }

    bindFn.prototype = Object.create(fn.prototype)

    return bindFn

}

```



# 模拟new#



创建一个新的空对象
把this绑定到空对象
使空对象的__proto__指向构造函数的原型(prototype)
执行构造函数，为空对象添加属性
判断构造函数的返回值是否为对象，如果是对象，就使用构造函数的返回值，否则返回创建的对象
const createNew = (Con, ...args) => {
    const obj = {}
    Object.setPrototypeOf(obj, Con.prototype)
    let result = Con.apply(obj, args)
    return result instanceof Object ? result : obj
}


# 模拟instanceOf#



遍历左边变量的原型链，直到找到右边变量的 prototype，如果没有找到，返回 false

```js
const myInstanceOf = (left, right) => {

    let leftValue = left.proto

    let rightValue = right.prototype

    while(true) {

        if(leftValue === null) return false

        if(leftValue === rightValue) return true

        leftValue = leftValue.proto

    }

}

```



# 深拷贝（简单版）#



判断类型是否为原始类型，如果是，无需拷贝，直接返回
为避免出现循环引用，拷贝对象时先判断存储空间中是否存在当前对象，如果有就直接返回
开辟一个存储空间，来存储当前对象和拷贝对象的对应关系
对引用类型递归拷贝直到属性为原始类型

```js
const deepClone = (target, cache = new WeakMap()) => {

    if(target === null || typeof target !== 'object') {

        return target

    }

    if(cache.get(target)) {

        return target

    }

    const copy = Array.isArray(target) ? [] : {}

    cache.set(target, copy)

    Object.keys(target).forEach(key => copy[key] = deepClone(obj[key], cache))

    return copy

}

```



# 深拷贝(尤雨溪版)#



vuex源码

原理与上一版类似

```js
function find(list, f) {

    return list.filter(f)[0]

}

function deepCopy(obj, cache = []) {

    // just return if obj is immutable value

    if (obj === null || typeof obj !== 'object') {

        return obj

    }

```



```js
// if obj is hit, it is in circular structure
const hit = find(cache, c => c.original === obj)
if (hit) {
    return hit.copy
}
 
const copy = Array.isArray(obj) ? [] : {}
// put the copy into cache at first
// because we want to refer it in recursive deepCopy
cache.push({
    original: obj,
    copy
})
Object.keys(obj).forEach(key => copy[key] = deepCopy(obj[key], cache))
 
return copy
}
```



# 函数防抖#



this继承自父级上下文，指向触发事件的目标元素
事件被触发时，传入event对象
传入leading参数，判断是否可以立即执行回调函数，不必要等到事件停止触发后才开始执行
回调函数可以有返回值，需要返回执行结果

 ```js
const debounce = (fn, wait = 300, leading = true) => {

    let timerId, result

    return function(...args) {

        timerId && clearTimeout(timerId)

        if (leading) {

            if (!timerId) result = fn.apply(this, args)

            timerId = setTimeout(() => timerId = null, wait)

        } else {

            timerId = setTimeout(() => result = fn.apply(this, args), wait)

        }

        return result

    }

}

 ```




# 函数节流(定时器)#



```js
const throttle = (fn, wait = 300) => {

    let timerId

    return function(...args) {

        if(!timerId) {

            timerId = setTimeout(() => {

                timerId = null

                return result = fn.apply(this, ...args)

            }, wait)

        }

    }

}

```




# 函数节流(时间戳)#



```js
const throttle = (fn, wait = 300) => {

    let prev = 0

    let result

    return function(...args) {

        let now = +new Date()

        if(now - prev > wait) {

            prev = now

            return result = fn.apply(this, ...args)

        }

    }

}

```




# 函数节流实现方法区别#



方法	使用时间戳	使用定时器
开始触发时	立刻执行	n秒后执行
停止触发后	不再执行事件	继续执行一次事件
数组去重

```js
const uniqBy = (arr, key) => {

    return [...new Map(arr.map(item) => [item[key], item])).values()]

}

const singers = [

    { id: 1, name: 'Leslie Cheung' },

    { id: 1, name: 'Leslie Cheung' },

    { id: 2, name: 'Eason Chan' },

]

console.log(uniqBy(singers, 'id'))

//  [

//    { id: 1, name: 'Leslie Cheung' },

//    { id: 2, name: 'Eason Chan' },

//  ]

```



原理是利用Map的键不可重复

# 数组扁平化（技巧版)#



```js
const flatten = (arr) => arr.toString().split(',').map(item => +item)
```


复制代码

# 数组扁平化#



```js
const flatten = (arr, deep = 1) => {

  return arr.reduce((cur, next) => {

    return Array.isArray(next) && deep > 1 ?

      [...cur, ...flatten(next, deep - 1)] :

      [...cur, next]

  },[])

}

```




# 函数柯里化#



```js
const currying = (fn) {

    _curry = (...args) => 

        args.length >= fn.length

        ? fn(...args)

        : (...newArgs) => _curry(...args, ...newArgs)

}

```



原理是利用闭包把传入参数保存起来，当传入参数的数量足够执行函数时，就开始执行函数

# 发布订阅EventEmitter#



```js
class EventEmitter {

    #subs = {}

    emit(event, ...args) {

        if (this.#subs[event] && this.#subs[event].length) {

            this.#subs[event].forEach(cb => cb(...args))

        }

    }

    on(event, cb) {

        (this.#subs[event] || (this.#subs[event] = [])).push(cb)

    }

    off(event, offCb) {

    if (offCb) {

        if (this.#subs[event] && this.#subs[event].length)

            this.#subs[event] = this.#subs[event].filter(cb => cb !== offCb)

      } else {

        this.#subs[event] = []

      }

    }

}

```



subs是EventEmitter私有属性(最新特性参考阮一峰老师的ECMAScript 6 入门)，通过on注册事件，off注销事件，emit触发事件

# 寄生组合继承#



```js
 function Super(foo) {

    this.foo = foo

  }

  Super.prototype.printFoo = function() {

    console.log(this.foo)

  }

  function Sub(bar) {

    this.bar = bar

    Super.call(this)

  }

  Sub.prototype = Object.create(Super.prototype)

  Sub.prototype.constructor = Sub

```

 


# ES6版继承#

```js
class Super {

    constructor(foo) {

      this.foo = foo

    }

    printFoo() {

      console.log(this.foo)

    }

  }

  class Sub extends Super {

    constructor(foo, bar) {

      super(foo)

      this.bar = bar

    }

  }

```



  

