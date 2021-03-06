#  Swift基础
* macOS 10.13.6, Xcode 9.4.1, swift 4.1.2

## 1. 字符串插值(string interpolation)
* 将常量或变量名放入圆括号中，并在开括号前使用反斜杠将其转义，例如print("a:\(a)")。
* 插值字符串中写在括号中的表达式不能包含非转义双引号和反斜杠，也不能包含回车和换行符。

## 2. 分号
* swift不强制要求在每条语句的结尾处使用分号(;)，当然也可以按照自己的习惯添加分号。
* 在同一行内写多条独立的语句时必须要使用分号，如let cat="xiaohua";print(cat)。

## 3. 整数
* 可以访问不同整数类型的min和max属性来获取对应类型的最大值和最小值。
* 在32位平台上，Int和Int32长度相同, UInt和UInt32长度相同；在64位平台上，Int和Int64长度相同，UInt和UInt64长度相同。

## 4 数值型字面量
* 二进制前缀0b, 八进制前缀0o, 十六进制前缀0x, 十进制没有前缀。
* 指数e(exponent)应用在十进制数中，在十进制浮点数中通过大写或者小写的e来指定,如1.25e2=125，1e-2=0.01。
* 指数p应用在十六进制数中, 在十六进制浮点数中通过大写或小写的p来指定，如0xFp2=60, 0xC.3P0=(12+3/16) * 2^0。
* 数值类字面量可以包括额外的格式来增强可读性。整数和浮点数都可以添加额外的零并且包含下划线，并不会影响字面量(1_00_000.000_1)。

## 5. 元组
* 把多个值组合成一个复合值。元组内的值可以使用任意类型，并不要求是相同类型，如(Int, String), (Int, Int, Int)或(String, Bool)等。
* 可将一个元组的内容分解成单独的常量和变量，若只需要一部分元组值，分解的时候可以把要忽略的部分用下划线标记。
* 可以通过下标来访问元组中的单个元素，下标从零开始。
* 在指定元素类型的情况下加上元素名称let person:(Int, String) = (age: 23, name: "lily")。
  
## 6. 取余
* 在对负数b求余时，b的符号会被忽略。这意味着a%b和a%-b的结果是相同的, 求余符号与a的符号一致。
* 浮点数求余18.5.truncatingRemainder(dividingBy: 3) = 0.5
    
## 7. 基本运算符
* 空合运算符(a??b)将对可选类型a进行空判断，如果a包含一个值就进行解封，否则就返回一个默认值b。前提1是表达式a必须是Optional类型，前提2是默认值b的类型必须要和a存储值的类型保持一致。
* 溢出运算符(&+, &-)，当使用溢出运算符发生溢出时值会循环变化。

## 8. 区间运算符
* 闭区间运算符(a...b)定义一个包含从a到b(包括a和b)的所有值的区间。
* 半闭区间(a..<b)定义一个从a到b(不包括b)的所有值的区间。

## 9. Unicode
* 是一个国际标准，用于文本的编码和表示。
* 每一个字符都可以被解释为一个或多个unicode标量。
* 可以通过字符串的utf8属性来访问对应的UTF-8代码单元集合，通过utf16属性来访问对应的UTF-16代码单元集合，通过unicodeScalars属性访问对应的21位Unicode标量值集合。

## 10. 数组
* 可以使用isEmpty和count属性的值是否为0来判断数组是否为空。
* 在数组后面添加新数据项可使用append方法, 添加数据项数组可以使用加法赋值运算符(+=)。
* 第一项在数组中的索引值是0而不是1。
* 可以利用下标来一次改变一序列数据值，即使新数据和原有数据的数量不一样，如arr[2...4] = ["apple"]将arr数组中索引为2，3，4的三个值变为了一个值，长度减二。
* 不能使用下标语法在数组尾部添加新项，即不允许索引越界。
* 若同时需要每个数据项值和索引值，可使用数组的enumerated函数进行遍历,如for (index, value) in arrs.enumerated() {}。

## 11. 字典
* swift字典使用时需要具体规定可以存储键和值的类型，在某个特定字典中可以存储的键和值必须提前定义清楚。
* 遍历字典时可以通过元组来接收对应的键值对for (key, value) in dic。
* 字典类型时无序集合类型，字典键、值、键值对在遍历的时候会重新排列且顺序是不固定的。

## 12. switch
* swift的switch语句无需写break。
* case可以匹配更多的类型模式，包括区间匹配，元组和特定类型的描述，case语句中匹配的值可以是由case体内部临时的常量或变量决定，也可以由where分句描述更复杂的匹配条件。
* 每一个case分支都必须包含至少一条语句，一个case也可以包含多个模式，用逗号把它们隔开。
* 可以使用元组在同一个switch语句中测试多个值，元组的元素可以是值，也可以是区间。另外，使用下划线来匹配所有可能的值。
* case分支的模式允许将匹配的值绑定到一个临时的常量或变量，这些常量或变量在该case分支里就可以被引用了(值绑定)。
* fallthrough关键字不会检查它下一个将会落入执行case的条件是否匹配而继续执行代码连接到下一个case，不过下一个case中不能有变量否则会报错(慎用)。

