

## 继承
### 什么是继承？
- 子类可以使用父类中的属性或者方法
### 原型继承
- 让父类中的属性和方法，在子类原型对象的原型链上，即让子类的显式原型，指向父类的实例对象，


```javascript
	function parent() {
        this.x = 'parent';
    }
    parent.prototype.getX = function () {
        console.log(this.x);
    }

    function child() {
        this.y = 'child';
    }

    child.prototype = new parent();
    child.prototype.constructor = child;    //改变child的显式原型后child的constructor会消失
    child.prototype.getY = function () {
        console.log(this.y);
    }	
```

### call继承
- 通过使用call方法，讲父类的this指向到子类


```javascript
	function parent() {
        this.x = 'parent';
    }
    parent.prototype.getX = function () {
        console.log(this.x);
    }

    function child() {
		parent.call(this);
        this.y = 'child';
    }

    child.prototype.getY = function () {
        console.log(this.y);
    }
```

### 寄生组合继承
- call无法继承父类的公有方法，且原型继承的方法会使原本的公私方法混淆

    ```javascript
    function parent() {
        this.x = 'parent';
    }
    parent.prototype.getX = function () {
        console.log(this.x);
}
    
    function child() {
        parent.call(this);
        this.y = 'child';
    }
    
    child.prototype = Object.create(new parent());
    child.prototype.getY = function () {
        console.log(this.y);
    }
    console.log(new child());
    ```


### ES6中的继承
- class关键字实现类，类似寄生组合继承

- extends实现公共属性或方法的继承

- super实现私有属性或方法的继承

- 在constructor中首行必须写super，constructor可以省略，浏览器运行时会自动创建，类似JAVA中的构造函数
    	 
    	
    ```javascript
    class parent {
       constructor(){
       	this.A='A';
      	}
      getA(){
     		console.log(this.A);
    	}
   }
   class child extends parent{
      	constructor(){
    		super()
      		this.B='B'
      	}
      	getB(){
      		 console.log(this.B);
      	}
   }
      	 
   console.log(new child());
   ```
   
   