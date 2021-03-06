[字符串][string]

[string]: string.md
#数组,向量,和切片
- - -
像大多数语言一样,Rust使用链表类型来表述一序列的东西,最基本的就是数组,一个固定大小的都是同种类型的元素的列表,默认情况下,数组是不可变的

    let a = [1, 2, 3]; // a: [i32; 3]
    let mut m = [1, 2, 3]; // mut m: [i32; 3]

有一种简便写法,用来初始化一个数组的元素，每个元素是一样的值,如下面的例子,a的每个元素被初始化为0：

    let a = [0; 20]; // a: [i32; 20]
    
数组类型是**[T;N]** ，当我们涉及到泛型的时候再谈论T这个符号。

使用**a.len()**可以得倒a数组中元素的个数,使用**a.iter()**和一个循环来遍历这个数组, 下面代码按顺序打印每一个成员：

    let a = [1, 2, 3];

    println!("a has {} elements", a.len());
    for e in a.iter() {
        println!("{}", e);
    }
    
可以使用下标访问一个数组的特定元素:
    
    let names = ["Graydon", "Brian", "Niko"]; // names: [&str; 3]

    println!("The second name is: {}", names[1]);

和大多数语言一样下标从0开始,所以第一个名字是**names[0]**,第二个名字是**names[1]**，上面的例子打印**第二个名字:Brain**.
如果你使用了一个越界的下标，将会得到一个错误:array access is bounds-checked at run-time.(运行时数组访问边界检查),在其他系统及编程语言中这种错误访问是导致许多bug原因.

向量是一个动态的或叫做"可增长"的数组,作为标准库Vec<T>的实现(我们稍后谈乱<T>的含义),向量总是在堆上分配数据,向量相对于切片就像String相对于&Str.
你可以使用宏vec!创建向量:

    let v = vec![1, 2, 3]; // v: Vec<i32>

(注意和前面我们使用的println!宏不一样,使用vec!有方括号[],Rust 允许你在不同情况下使用不同的符号，一般按习惯来)

你可以得到向量长度,迭代他们,下标的使用和数组一样,此外,向量是可变并且自动增长

    let mut nums = vec![1, 2, 3]; // mut nums: Vec<i32>

    nums.push(4);

    println!("The length of nums is now {}", nums.len()); // Prints 4

向量有许多有用的方法。

一个切片就是引用(查看)一个数组部分数据，对于需要安全,高效访问数组的部分数据十分有用，并且不需要拷贝。例如,你只想将一个文件的一行数据读进内存.
切片不是凭空创建的，而是来自一个存在的变量,切片有长度，可变或者不可变都可以,使用的方式类似数组:

    let a = [0, 1, 2, 3, 4];
    let middle = &a[1..4]; // a的切片。包含元素1,2,3
    
    for e in middle.iter() {
        println!("{}", e); // Prints 1, 2, 3
    }
    
你可以得到向量的切片,String或者&str的切片,因为他们背后都是基于数组,切片是**&[T]**类型，&[T]我们涉及到泛型再讨论.

目前为止,我们已经学习了Rust基础部分的全部,我们准备好构建我们的猜谜游戏,我们需要知道最重要的一点就是:怎么从键盘得到输入,没有输入如何猜谜！

[标准输入][sinput]

[sinput]:sinput.md



