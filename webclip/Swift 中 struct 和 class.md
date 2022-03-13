# Swift 中 struct 和 class
相对于 `Objective-C` 中的结构体，`Swift` 对结构体的使用比重大了很多，结构体成为了实现面向对象的重要工具。

Swift 中的结构体与 `C++` 和 `Objective-C` 中的结构体有很大的差别，`C++` 和 `Objective-C` 中的结构体只能定义一组相关的成员变量，而 `Swift` 中的结构体不仅可以定义成员变量（属性），还可以定义成员方法。因此，我们可以把结构体看做是一种轻量级的类。

`Swift` 中类和结构体非常类似，都具有定义和使用属性、方法、下标和构造器等面向对象特性，但是结构体不具有继承性，也不具备运行时强制类型转换、使用析构器和使用引用计等能力。

`Swift` 中 `struct` 是值类型，而 `class` 是引用类型，所以`struct` 的行为也可以用到所有的值类型上面，相同地 `class` 的行为也可以用到引用类型上。值类型的变量直接包含他们的数据，而引用类型的变量存储对他们的数据引用，因此后者称为对象，因此对一个变量操作可能影响另一个变量所引用的对象。对于值类型都有他们自己的数据副本，因此对一个变量操作不可能影响另一个变量。

##### 1. 类和结构体定义

Swift 中的类和结构体定义的语法是非常相似的。我们可以使用 class 关键词定义类，使用 struct 关键词定义结构体，它们的语法格式如下：

    // 定义类
    class 类名 {
      定义类的成员
    }
    // 创建一个 class 名称为 ClassPerson
    class ClassPerson {
      var name = "Keya"
      var age = 18
    }

    // 定义结构体
    struct 结构体名 {
      定义结构体的成员
    }
    // 创建一个 struct 名称为 StructPerson
    struct StructPerson {
      var name = "Keya"
      var age = 12
    }
    复制代码

##### 2. 类和结构体实例化

    //区别：class 在实例化的时候不能自动把 property 放在 constructor 的参数里面去，想要和 struct 一样的效果就需要我们自己去创建构造函数了。

    // 类实例化
    let classPerson = ClassPerson()
    // class 不能直接用 ClassPerson(name:"Keya",age:12) 必需要自己创建构造函数才可以
    classPerson.name = "Keya"
    classPerson.age = 12

    // 结构体实例化
    var structPerson = StructPerson(name:"Keys",age:12)
    // 另外一种实例化方法
    var structPerson = StructPerson()
    structPerson.name = "Keya"
    structPerson.age = 12
    复制代码

##### 3. 是否可变

    // 区别：let 在 class 上并不会报错。但是 Swift 常用的 String, Array, Dictionary 都是 struct，所以 let 是会有一定效果的，这里需要注意一下。

    let classPerson = ClassPerson()
    classPerson.name = "keys"
    classPerson.age = 18
    // 此处可以修改

    let structPerson = StructPerson()
    structPerson.name = "persopn"
    // 此处会报错
    复制代码

##### 4. 赋值给另外一个变量

    // 区别：
    // class 是引用类型，在赋值的时候给另外一个变量赋予了一个引用的效果，
    // struct 是值类型，它会复制一份完全相同的内容给另外一个变量，可以清晰的分辨出他们的不同之处。

    // 类赋值
    let classPerson = ClassPerson()
    classPerson.name = "keya"
    classPerson.age = 12
    // classPerson.name=keya,classPerson.age=12

    let classOPerson1 = classPerson
    classOPerson1.name = "susu"
    classOPerson1.age = 11
    // classPerson.name=susu,classPerson.age=11,classOPerson1.name=susu,classOPerson1.age=11

    // 结构体赋值
    var structerson = StructPerson()
    structerson.name = "keya"
    structerson.age = 18
    // structerson.name=keya,structerson.age=18 

    var structerson1 = structerson
    structerson1.name = "susu"
    structerson1.age = 123
    // structerson.name=keya,structerson.age=18,structerson1.name=susu,structerson1.age=123
    复制代码

##### 5. mutating 关键字

    // 区别：struct 在 function 里面需要修改 property 的时候需要加上 mutating 关键字，而 class 就不用了。



    //在不修改原 class 和 struct 的情况下添加一个 method：modifyPersonName(newName:)
    // 类
    class ClassPerson {
        var name = "keya"
        var age = 0
    }
    extension ClassPerson {
        func modifyPersonName(newName:String) {
            self.name = newName
        }
    }

    // 结构体
    struct StructPerson {
        var name = "susu"
        var age = 0
    }
    extension StructPerson {
        mutating func modifyPersonName(newName:String) {
            self.name = newName
        }
    }
    复制代码

##### 6. 关于继承

    // 区别：class 可以继承，而 struct 不可以。


    // 创建一个 继承与 ClassPerson 类的 ClassSwiftPerson：
    class ClassPerson {
        var name = "keya"
        var age = 11
    }
    extension ClassPerson {
        func modifyPersonName(newName:String) {
            self.name = newName
        }
    }
    class ClassSwiftPerson:ClassPerson {
    }

    // 实例化一个 Swift 类 ClassSwiftPerson：
    let swiftPerson = ClassSwiftPerson()       
    swiftPerson.name = "CJ"
    swiftPerson.name = "18"
    swiftPerson.modifyPersonName(newName: "帅")

    复制代码

 [https://juejin.cn/post/6983865041258807303](https://juejin.cn/post/6983865041258807303)
