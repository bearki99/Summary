##  TypeScript 学习

###  原因

​	TypeScript是JavaScript的**超集**，给JS增加了一套静态类型系统，从**动态类型语言**变成了**静态类型语言**，可以在编译的时候就检查出来问题。

普通的JS在编译的时候是查不出来类型的问题的，只有在运行的时候才会检查

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/33b13f9fef884cdc9f598930f40a42f9~tplv-k3u1fbpfcp-zoom-in-crop-mark:3780:0:0:0.awebp?)

##  TS中的类型

基本类型：number、boolean、string、bigint、symbol、undefined、null

包装类型：Number、Boolean、Object、Symbol、String

复合类型：

- 元祖：元素个数和类型固定的数组类型

  ```typescript
  type Tuple = [number, string];
  ```

- 接口：可以描述函数，对象，构造器的结构

  ```typescript
  interface IPerson {
      name: string;
      age: number;
  }
  ```

- 枚举：一系列值的复合

  ``` typescript
  enum Transpiler {
      Babel = 'babel',
      Postcss = 'postcss',
      Terser = 'terser',
      Prettier = 'prettier',
      TypeScriptCompiler = 'tsc'
  }
  
  const transpiler = Transpiler.TypeScriptCompiler;
  ```

此外还有几种特殊的类型：void never any unknown