## 13. 函数
* 可以使用元组来返回多个值，可对每个返回值取一个别名供返回值调用。
* 可以使用下划线(_ )作为参数的外部参数名，这样可以在调用时不用提供外部参数名。
* 在参数名对应的参数类型后面赋值即可给函数参数设置默认值。
* 当未给带默认值的参数提供外部参数名时，swift会自动提供外部参数名字，此时外部参数名和局部名字是一样的。
* 一个可变参数可以接受一个或多个值，通过在参数变量类型后面加入三个点号(...)来定义可变参数，在函数体内将这个可变参数当做这个类型的一个数组。一个函数至多能有一个可变参数且它必须是最后一个参数。
* 若项一个函数可以修改参数的值并在函数调用结束后修改仍然存在则把这个参数定义为输入输出参数(parm: inout Type)。输入输出参数的传入只能是变量而不能是常量或字面量(这些量是不能被修改的)且需要在前面加&符号表示这个值可以被函数修改，输入输出参数不能有默认值。
* 可以用(Int, Int) -> Int这样的函数类型作为另一个函数的参数类型，这样就可以将函数的部分实现交由函数的调用者。
* 函数类型作为另一个函数的返回类型只需将原来的返回值类型替换为想要的函数类型，如func stepFunc(isUp: Bool) -> (Int) -> Int。

## 14. 闭包
* 是一组预先准备好的代码，在我们需要它的时候就会被调用，可以当作参数来传递。
* 内联闭包表达式中，函数和返回值类型都写在大括号内，而不是大括号外。闭包的函数体部分由关键字in引入，该关键字表示闭包的参数和返回值类型定义已经完成，闭包函数体即将开始。

## 15. 枚举
* 使用enum关键字并把它们整个定义放在一对大括号内，枚举中被定义的值是枚举的成员值(成员)。
* swift的枚举成员在被创建时不会被赋予一个默认的整数值，多个成员值可以出现在同一行上用逗号隔开。
* 原始值可以是字符串，字符或任何整型值或浮点型值，每个原始值在它的枚举声明中必须是唯一的。当整型值被用于原始值，如果其他枚举成员没有值时，它们会自动递增。使用枚举成员的rawValue属性可以访问该枚举成员的原始值。

## 16. 类和结构体
* 使用class和struct关键字来表示类和结构体，并在一对大括号中定义它们的具体内容，定义一个新类或结构体时实际上是有效地定义了一个新的swift类型，建议使用首字母大写驼峰标示UpperCamelClass方式命名。
* 等价于(===)表示两个类类型的常量或变量引用同一个类实例，等于(==)表示两个实例的值相等或相同，判定遵照类设计者定义的评判标准。
* 结构体实例总是通过值传递属于值类型，类实例总是通过引用传递属于引用类型。当值类型的实例被声明为常量的时候，它的所有属性也就成了常量不允许被更改。属于引用类型的类则不一样，它把一个引用类型的实例赋给一个常量后仍然可以修改实例的变量属性。
* 延迟存储属性是指当第一次被调用的时候才会计算其初始值的属性。在属性声明前使用lazy来标示一个延迟存储属性。延迟存储属性必须是变量,因为属性的值在实例构造完成之前可能无法得到。而常量属性在构造过程完成之前必须要有初始值，因此无法声明成延迟属性。
* 计算属性可以定义在类、结构体和枚举中。计算属性不直接存储值，而是提供一个getter来获取值，一个可选的setter来间接设置其它属性或变量的值。
* 声明类的类方法在方法的func关键字之前加上关键字class,声明结构体和枚举的类方法在方法的func关键字前加上关键字static。
* 类不光可以重写方法，还可以重写属性及属性观察器。如果不希望方法、属性或附属脚本等不被重写，只需在声明关键字前加上final即可。也可以通过在关键字class前添加final来将整个类标记为final，这样的类是不可被继承的。

## 17. 附属脚本
* 附属脚本允许通过在实例对象后面的方括号中传入一个或多个索引值来对实例进行访问和赋值。定义附属脚本使用subscript关键字，显示声明一个或多个传入参数和返回类型，可设定为读写或只读。
* 通常是用来访问集合，列表或序列中元素的快捷方式，可依据需求在特定的类或结构体中自由实现附属脚本来提供合适的功能。
* 附属脚本允许任意数量的入参索引且每个入参类型也没有限制，返回值也可是任意类型。附属脚本可以使用变量参数和可变参数，但不允许使用inout参数或给参数设置默认值。
* 一个类或结构体可依据自身需要提供多个附属脚本实现，在定义附属脚本时通过入参个数和类型进行区分，使用附属脚本时会自动匹配合适的附属脚本实现运行(重载)。

