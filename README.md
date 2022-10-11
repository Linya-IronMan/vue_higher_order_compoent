# vue_higher_order_compoent
在vue2中使用高阶组件

# 资料

- [Vue进阶必学只高阶组件 HOC](https://juejin.cn/post/6844904116603486221)

# 总结

智能组件和木偶组件解耦合。
木偶组件就是纯UI组件，智能组件则是为木偶组件提供数据以渲染。

文章中介绍的是一种通用的行为抽象。比如每次写请求的时候都需要有loading，error状态，都需要有取数据的逻辑，并且要管理这些状态。
React 社区在流行 Hook 之前，经常用 HOC 也就是高阶组件来处理这样的抽象。


vue 中组件就是一个对象，高阶组件就是一个函数接受一个对象，返回一个包装好的对象。`f(object) -> newObject`

在实际的使用过程中，组件是通过函数的返回值得到的，同样是需要进行注册。
```javascript
const hoc = withPromise(view, request)

new Vue({
  el: 'app',
  components: {
    hoc
  }
})
```


我们同样可以使用函数式编程的方式来对各种组件进行组合。
```javascript
var hoc = withLog(withPromise(view, request));

const compsosed = compose(
    withPromise(request),
    withLog,
)

const hoc = compsosed(view)
```
