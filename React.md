#  React

##  JSX

写的JSX会变成什么？

![jsx_03.jpg](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/63f79f34c6184f46bd628ea24351a40a~tplv-k3u1fbpfcp-zoom-in-crop-mark:3780:0:0:0.awebp)

会被编译为React Element形式，这里讲一下React.createElement的用法

**React**.**createElement**(  type,  [props],  [...children] )

- type：如果是组件类型，会传入组件对应的类/函数；如果是dom元素类型，会传入div或者span之类的字符串
- props: 一个对象，在dom中为标签属性，在组件类型中为props
- 其他参数依次为children，按照顺序进行排列

##  React底层调和处理后，终将变成什么

- 会将React element对象的每一个子节点都会形成一个与之对应的fiber对象，之后将每个fiber对象联系起来

###  fiber 类型

React针对不同的React element对象生成不同tag的fiber对象

``` typescript
export const FunctionComponent = 0;       // 函数组件
export const ClassComponent = 1;          // 类组件
export const IndeterminateComponent = 2;  // 初始化的时候不知道是函数组件还是类组件 
export const HostRoot = 3;                // Root Fiber 可以理解为根元素 ， 通过reactDom.render()产生的根元素
export const HostPortal = 4;              // 对应  ReactDOM.createPortal 产生的 Portal 
export const HostComponent = 5;           // dom 元素 比如 <div>
export const HostText = 6;                // 文本节点
export const Fragment = 7;                // 对应 <React.Fragment> 
export const Mode = 8;                    // 对应 <React.StrictMode>   
export const ContextConsumer = 9;         // 对应 <Context.Consumer>
export const ContextProvider = 10;        // 对应 <Context.Provider>
export const ForwardRef = 11;             // 对应 React.ForwardRef
export const Profiler = 12;               // 对应 <Profiler/ >
export const SuspenseComponent = 13;      // 对应 <Suspense>
export const MemoComponent = 14;          // 对应 React.memo 返回的组件
```

##  React组件

1. 类组件
2. 函数组件

###  组件通信方式

1. props
2. ref
3. React-Redux
4. context
5. event bus

- props和callback方式
  - 父组件可以通过props将消息传递给子组件，子组件可以通过执行props中的回调函数的callback来触发父组件的方法，实现父子组件通信

###  组件的强化方式

####  类组件继承

####  自定义Hooks

####  HOC高阶组件

##  setState

React V18里面是异步的 进行批量更新

##  生命周期

React两个重要阶段 render阶段和commit阶段

render阶段会深度遍历fiber树，目的是为了发现不同（diff），对于变化的组件会执行render函数，在一次调和过程完毕之后，到了commit阶段，commit阶段会修改真实的DOM节点
