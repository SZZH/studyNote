## 类

### 基础

#### 属性修饰符

1. `public` 表示当前属性为一个公开的属性，类的实例对象可以访问到。（ts中类的属性默认为public）
2. `private` 表示当前属性为一个私有属性，只能在当前类内部才能使用。
3. `protected` 表示当前为一个受保护的属性，只能在当前类或者其派生类中才能使用。
4. `readonly` 表示当前为一个只读属性。
5. `static` 与js中的static一致，不能被类的实例访问。

### 定义属性

1. ```typescript
   class Person {
     	// 类中定义的实例属性必须初始化（可以通过修改 tsconfig 文件的配置项来解除此限制）
     	name: string = 'xx'
     
     	// 或者
       name:string;
       constructor(name:string){
        this.name = name;
       }
   }
   ```
   
2. ```typescript
   class Person {
       constructor(public name:string){
       }
   }
   或者
   class Person {
       constructor(private name:string){
       }
   }
   或者
   class Person {
       constructor(protected name:string){
       }
   }
   ```

### 存取器 - 在读取或设置属性前做额外操作

```typescript
class Person {
    constructor(public mName:string){}
    //读取器
    get name (){
        retrun this.mName;
    }
    //存储器
    set name (name:string){
        this.mName = name;
    }
}
```

​	