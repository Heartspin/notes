## 关于python 3.12.6 ModelNotFound

![image-20240924102916968](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240924102916968.png)

升级 pip 

```cmd
python -m ensurepip --upgrade
```

如果你在使用 Python 3.12.6，那么`distutils`应该已经自带了。你可以尝试在 Python 3.12.6 中导入`distutils`，看看是否可以成功导入。

如果你在使用的是 Python 2.x，那么`distutils`在 Python 2.7.9 及更高版本中已被移除。在这种情况下，你需要使用`pip`来安装`distutils`。在终端中运行以下命令：

```
pip install distutils
```

如果你在使用的是 Python 3.x，并且仍然遇到这个问题，那么可能是你的 Python 环境配置有问题。你可以尝试重新安装 Python，或者在不同的 Python 环境中尝试安装`distutils`。

==该问题通常是由于安装问题==

## 通过构造函数实现继承时的问题

```js
 // 借助构造函数继承父类的属性和方法
    function Father(name) {
        this.name = name
        console.log(this.name);
    }
    Father.prototype.say = function () {
        console.log('hello');
    }
    function Son(name) {
        // call() 调用函数，并修改函数内部的this指向
        Father.call(this, name)
    }
    var f = new Father('father')
    var s = new Son('ling')
    console.log(Father.prototype);
    console.log(Son.prototype);
```

![image-20241010104030067](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20241010104030067.png)

在JavaScript中，原型链是对象继承属性和方法的关键机制。每个JavaScript对象都有一个原型对象，当访问一个对象的属性或方法时，如果该对象本身没有该属性或方法，JavaScript会继续在原型链上查找，直到找到为止。

Son的实例没有直接连接到Father的原型链上，因此无法访问到Father原型上的方法。

## 通过原型对象实现继承时的问题

```js
 function Father(name) {
        this.name = name
        // console.log(this.name);
    }
    Father.prototype.say = function () {
        console.log('hello');
    }
    function Son(name) {
        // call() 调用函数，并修改函数内部的this指向
        Father.call(this, name)
    }

    var f = new Father('father')
    var s = new Son('ling')
    console.log(Son.prototype);

Son.prototype = new Father()
    // 修改子类原型对象的构造函数
    Son.prototype.constructor = Son;
    // var f = new Father('father')
    var s = new Son('ling')
    console.log(Son.prototype);
```

![image-20241010113440465](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20241010113440465.png)

![image-20241010113246458](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20241010113246458.png)

上述问题出现的直接原因就是，当修改了子类的原型对象以后，即使后期再将子类的原型对象指回自己，那么之前实例化的子类对象也还是之前的那个，依旧不会包含父类原型对象的方法，必须重新实例化或者将实例化放在，修改原型之后
