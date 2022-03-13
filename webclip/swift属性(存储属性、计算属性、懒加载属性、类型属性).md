# swift属性(存储属性、计算属性、懒加载属性、类型属性)
这是我参与更文挑战的第 11 天，活动详情查看： [更文挑战](https://juejin.cn/post/6967194882926444557 "https&#x3A;//juejin.cn/post/6967194882926444557")

### 存储属性

-   存储属性：将常量或变量值存储为实例的一部分 (结构体和类都支持存储属性)
-   结构体和类中，变量存储属性用关键字`var`声明，常量存储属性用关键字`let`声明
-   结构体实例赋值给常量，该实例属性不能被修改

    ```js
    struct Teacher {
        let name = ""
        var age = 0
    }

    var teacherA = Teacher()
    teacherA.age = 30
    teacherA.name = "TeacherA"    


    let teacherB = Teacher()
    teacherB.age = 30            
    teacherB.name = "TeacherB"   
    ```

    Teacher 结构体分别定义了常量存储属性 name 和变量存储属性 age。使用关键字 `var` 定义的 teacherA， 该实例无法修改常量属性，但是可以修改变量属性。使用关键字 `let` 定义的 teacherB，该实例无法修改常量属性和变量属性。因为结构体属于值类型，当值类型的实例被声明为常量的时候，它的所有属性也就成了常量
-   类实例赋值给常量，可以修改该实例变量属性（类属于引用类型）

    ```js
    class Teacher {
        let name = ""
        var age = 0
    }

    var teacherA = Teacher()
    teacherA.age = 30
    teacherA.name = "TeacherA"    


    let teacherB = Teacher()
    teacherB.age = 30            
    teacherB.name = "TeacherB"   
    ```

    Teacher 类分别定义了常量存储属性 name 和变量存储属性 age。由于类是引用类型，所以不管是使用类的变量实例还是常量实例，都可以修改变量属性的值，但是依然不能修改常量属性的值

* * *

### 懒加载存储属性

-   懒加载存储属性：当第一次被调用的时候才会计算其初始值的属性，在属性声明前使用关键字`lazy`来表示延迟存储属性
-   懒加载存储属性的声明使用关键字`var`，因为在实例初始化完成之前可能无法检索其初始值。常量属性在初始化完成之前必须始终有一个值，因此不能声明为惰性

```js
class Friend{
    var name: String!
    init() {
        print("Friend 初始化")
    }
}

class Hobby{
    var name: String!
    init() {
        print("Hobby 初始化")
    }
}

class Student {
    var name: String!
    var hobby :Hobby = Hobby()
    lazy var friend:Friend = Friend()
}
var stu = Student()
print("---完美分割线---")
stu.friend.name = "韩梅梅"

log:
Hobby 初始化
---完美分割线---
Friend 初始化
```

当初始化 Student 时，没有用关键字`lazy`修饰的属性 hobby 会随着 Student 初始化而初始化，使用关键字`lazy`修饰的属性 friend 在使用时才执行初始化

* * *

### 计算属性

-   计算型属性：不直接存储值，而是通过`setter`、`getter`方法来取值或赋值
-   计算属性只能用关键字`var`声明

    ```js
    class Student {
        var firstName = ""
        var lastName = ""

        
        var fullName:String {
            
            get{
                return firstName + lastName
            }
            
            set(newValue){
                self.firstName = newValue.components(separatedBy: " ")[0]
                self.lastName = newValue.components(separatedBy: " ")[1]
            }
        }
    }

    let student = Student()
    student.fullName = "xiao ming"
    print(student.firstName)    
    print(student.lastName)   

    log:
    xiao
    ming
    ```

    定义一个 Student 类，存储属性分别是 firstName 和 lastName，根据这俩个存储属性可以获取 fullName，所以声明一个计算属性 fullName，通过提供的`setter`和`getter`方法进行 fullName 的逻辑处理
-   只读计算属性：只有`getter`方法，没有`setter`方法的计算属性。只读计算属性始终返回一个值，可以通过点语法访问，但不能设置为其他值

    ```js
    class Student {
        var firstName = ""
        var lastName = ""
        var fullName:String {
            get{
                return firstName + lastName
            }
        }
    }

    let student = Student()
    student.firstName = "xiao"
    student.lastName = "ming"
    print(student.fullName)    

    log:
    xiaoming
    ```
-   只读计算属性的声明，也可以删除关键字`getter`方法及其`{}`

    ```js
    class Student {
        var firstName = ""
        var lastName = ""
        var fullName:String {
            return firstName + lastName
        }
    }
    ```

* * *

### 属性观察者

-   属性观察者：观察和响应属性值的变化。每次属性的值被更新时，属性观察者都会被调用，即使新值和属性当前的值是一样的
-   任何存储属性都可以添加属性观察者（赖加载属性除外），如果是继承的属性，可以通过在子类中覆盖该属性来添加属性观察者。如果是计算属性，使用属性的`setter`方法来观察和响应值的更改，而不需要创建观察者
-   使用`willSet`在新的值被更新之前调用。(`willSet`会将新属性值作为常量参数传入，可以在此参数指定一个名称，如果没有指定，默认名称`newValue`表示)
-   使用`didSet`在新的值被设置之后调用。(`didSet`会将旧属性值作为参数传入，可以在此参数指定一个名称，如果没有指定，默认参数名`oldValue`表示)

    ```js
    class Student {
        var name:String = "" {
            
            willSet(newName){
                print("新值是：\(newName)")
            }
            
            didSet{
                print("旧值是：\(oldValue)")
            }
        }
    }
    let student = Student()
    student.name = "小白"
    print("---完美分割线---")
    student.name = "小黑"

    log:
    新值是：小白
    旧值是：
    ---完美分割线---
    新值是：小黑
    旧值是：小白
    ```
-   父类的属性在子类的初始化中被赋值时，它在父类中的 `willSet` 和 `didSet` 观察者会被调用，随后才会调用子类的观察者。在父类初始化方法调用之前，子类给属性赋值时，观察者不会被调用

    ```js
    class Person {
        var name:String = ""{
            willSet(newName){
                print("父类新值是：\(newName)")
            }
            didSet{
                print("父类旧值是：\(oldValue)")
            }
        }
    }

    class Student: Person {
        override init() {
            super.init()
            super.name = "小黑"
        }
        override var name:String{
            willSet(newName){
                print("子类新值是：\(newName)")
            }
            didSet{
                print("子类旧值是：\(oldValue)")
            }
        }
    }

    let student = Student()
    student.name = "小白"

    log:
    父类新值是：小黑
    父类旧值是：
    子类新值是：小白
    父类新值是：小白
    父类旧值是：小黑
    子类旧值是：小黑
    ```

* * *

### 类型属性

-   类型属性：属性属于某一个类的而不是属于某一个对象实例的。 可以认为所有的对象实例公用这个属性
-   类型属性必须有默认值
-   类型属性使用点语法进行查询和设置
-   使用关键字 `static` 定义类型属性，对于类类型的计算类型属性，可以使用`class`关键字来代替`static`定义类型属性，从而允许子类重写父类的实现

```js
class Person {
    static var name:String  = "person"
    static var age:Int {
        return 15
    }
    class var hobby:String {
        return "hobby"
    }
}


class Student:Person {
    class override var hobby: String {
        return "student"
    }
    
    



}

print(Student.name)
print(Student.hobby)

log:
person
student
```

 [https://juejin.cn/post/6973672678465273870](https://juejin.cn/post/6973672678465273870)
