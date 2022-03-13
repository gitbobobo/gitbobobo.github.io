# Swift高阶函数介绍（map、flatMap、filter、reduce）
`Swift` 提供了如下几个高阶函数： `map`、 `flatMap`、 `filter`、 `reduce`。使用高阶函数进行函数式编程不仅可以简化我们的代码，而且当数据比较大的时候，高阶函数会比传统实现更快，因为它可以并行执行（如运行在多核上）。

#### 一. map 函数

1.  方法介绍

map 方法获取一个闭包表达式作为其唯一参数。 数组中的每一个元素调用一次该闭包函数，并返回该元素所映射的值。 简单说就是数组中每个元素通过某个方法进行转换，最后返回一个新的数组。 2. 使用样例

(1) 下面将 `Int` 类型数组），转换成 `String` 类型的数组, 并且前面拼接上, "Swift"

    let  ins = [2, 3, 4]
    let  strs = ins.map ({  "Swift\($0)"  })
    print (strs) /// ["Swift2", "Swift3", "Swift4"]
    复制代码

(2）对一个数组里面的数据进行平方操作

    let  values = [2, 3, 4]
    let  squares = values.map ({ $0 * $0 })
    print (squares) ///[4, 9, 16]
    复制代码

#### 二、flatMap 函数

1.  方法介绍

`flatMap` 方法同 `map` 方法比较类似，只不过它返回后的数组中不存在 nil（自动把 nil 给剔除掉），同时它会把 `Optional` 解包。 2. 使用样例 (1）下面比较 map 和 flatMap 这两个方法

    let  array = [ "Blue" ,  "red" ,  "Green" ,  "" ]
     
    let  arr1 = array.map { a ->  Int?  in
         let  length = a.count
         guard length > 0  else  {  return  nil  }
         return  length
    }
    print ( "arr1:\(arr1)" )
     
    let  arr2 = array.flatMap { a->  Int?  in
         let  length = a.count
         guard length > 0  else  {  return  nil  }
         return  length
    }
    print ( "arr2:\(arr2)" )

    /// arr1:[Optional(4), Optional(3), Optional(5), nil]
    /// arr2:[4, 3, 5]
    复制代码

    flatMap: 
    注意：4.1之后如果闭包中返回的值是可选的话，就要使用compactMap代替flatMap了，不然的话就会警告。
    @available(swift, deprecated: 4.1, renamed: "compactMap(_:)", message: "Please use compactMap(_:) for the case where closure returns an optional value")
    复制代码

（2） `flatMap` 还能把数组中存有数组的数组（二维数组、N 维数组）一同打开组装成一个新的数组。

    let  array = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    let  arr1 = array.map { $0 }
    let  arr2 = array.flatMap{ $0 }
    print(arr1)
    print(arr2)
    ///[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    ///[1, 2, 3, 4, 5, 6, 7, 8, 9]
    复制代码

#### 三、filter 函数

1.  方法介绍

`filter` 方法用于过滤元素，即筛选出数组元素中满足某种条件的元素。 2，使用样例 （1）筛选出金额大于 `10` 的元素。

    let  prices = [2, 15, 23]
    let  result = prices.filter ({ $0 > 10 })
    print (result) // [15, 23]
    复制代码

#### 四、reduce 函数

1.  方法介绍

`reduce` 方法把数组元素组合计算为一个值，并且会接受一个初始值，这个初始值的类型可以和数组元素类型不同。 （1）将数组中的金额相加，计算总和。

    let  prices = [20,30,40]
    let  sum = prices.reduce(0) { $0 + $1 }
    // 可以简化为 let  sum = prices.reduce(0, +)
    print (sum) ///90
    复制代码

（2）将数组转成字符串，每个元素用顿号（ 、）隔开。

    let  array = [ "Blue" ,  "red" ,  "Green"  ]
    let  str = array.reduce( "" , {
         return  $0 ==  ""  ? $1 : $0 +  "、"  + $1
    })
    print (str)/// Blue、red、Green
     
    //上面等效与
    let  str2 = array.joined(separator:  "、" ) 
    // Blue、red、Green
    复制代码

#### 五、高阶函数的组合使用、链式调用

1\. 组合使用 （1） `flatMap` 配合 `filter` 将多维整型数组里面的偶数筛选出来并且组合成了一个一维数组。

    let  collections = [[2, 7, 9], [4, 1], [5, 1, 3]]
    let  onlyEven = collections.flatMap {
         $0.filter  { $0 % 2 == 0 }
    }
    print (onlyEven) ///[2, 4]
    复制代码

（2） map 配合 reduce 计算二维数组里每个分组的总和。

    let  collections = [[5,2,7],[4,8],[9,1,3]]
    let  sums = collections.map ({ $0.reduce(0, +) })
    print (sums) /// [18, 5, 9]
    复制代码

2，链式组合 （1）将数组中大于 5 的所有数字进行求和操作。

    let  marks = [5, 2, 7, 3, 6, 8]
    let  total = marks.filter {$0 > 5}.reduce(0,+)
    print(total) /// 21
    复制代码

（2）对某一个数组里面的数字进行平方操作然后再筛选出偶数值。

    let  numbers = [2, 9, 5, 4, 8, 7]
    let  evenSquares = numbers.map {$0 * $0}.filter {$0 % 2 == 0}
    print(evenSquares) /// [4, 16, 64]
    复制代码

    End
    复制代码

 [https://juejin.cn/post/6983973263508504583](https://juejin.cn/post/6983973263508504583)
