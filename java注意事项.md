# 代码书写注意事项

- 一段代码完成一件事
- 过关斩将，多写if，少嵌套if-else  https://www.bilibili.com/video/BV1fh411y7R8?t=515.6&p=341

# 1、运算符注意事项

只要是运算符进行运算，都要关注自动转型和精度损失，三元运算符也是一样

## 1.1 小数运算

- 注意小数运算时的精度损失和尾数不确定性
- 小数比较时注意不能直接比较，需要使用Math函数进行精度判断

## 1.2 算数运算符

- / 除法运算符：注意运算后的自动转换和赋值的变量类型是否一致，或精度损失

- % 取模运算符： 注意取模的实质公式 a-a/b*b，如果a%b当a是小数时，公式 = a-(int)a/b * b;

  > -10.5%3 = -10.5-（-10）/ 3 *3 = -10.5

- 前++--后++--运算符：注意运算实质逻辑：i=i+1;temp=i;i=temp;注意：在i=i+1;运算时，系统会强制数据类型转换（例如：byte i = 2; i++; 合法，因为i++ 相当于i=i+1;时数据类型提升至int后会强制转换成byte）

## 1.3 赋值运算符

- +=，-=等复合赋值运算符：运算赋值时会进行强制类型转换

# 2、原码、反码、补码

- 全部注意细节

# 3、程序控制结构

## 3.1 分支语句

- case穿透：switch流程图
- switch细节注意；

## 3.2 循环

### for循环

- 循环初始值和变量迭代可以有多条，但要求类型一样，中间用逗号隔开。

### 增强for循环

- for(数组元素数据类型 变量名 ： 数组名){

  }

## 3.3 跳转控制语句

### break

- break细节注意：break用于多重循环时，可以通过标签指定跳出哪层循环。标签的命名随意；lable:

### continue

- cpntinue细节注意：continue用于多重循环时，可以通过标签指定跳过哪层循环。标签的命名随意；lable:

# 4、数组

## 4.1 数组赋值机制

- 数组赋值的注意事项：基本数据类型赋值方式是值拷贝；引用数据类型赋值方式是地址传递。
- 数组扩容和数组拷贝时，将最新的数组赋值给原来的，则原来的数组空间会被垃圾回收。

## 4.2 二维数组

- 二维数组的动态初始化中列数不确定的初始化方式。

# 5、面向对象编程（初级）

## 5.1 类（五大成员：属性、方法、构造器、代码块、内部类）

### 内存结构示意图

1、方法区加载类信息，把类的属性方法加载一下，只会加载一次，之后再创建相同的对象时不会再加载。

2、栈创建一个对象名指向一个地址，没有new时指向空地址。

3、当new对象时，在堆中开辟空间，并把地址赋值给对象名，在方法区的常量池中开辟对象引用数据类型的空间，基本数据类型在堆中的空间中存储。并把对象的属性进行默认初始化。

4、当给对象的属性赋值时，会替代默认初始值。

## 5.2 对象创建流程分析

> 看7.9对象创建流程分析，这里加入了构造器后又进行分析。
>
> https://www.bilibili.com/video/BV1fh411y7R8?t=1000.7&p=245
>
> https://www.bilibili.com/video/BV1fh411y7R8?spm_id_from=333.788.player.switch&vd_source=b627602b9ecf6a3076420c23f46f44c9&p=248 this的隐藏

## 5.3 递归

- 递归必须向退出递推的条件逼近，否则就是无限递归导致栈溢出。

## 5.4 变量

> 全局变量和局部变量的比较在作用域的注意事项中。

### 全局变量（属性）（成员变量）

- 可以不赋值直接使用，因为有默认值

### 局部变量

> 一般是在成员方法中定义的变量、代码块。

- 必须赋值后才能使用，因为没有默认值

## 5.5 方法

### 1、成员方法

### 2、方法重载

> 同一类中，允许多个重名方法存在，但形参列表不一致。
>
> 1、同一类
>
> 2、方法名相统，形参列表不同，返回类型无要求

### 3、可变参数

> java允许将同一个类中多个同名同功能但参数个数不同的方法，封装成一个方法。
>
> 语法：访问修饰符 返回类型 方法名（数据类型... 形参名）；这里的形参在使用时当做数组使用；
>
> 1、同一类
>
> 2、同名、同功能、参数数据类型相同但个数不同（0个或任意多个），封装成一个方法；
>
> 3、实参可以是数组，因为形参本质就是数组；
>
> 4、可变参数可以和普通参数放在一起，但是必须放在末尾，且只能出现一个可变参数；

## 5.6 作用域

- 全局变量：整个所在类，或者通过对象.被其他类调用；
- 局部变量：定义它的代码块；
- 全局变量和局部变量的比较在作用域的注意事项中。

## 5.7 构造方法（构造器）

> - 为了解决在创建对象时就给对象属性赋值；完成新建对象的初始化；
>
> - 构造器可以重载；
> - this可以在构造器中调用其他构造器时必须放在第一条语句

## 5.8 This关键字

> this只能在类定义的方法中使用，不能在类定义的外部使用；

- 应用于构造器中区别属性和参数；
- 可以访问本类的属性、方法、构造器
- this可以在构造器中调用其他构造器时必须放在第一条语句

# 6 面向对象编程（中级）

## 6.1 包

> 应用场景:区分相同名字的类、当类很多时很好的管理类（每个包方功能相识的类）、控制访问范围；

- 打包语法：package 包名；
- 包名：com.公司名.项目名.业务模块名；

> 导入两个包中相同名字的类时，可以用包名区分：
>
> https://www.bilibili.com/video/BV1fh411y7R8?t=544.4&p=275
>
> Dog dog = new Dog(); 
>
> com.xiaoming.Dog dog1 = new com.xiaoming.Dog();

## 6.2 访问修饰符

> 控制方法和属性的访问权限

- public ：对外公开
- protected ：对子类和同一个包公开
- 默认 ：对同一个包公开，但子类不能访问；同一包下的子类可以访问；
- private ：只对类本身可以访问。

## 6.3 面向对象的三大特征

### 封装 encapsulation

- 实现封装的步骤：课件8.6.4https://www.bilibili.com/video/BV1fh411y7R8?t=20.1&p=282

### 继承 extends

> 内存分析：https://www.bilibili.com/video/BV1fh411y7R8?t=34.2&p=294

- Ctrl+H 快捷键可以查看类的继承关系；

- 为什么需要继承？类代码复用性；

  > 解决两个类的属性和方法很多事相同的；小学生，大学生；

- 继承示意图：https://www.bilibili.com/video/BV1fh411y7R8?t=76.9&p=287

- 父类-基类-超类   子类-派生类；

- 继承的注意细节8.8.6课件https://www.bilibili.com/video/BV1fh411y7R8?t=90.5&p=289

- 子类必须调用父类的构造器完成父类的初始化https://www.bilibili.com/video/BV1fh411y7R8?t=17.7&p=290

1、子类调父类构造器

>  创建子类时默认自动调用父类的无参构造器；原理：隐藏了super（）；如果父类没有提供无参构造器，则必须在子类的构造器中用Super去指定调用父类的那个构造器。

#### Super

- 功能

  1、 调用父类构造器

  2、 访问父类属性（私有不可以）、方法（私有不可以）

  3、 子类中有和父类重名的方法和属性时，想调用父类的方法和属性，可以通过Super指定；注意向上找的原则；

- 使用在子类构造器中，用来显式调用父类构造器；

- 放在第一行；

- super和this不能共存在一个构造器中。

### 多态

- 为什么需要多态？https://www.bilibili.com/video/BV1fh411y7R8?t=1085.7&p=306

> 为了解决方法重载太多次的问题；主人喂食

- 多态的具体体现
  - 方法体现多态： 重写和重载体现多态；
  - 对象体现多态：https://www.bilibili.com/video/BV1fh411y7R8?t=113.3&p=308
    - 一个对象的编译类型和运行类型可以不一致；**让父类的引用指向子类的对象**
    - **编译类型在定义对象时就确定了，不能改变**
    - **运行类型是可以变化的**：让父类引用指向新的子类对象；
    - **编译类型看定义时=号的左边，运行类型看=号的右边；**

#### 向上转型

https://www.bilibili.com/video/BV1fh411y7R8?t=80.4&p=310

- 本质：父类引用指向子类对象

- 语法：父类类型 引用名 = new 子类类型（）；

- **特点**：编译类型看左边，运行类型看右边；

  ​			可以调用父类中的所有成员（属性和方法）（**有访问修饰符仍要遵守访问修饰符**）；

  ​			不能调用子类中的特有成员（属性和方法）；

  > 因为在编译阶段能调用哪些成员，是由编译类型决定的；

  ​			**方法调用的最终运行效果看子类的实现；属性的值看编译类型！！！！**

  https://www.bilibili.com/video/BV1fh411y7R8?t=176.4&p=312

  > 编译时看编译类型，方法调用运行时看子类的具体实现，属性还是看编译类型；
  >
  > 编译是一套规则（看明面上的），运行是一套规则；

#### 向下转型

> 将向上转型的对象再转型回来；
>
> 语法：子类类型 引用名 = （子类类型）父类引用；

- 只能强转父类的引用（也就是被向上转型的对象），不能强转父类的对象；
- 要求父类的引用必须和向下转型的对象一致；
- 可以调用子类类型的所有成员（属性和方法）；**即恢复原状**
- 向下转型后原来的父类引用仍可用。只是把地址给他了。

#### instanceOf（判断对象类型是否是XX类型或XX的子类型）

> 结果为boolean值

#### 多态的应用

##### 1、多态数组

> 数组的定义类型为父类类型，里面保存的实际元素类型为子类类型；

##### 2、多态参数

> 方法定义的形参参数为父类类型，实参类型允许为子类类型；

---

### 方法重写/覆盖(Override)

> 子类重写从父类(不限于直接父类)继承的方法；

- 子类和父类的方法名、形参列表完全一致
- 返回类型可以是一样或者是父类返回类型的子类。
- 子类重写方法不能缩小父类方法的访问权限。

## 6.4 Java的动态绑定机制(非常重要)

https://www.bilibili.com/video/BV1fh411y7R8?t=462.2&p=315

个人理解：只要调用方法，不论在哪，都会从运行类型开始找；

1、**方法有动态绑定机制**：当调用对象**方法**的时候，该方法会和该对象的内存地址（运行类型）绑定；

2、**属性没有动态绑定机制**：当调用对象**属性**时，没有动态绑定机制，哪里声明，哪里使用；

## 6.5 Object类的详解

> 学习目的：因为Object是所有类的父类，所以Object拥有的方法，所有类都拥有；

### 1、equals（）方法

- ==和equals的对比：

  - == : 既可以判断基本类型，也可以判断引用类型

    > 判断基本类型即判断值相等
    >
    > 判断引用类型即判断地址相同

  - equals ： 只能判断引用类型。

    > 默认判断地址是否相同，子类往往重写该方法，用于判断内容是否相等；

- 子类往往重写，用于判断值相等；

### 2、hashCode()方法

> 返回该对象的哈希码值

- 课件8.1.2小结
- 子类往往重写

### 3、toString()方法

- 默认返回：全类名+@+哈希值的十六进制
- 子类往往重写，用于返回对象的属性信息。**快捷键：alt+insert选择toString（）；**
- 当直接输出一个对象时（println(对象名)),默认调用toString()方法；

### 4、finalize（）方法

> 当对象被回收时，回收之前系统自动调用该对象的finalize方法。
>
> 垃圾回收是由系统调用的，也可以通过System.gc（）主动触发垃圾回收机制。

- 子类可以重写该方法。**快捷键：alt+insert选择finalize（）**

## 6.6 断点调试

- F7:跳入方法内

- Shif+F8：跳出方法外

- F8: 逐行执行代码

- F9 :执行到下一个断点；

- Alt+Shift+F7：强制进入方法内

  > 适用于需要强制进入方法时和遇到调用方法中嵌套调用方法时使用；因为这种语句使用F7只会进入外层方法，使用Alt+Shift+F7会进入内层方法；

- 注意Idea工具在Debug默认情况下显示的数据是简化后的，有些数据看不到，如果希望看到完整的数据，需要设置：

  > Setting->Build,Execution,Deployment->Debugger->Data Views->Java->取消Enable alternative view for Collections classes勾选

# 7 面向对象编程（高级部分）

 ## 7.1 类变量(静态变量/静态属性)和类方法(静态方法)

#### 类变量

> 为什么要用类变量？https://www.bilibili.com/video/BV1fh411y7R8?t=1.9&p=374
>
> 为了让一个类中的变量让所用该类的对象同时引用共享；

- 使用场景:需要一个变量让所用该类的对象同时引用共享；

- 类变量可以通过类名访问；

- **类变量在类加载的时候就生成了**。

  > 因为在类加载的时候会在堆中映射一个类对象模版，新建的对象都会按照模版创建，并且也可以通过这个模版知晓类的信息；

- 类变量在内存中的分析：https://www.bilibili.com/video/BV1fh411y7R8?t=37.6&p=376

  > 类变量存放位置：与jdk版本有关；
  >
  > jdk1-7存放在方法区的静态域里面；jdk8以后存放在堆里面；

- 使用细节：https://www.bilibili.com/video/BV1fh411y7R8?t=19.3&p=378

#### 类方法

- 使用场景：当方法中不涉及任何和对象相关的成员，则可以将方法设计成静态方法，提升开发效率。

  > 如果我们希望不创建实例，也可以调用某个方法（当做工具来使用），这时把方法做成静态方法非常合适；

- **类方法也是在类加载的时候就生成了**，结构信息存储在方法区。

- 类方法中不允许使用和对象有关的关键字this和super参数；

- 类方法只能访问类变量和类方法

## 7.2 main方法详解

> https://www.bilibili.com/video/BV1fh411y7R8?t=286.3&p=383

- 命令行给main方法传参：java 类名 参数1 参数2 ...
- IDEA给main方法传参：点击锤子旁边的下拉框-> Edit Configurations->Program arguments;

## 7.3 代码块

- 不可显示调用，加载类时或创建对象时隐式调用；

- 语法：[static]{ 代码 };

  > 分为静态代码块和普通代码块；
  >
  > 后面的分号可省略；

- 静态代码块只能调用静态成员，普通代码块可以调用任意成员；

### 代码块好处

- 相当于另外一种形式的构造器（对构造器的补充机制），可以做初始化的操作。
- 使用场景：如果多个构造器中都有重复的语句，可以抽取到代码块中，提高代码的复用性；
- 代码块的调用优先于构造器；其中静态代码块优先于普通代码块；

### 代码块什么时候被调用？

- **静态代码**块随着类的加载而执行；**只会执行一次**；因为类只会加载一次

- 普通代码块随着创建对象而执行；**创建几次就执行几次；**

### 类什么时候被加载？（类只会加载一次）

1、 创建对象实例时（new）;

2、 创建子类对象实例时，父类也会被加载；

3、 使用类的静态成员时（类变量，类方法）时；

### 创建一个对象时，在类的调用顺序是：

https://www.bilibili.com/video/BV1fh411y7R8?t=412.1&p=388

1、先调用静态代码块和静态属性初始化：优先级一样，按照定义顺序调用；

2、再调用普通代码块和普通属性的初始化：优先级一样，按照定义顺序调用；

3、后调用构造器。构造其中隐含了：super（）；和（调用普通代码块和普通属性初始化）的两条语句；

### 创建一个子类对象时（继承关系），他们的静态代码块、静态属性初始化、普通代码块、普通属性初始化、构造方法的调用顺序如下：

https://www.bilibili.com/video/BV1fh411y7R8?t=52.4&p=390



## 7.4 单例设计模式(单个的实例)

> 某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例的方法；

- 价值：比如开发网站，有一个类非常的占用资源，但是我们只需要一个实例就行。这时，单例设计模式就很有用；

### 饿汉式

你不使用，也帮你创建；

- 在类加载时创建对象。
- 不存在线程安全的问题
- 浪费了资源

> 步骤：
>
> 1、 构造器私有化
>
> 2、 类的内部**创建**一个私有的静态的对象
>
> 3、 向外暴漏一个静态的公共方法getInstance；通过方法获取对象（引用）；
>
> 4、 代码实现；

### 懒汉式

你不使用，就不创建；

- 使用时创建对象；
- 存在线程安全的问题
- 不浪费资源

> 为了解决饿汉式的缺点
>
> 1、当类加载时就会初始化静态属性（静态对象），导致不想使用对象时，系统也创建了对象，但是不会被使用，浪费了空间；

---

> 步骤：
>
> 1、 构造器私有化
>
> 2、 类的内部**声明**一个私有的静态的对象；
>
> 3、 **向外暴漏一个静态的公共方法getInstance，在方法中创建对象（先判空）并return出去这个对象；**
>
> 4、 代码实现；

## 7.5 final关键字

> 为什么需要final关键字？
>
> 不希望类被继承、父类方法被子类重写、类的属性的值被修改、某个局部变量被修改；
>
> 只想使用类的一个属性，但不想类被加载；可以同时使用final+staic修饰；

- 可以修饰类、属性、方法和局部变量；

### 注意事项：

https://www.bilibili.com/video/BV1fh411y7R8?t=15.1&p=395

- final修饰的属性叫常量，命名规范XX_XX_XX；

- final修饰的属性在定义时必须赋初值；

  > 赋值形式：
  >
  > 1、定义时赋初值
  >
  > 2、在构造器中赋初值（**若final修饰的属性时静态的，则不可以**）
  >
  > 3、在代码块中赋初值；（**若final修饰的属性时静态的，则只能在静态代码块**）

- 没有必要在final类中再将方法修饰为final方法了；

## 7.6 抽象类 abstract

> 为什么需要抽象类？https://www.bilibili.com/video/BV1fh411y7R8?t=76.9&p=398
>
> 1、当父类的某些方法，需要声明，但是不知道如何实现时，可以将其声明为抽象方法，那么这个类就是抽象类；
>
> 2、解决代码的复用性 https://www.bilibili.com/video/BV1fh411y7R8?t=616.4&p=402

- 只能修饰类和方法；

- 抽象方法：没有实现的方法（由子类实现），即没有方法体(没有大括号)，还要以；号结尾；
- 抽象类：含有抽象方法时，需要把类也声明为抽象的；抽象类也可以没有抽象方法直接声明；
- 一般用来设计开发模式使用较多；

### 注意事项

- 抽象类不可实例化；
- 一个类继承抽象类，必须实现抽象类的所有抽象方法（加个大括号也可以）除非自己也声明为抽象类或父抽象类没有抽象方法；
- 抽象方法不能用private、final、static来修饰；抽象类不能用final修饰；

### 抽象类的使用价值-模版设计模式

>  https://www.bilibili.com/video/BV1fh411y7R8?t=1013.4&p=402
>
>  原理：动态绑定；

## 7.7 接口

> 把一些没有实现的方法封装到一起，某个类要使用时再根据实际情况把这些方法写出来。

- jdl7.0之前，接口中的方法都没有方法体，默认抽象方法；
- **jdk8之后，接口中可以有静态方法，默认方法（使用default关键字修饰），也就是说接口中可以有方法的具体实现。**

### 深入讨论

- 使用接口解决方法命名规范统一；https://www.bilibili.com/video/BV1fh411y7R8?t=403.5&p=405

### 注意事项

- 接口不可实例化
- 抽象类实现接口，可以不用实现接口的方法；
- 一个类同时可以实现多个接口
- 接口中的所有属性都是public static final的；接口中的属性访问形式：接口名.属性名；
- 接口不能继承其他类，只能继承多个接口；
- 接口的修饰符只能是public和默认；

### 接口VS继承类

- 小结：子类继承了父类，就自动拥有父类的功能；如果子类需要拓展功能，可以通过实现接口的方式拓展；实现接口是对java单继承机制的补充；

- 解决的问题不同：

  > 继承：解决代码的复用性和可维护性；
  >
  > 接口：主要是设计，设计各种规范的方法，让其他类去实现；

- 接口在一定程度上实现代码解耦

### 接口体现多态

- 多态数组

- 多态参数

- 多态传递现象

  > https://www.bilibili.com/video/BV1fh411y7R8?t=206.3&p=411
  >
  > 当一个test类实现A接口，则可以向上转型A a = new Test();如果这个接口继承了另一个接口B,则出现多态传递：B b = new Test();

## 7.8 内部类 inner class

> 一个类内部有完整的嵌套了另一个类结构，被嵌套的类称为内部类,嵌套的称为外部类outer class

- 特点：直接访问私有属性，并且可以体现类的包含关系；

- **内部类的分类**

  > 定义在外部类局部位置上（通常在方法内，或代码块内）:局部内部类（有类名）,匿名内部类(无类名)
  >
  > 定义在外部类的成员位置上：成员内部类（没有static修饰）,静态内部类(使用static修饰)

### （局部内部类和匿名内部类共同特点）

- 直接访问外部类的所有成员，包含私有的

- 不能添加访问修饰符，本质也是一个局部变量；

- 作用域仅在定义他的方法和代码块中；

- 局部内部类->访问->外部类的成员:访问方式：直接访问

- 外部类->访问->局部内部类的成员:访问方式：创建对象，再访问

- 外部其他类->不能访问->局部内部类

- 如果外部类和局部内部类的成员重名时，默认遵循就近原则；

  如果想访问外部类的成员，则可以使用（外部类名.this.成员）去访问；

  谁调用内部类所在的方法，谁就是外部类名.this

### 1、 局部内部类

### 2、 匿名（局部）内部类！！！！！！！！

> 为什么需要匿名内部类？https://www.bilibili.com/video/BV1fh411y7R8?t=660.1&p=416
>
> 有些类只想使用一次，后面不再使用；

> 1、本质是类；2、内部类 ；3、没有类名； 4、同时还是一个对象
>
> 语法：new 类或接口(参数列表){类体};

- 运行类型是匿名内部类；
- 既有定义类的定义，也有创建对象的特征；
- **计算机内部逻辑是基于谁，即在内部继承这个类生成匿名内部类；**
- 匿名内部类创建后可以被接收，也可以不接收；可以接收后调用自己的方法，也可以直接.调用；因为本身也是一个对象；https://www.bilibili.com/video/BV1fh411y7R8?t=351.6&p=418

#### 匿名内部类的最佳实践

- 把匿名内部类当做实参直接传递，简洁高效。https://www.bilibili.com/video/BV1fh411y7R8?t=3.7&p=419



### 3、成员内部类

定义位置：定义在外部类的成员位置，并且没有static修饰；

- 直接访问外部类的所有成员，包含私有的；

- 可以添加任意访问修饰符（public、protected、默认、private）,因为它的地位就是一个成员；

- 调用方法：在外部类的成员方法中创建成员内部类对象，再调用方法；

- 成员内部类->访问->外部类的成员:访问方式：直接访问

- 外部类->访问->成员内部类的成员:访问方式：创建对象，再访问

- 外部其他类可以访问成员内部类2种方式https://www.bilibili.com/video/BV1fh411y7R8?t=718.4&p=421

  1、 创建外部类对象；用外部类的对象.new 内部类（）；

  2、创建外部类对象调用在外部类中编写一个方法，返回内部类的对象；

  ​		outer.getInner();

  ​		new Outer().new Inner();

- 如果外部类和局部内部类的成员重名时，默认遵循就近原则；

  如果想访问外部类的成员，则可以使用（外部类名.this.成员）去访问；


### 4、静态内部类

定义位置：定义在外部类的成员位置，有static修饰；

- 直接访问外部类的**所有静态成员**，包含私有的,但不能直接访问非静态成员；

- 可以添加任意访问修饰符（public、protected、默认、private）,因为它的地位就是一个成员；

- 作用域与其他成员一样，为整个类体；

- 静态内部类->访问->外部类的静态成员:访问方式：直接访问所有静态成员

- 外部类->访问->静态内部类的成员:访问方式：创建对象，再访问

- 外部其他类-> 访问->静态内部类两种方式https://www.bilibili.com/video/BV1fh411y7R8?t=123.4&p=423

  1、 new Outer().Inter().var;通过类名调用，前提是满足访问权限；

  2、 编写一个方法（可以是非静态的方法，或者静态方法），返回静态内部类的对象实例；

- 如果外部类和局部内部类的成员重名时，默认遵循就近原则；

  如果想访问外部类的成员，则可以使用（**外部类名.成员**）去访问；





# 枚举enum

> 为什么需要枚举？https://www.bilibili.com/video/BV1fh411y7R8?t=475.1&p=425
>
> - 某一类的对象（具体值）是固定的个数，不会有其他更多；
>
> - 这些对象只读，不修改
>
> 解决方案：枚举

## 枚举介绍

- 是一组常量的集合。（可以理解枚举是一种特殊的类里面只包含一组有限的特定的对象）

- 枚举的两种实现方式

  1、 自定义类实现枚举

  2、 使用enum关键字实现枚举

## 1、自定义类实现枚举（不继承Enum类，不能使用其方法）

- 不需要提供setXX方法，因为枚举对象通常为只读；
- 对枚举对象/属性使用final+static共同修饰，实现底层优化
- 枚举对象名通常使用全部大写常量的命名规范
- 枚举对象根据需要可以有多个属性；

步骤：

1、 构造器私有化,防止对象被创建

2、 去掉setXX相关方法，防止属性被修改;

3、 在类的内部直接创建一组固定的对象，并对外暴露（public final static）

## 2、enum关键字实现枚举（类比自定义）

https://www.bilibili.com/video/BV1fh411y7R8?t=197.2&p=427

1、将class关键字替换为enum关键字

2、 常量（对象）名写成SPRING("春天"，"温暖");写在类的最前面；

3、 多个常量（对象）之间使用，逗号间隔，最后一个分号结尾；

> SPRING（”春天“,"温暖"）,WINTTER("冬天","寒冷");

### 注意事项:

- 使用enum关键字开发一个枚举类时，默认继承Enum类
- 使用enum关键字后，就不能继承其他类了，因为java的单继承机制；
- 传统的 public static final Season2 SPRING = new Season2("春天", "温暖"); 简化成 SPRING("春天", "温暖")， 这里必须知道，它调用的是哪个构造器.
- **如果使用无参构造器 创建 枚举对象，则实参列表和小括号都可以省略**
- println(枚举对象)实质是调用枚举类的父类Enum的ToString()方法返回对象的name；
- 枚举类和普通类一样，可以实现接口，如下形式：enum 类名 implement 接口1，接口2{}；

### Enum类的相关方法

> 因为使用enum关键字时会继承Enum类，所以学习一下相关方法
>
> https://www.bilibili.com/video/BV1fh411y7R8?t=174.6&p=430

- toString()

- name():得到当前枚举常量的名称；建议使用toString（）

- ordinal()：得到当前枚举常量的次序（从零开始编号）

- values()：返回的是一个对象数组；把所有的枚举常量作为数组返回

- valueOf():将字符串转换成枚举对象，**要求字符串必须为已有的常量名，否则报异常**； 

  > Season2.valueOf(”常量名“).var；也就是说获取一个指定的枚举对象

- 枚举对象.compareTo(枚举对象)：比较两个枚举常量，比较的就是位置编号；（按照声明的顺序排列）

## 注解-JDK内置的基本注解类型

> - 注解Annotation用于修饰解释 包、类、方法、属性、构造器、局部变量等数据信息；
>
> - 和注释一样，注解不影响程序逻辑，但注解可以被编译或运行，相当于嵌入在代码中的补充信息；
> - 在javaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在javaEE中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替javaEE旧版中所遗留的繁冗代码和xml配置等

#### 基本的注解介绍

> 使用Annotation时要在前面增加@符号，并把Annotation当成一个修饰符使用。用于修饰它支持的程序符号；

三个基本的Annotation：

- @Override：限定某个方法，是重写父类方法，**该注解只能用于方法**；

  > 不写不检查，写了就检查；价值就是做语法校验；
  >
  > 如果写上注解：编译器则去检查是否真的重写了父类的方法；确实重写了就编译通过，否则编译错误；

  - 什么是@Override，底层是一个@interface的注解类，是jdk5.0之后加入的；
  - 查看@Override的注解源码为@Target（ElementType.METHOD），说明只能修饰方法；
  - @Target是修饰注解的注解，称为元注解；

- @Deprecated：用于表示某个程序元素（类，方法）已过时

  > 注解后表示：不推荐使用，但仍然可以使用

  - 可以修饰方法，类,字段，包，参数等
  - @Target（value = {CONSTRUCTOR,FIELD,LOCAL_VARIABLE,METHOD,PACKAGE,PARAMETER,TYPE}）
  - @Deprecated的作用可以做到新旧版本的兼容和过渡

- @SuppressWarnings:抑制编译器警告

  [SuppressWarning 中的属性介绍以及属性说明](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\资料\分享资料\SuppressWarning 中的属性介绍以及属性说明.txt)

  - 使用语法:@SuppressWarnings({"rawtypes","unchecked".....})中间用字符串填写属性，用逗号隔开

  - 作用范围：和你写的位置有关

    > 写在方法外，作用范围就是这个方法
    >
    > 写在某个语句上，作用范围就是精准抑制某个语句的警告
    >
    > 写在类上，抑制整个类

## 元注解：对注解进行注解

> 用于修饰其他的注解

元注解：本身作用不大，主要知道他是干什么的；

https://www.bilibili.com/video/BV1fh411y7R8?t=146.8&p=436

- Retention：指定注解的可以保留多长时间；三种SOURCE源码、CLASS类，RUNTIME运行时
- Target：指定注解可以在哪些地方使用
- Documented：指定该注解是否会在javadoc中体现
- Inherited：子类会继承父类注解；

# 8 异常 Exception

> 应用场景：保证程序的健壮性https://www.bilibili.com/video/BV1fh411y7R8?t=8.3&p=459

概念：https://www.bilibili.com/video/BV1fh411y7R8?t=197.9&p=445

执行过程中所发生的异常事件分为两大类：

- Error（错误）:
- Exception:Exception分为两大类：运行时异常和编译时异常

## 8.1 异常体系图（！！）

> https://www.bilibili.com/video/BV1fh411y7R8?t=54.0&p=446

## 8.2 常见的异常

### 运行时异常

- 空指针异常
- 数学运算异常
- 数组下标越界异常
- 类型转换异常：.ClassCastException
- 数据格式不正常异常：

### 编译时异常

- SQLException：操作数据库时，查询表可能发生异常
- IOException：操作文件时发生异常
- FileNotFoundException：操作一个不存在的文件异常
- ClassNotFoundException：加载不存在得到类时异常
- EOFException：操作文件到文件末尾发生异常
- IllegalArguementException：参数异常

## 8.3 异常处理（！！）

### 异常处理两种方式

**异常的默认处理方式就是throws**；

- try-catch-finally

  > 程序员在代码中捕获发生的异常，自行处理
  >
  > try:如果出现异常则异常之后的语句不会执行
  >
  > catch:不出现异常时不执行，出现异常才执行
  >
  > finally：无论有没有异常都执行，一般用来关闭try中的资源
  >
  > ### Try-catch-finally注意细节
  >
  > - try代码块有多个异常，可以有多个catch语句，捕获不同的异常，要求父类异常在后，子类异常在前。如果发生异常只会匹配一个catch
  >
  >   > try{
  >   >
  >   > }catch（NullPointerException e）{
  >   >
  >   > }ctach（Exception e）{
  >   >
  >   > }
  >
  > - 也可以只写try-finally;应用场景：执行一段代码，无论是否发生异常，都必须执行某个业务逻辑
  >
  >   > try{
  >   >
  >   > }
  >   >
  >   > finally{
  >   >
  >   > }
  >
  > - 在try-catch-finally结构中的执行顺序细节：https://www.bilibili.com/video/BV1fh411y7R8?t=258.3&p=451

- throws（默认）

  > 将发生的异常抛出，交给调用者（方法）来处理，最顶级的处理者就是JVM
  >
  > 将异常往上级抛出
  >
  > ### throws注意细节
  >
  > - 当一个方法可能出现异常但不知如何处理时可以抛出异常；
  > - 在方法声明中可以声明抛出异常的列表（可以抛出多个异常），throws后面的异常类型可以是方法中产生的异常类型，也可以是它的父类

- 两种方式的处理机制

  > https://www.bilibili.com/video/BV1fh411y7R8?t=70.3&p=449

## 8.4 注意细节

- 对于编译异常，程序中必须处理；try-catch或throws

- 对于运行异常，程序中如果没有处理，默认就是throws方式处理
- 子类重写父类的方法时，对抛出异常的规定：子类重写的方法，所抛出的异常要么和父类抛出的异常一致，要么为父类抛出的异常的类型的子类型；

## 8.5 自定义异常

当程序中出现了某些“错误”，但该错误信息没有在Throwable子类中描述处理，这个时候可以自己设计异常类，用于描述该错误信息；

- 步骤：

  > 1、 定义类：自定义异常类名继承Exception或RuntimeException；创建构造器（String message）
  >
  > 2、 如果继承Exception属于编译异常
  >
  > 3、 如果继承RuntimeException属于运行异常

- **一般情况下，我们的自定义异常继承RuntimeException运行时异常，因为可以使用默认的异常处理机制**；

## 8.6 throw和throws的对比

- throws是一种异常处理方式，位置在方法声明处，后面跟异常类型；
- throw是手动生成异常对象的关键字，位置在方法体中，后面跟异常对象；

# 9 常用类

> - 实现了Serializable接口：对象可以串行化，进行网络传输，可以保存到文件
> - 实现了Comparable接口:对象可以相互比较大小

## 9.1 包装类（Wrapper）

> 1、针对八种基本数据类型相应的引用类型-包装类
>
> 2、有了类的特点就可以调用类的方法
>
> ![包装类](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\包装类.png)

- 包装类和基本数据的转换（装箱和拆箱JDK5之后都是自动的）

  > https://www.bilibili.com/video/BV1fh411y7R8?t=346.7&p=461

- 包装类型和String类型的相互转换

  > https://www.bilibili.com/video/BV1fh411y7R8?t=258.2&p=463
  >
  > 包装类转字符串
  >
  > Integer i = 100;//自动装箱
  >
  > String s = i+"";//方式一
  >
  > String s = i.toString();//方式二
  >
  > String s = String.valueOf(i);//方式三
  >
  > 字符串转包装类
  >
  > String s = "12345";
  >
  > Integer i = Integer.paeseInt(s);//方式一
  >
  > Integer i = new Integer(s);//方式二

- Integer类和Character类的常用方法

  ![Integer类和Character类的常用方法](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\Integer类和Character类的常用方法.png)

## 9.2 String!

String类是保存字符串常量的。每次更新都需要重新开辟空间，效率较低，因此java设计者还提供StringBuilder和StringBuffer来增强String的功能，提高效率；https://www.bilibili.com/video/BV1fh411y7R8?t=93.6&p=472

- String类的理解和创建对象

  > 理解：
  >
  > - 字符串的字符使用Unicode编码，字母和汉字都是两个字节
  >
  > - String是一个final类，不能被继承
  > - **字符串用于字符存储，底层是一个private fina char value[]**
  > - 注意：因为value是一个final类型，所以数组名value指向的地址不能修改
  >
  > 常用的构造器：
  >
  > - new String（）；
  > - new String (String original);
  > - new String(char[] a);
  > - new String (char[] a,int startIndex,int count);

- 两种创建String对象的区别

  > 方式一：String s = "hsp";
  >
  > > 先从常量池查看是否有“hsp”数据空间，有则指向，没有则重新创建再指向地址
  >
  > 方式二：String s = new String("hsp");
  >
  > > 现在堆中创建空间，里面维护了value属性，指向常量池的hsp空间，有则指向，没有则重新创建再指向地址；
  >
  > 内存分析：https://www.bilibili.com/video/BV1fh411y7R8?t=219.8&p=467

- Intern（）方法

  > 如果池中已包含一个等于此String对象存储的字符串则返回字符串内容的地址也就是内部value指向的地址；
  >
  > 否则此String对象将添加到常量池中，并返回此String对象的引用

- 字符串的特性

  >- String是一个final类，代表不可变的字符序列
  >
  >- 字符串是不可变的，一个字符串对象一旦被分配，其内容是不可变的（变得是指向字符串常量的地址）；
  >
  >- String a = "Hello";
  >
  > String b = "abc";
  >
  > String c = a+b;//此时c指向堆中对象value数组，Value指向常量池
  >
  > https://www.bilibili.com/video/BV1fh411y7R8?t=980.9&p=470
  >
  > String d = "abc"+"def";//这里直接指向常量池中abcdef

### String类的常见方法

- equals():区分大小写，判断内容是否相等

- equalslgnoreCase()：忽略大小写的判断内容是否相等

- length()：获取字符个数，字符串长度

- indexOf()：获取字符在字符串中第一次出现的索引（返回第一个字母出现的位置），索引从0开始，找不到返回-1

- lastIndexOf()：获取字符在字符串中最后一次出现的索引，索引从0开始，找不到返回-1

- substring(int start,int end)：截取指定范围的子串,end省略则截取到末尾

- trim()：去前后空格

- charAt()：获取某索引处的字符，注意不能使用Str[index]这种方式；

- toUpperCase()：转大写

- toLowerCase()：转小写

- replace(目标字符串，替换字符串)：返回一个替换字符串中的字符的新数组，对原数组没有影响

- split()：分割字符串,返回分割后的字符数组；如按照转义字符进行分割需要注意

  > String [] s = str.split();

- compareTo()：比较两个字符串的大小，返回正数：后者大，返回负数：前者大；返回0：相等

  > s1.compareTo(s2);
  >
  > 实质：长度相同：返回的是每一个字符对应的ASCLL码值的差值，前面-后面；
  >
  > ​			长度不同：返回的是长度长的位数减去长度短的位数，前面-后面；

- toCharArray()：转换成字符数组

- format()：格式化字符串；%s字符串，%c字符，%d整型,%.2f浮点型

  > 类似于C语言中的占位符；
  >
  > String s = String.format("姓名：%s 年龄 %d  成绩 %.2f  性别%c "，name,age,score,gender);
  >
  > 也可以这样写:
  >
  > String formatStr = "姓名：%s 年龄 %d  成绩 %.2f  性别%c ";
  >
  > String info = String.format(fomatStr,name,age,score,gender);

## 9.3 StringBuffer!

> 对String的一种增强，**代表可变的字符序列，可以对字符串内容进行增删**；
>
> - 很多方法与String相同，但StringBuffer是可变长度的；
> - StringBuffer是一个容器
> - StringBuffer是一个final类，不能被继承；

- StringBuffer的父类是AbstractStringBuilder()
- 内部是一个char[] value;不是final类型，所以引出存放在堆中

### StringBuffer常用方法

- 增加appnd();

  > str.append("");

- 删除delete(start,end)

- 修改replace(start,end,string):替换[start，end)

- 查找indexOf();

- 插入insert(idnex,string);

- 获取长度length()

### String VS StringBuffer

- String保存的是字符串常量，里面的值不能更改，每次String类的更新实际上就是更改地址，效率较低；
- StringBuffer保存的字符串变量，里面的值可以更改，每次StringBuffer的更新实际上可以更新内容，不用更新地址（除非装满了会进行扩容数组替换），效率较高；

### 构造器（决定初始容量）

- StringBuffer();构造一个其中不带字符串的字符串缓冲区，其初始容量为16个字符。
- StringBuffer（CharSequence seq）：构造一个和指定字符串大小一致的字符串缓冲区，并将指定的CharSequece字符放入字符数组中；
- StringBuffer（int capacity）:构造一个不带字符，但具有指定初始容量的字符串缓冲区。即对char[]大小进行指定
- StringBuffer(String s)：构造一个字符串缓冲区大小为指定的字符串长度+16，并将其内容初始化为指定的字符串内容；

### String和StringBuffer相互转换

- String转StringBuffer

  >方式一：
  >
  >String str = "hello tom";
  >
  >StringBuffer stringBuffer = new StringBuffer(str);//这里返回一个StringBuffer对象，对str没有影响；
  >
  >方式二：使用append方法
  >
  >String str = "hello tom";
  >
  >StringBuffer stringBuffer  = new StringBuffer()；
  >
  >StringBuffer append = stringBuffer.append（str）；

- StringBuffer转String

  > StringBuffer stringBuffer  = new StringBuffer("韩顺平教育")；
  >
  > 方式一：用toString()方法
  >
  > String s = stringBuffer.toString();
  >
  > 方式二：用构造器
  >
  > String s = new String(stringBuffer);

### 课堂练习

- append（null）；仍然可以存放

## 9.4 StringBuilder!

> - 一个可变的字符序列。此类提供一个与StringBuffer兼容的API，但不保证同步（**StringBuilder不是线程安全的**）。该类被设计用作StringBuffer的一个简易替换，用在字符串缓冲区被单个线程使用的时候。如果可能是单线程的，建议优先使用该类，因为在大多数实现中，他比StringBuffer要快；
> - 在StringBuilder上的主要操作就是append、insert方法，可重载这些方法以接收任意类型的数据；

- 常用方法和StringBuffer一样
- StringBuilder是final类，不能被继承；
- StringBuilder对象字符序列仍然是存放在其父类的char[] value；因此存放在堆中；
- StringBuilder没有做互斥处理，没有synchronuzed关键字，不是线程安全的；

### String、StringBuffer、StringBuilder的比较

>  https://www.bilibili.com/video/BV1fh411y7R8?t=103.7&p=480

- StringBuffer和StringBuilder非常类似，均代表可变的字符序列，而且方法一样
- String：不可变字符序列，效率低，但是复用率高；
- StringBuffer：可变字符序列、效率较高（增删）、线程安全
- StringBuilder：可变字符序列、效率最高、线程不安全；

### String、StringBuffer、StringBuilder的使用选择

![String、StringBuffer、StringBuilder选择](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\String、StringBuffer、StringBuilder选择.png)

## 9.5 Math类

> 包含用于执行基本数学运算的方法，比如初等指数、对数、平方根和三角函数

### 常用方法（均为静态方法）

- Math.pow(2,4):2的4次方

- Math.abs（-9）:取绝对值

- Math.ceil(-3.0001):向上取整

- Math.floor(-4.999):向下取整

- Math.round(5.12)：四舍五入

- Math..sqrt(9.0):求开方

- Math.random():返回一个[0-1)的随机数

  > 取[a,b]的随机整数值：https://www.bilibili.com/video/BV1fh411y7R8?t=969.9&p=481

- Math.max(a,b)：求两个数的最大值

- Math.min（a,b）：求两个数的最小值



## 9.6 Arrays类

Arrays里面包含了一系列的静态方法，用于管理或操作数组（比如排序和搜索）

- Arrays.toString（数组名）返回数组的字符串形式；

- Arrays.sort（数组名，[定制排序]）排序：自然排序和定制排序

  > 底层解析：https://www.bilibili.com/video/BV1fh411y7R8?t=1103.4&p=482

- Arrays.binarySearch（数组名，查找的值）：通过二分搜索法进行查找，数组必须是有序地；

- Arrays.copyOf（数组名arr，个数n）：数组元素的复制；从arr数组拷贝n个元素到新数组中；

  > 如果拷贝的长度超过arr元素个数；则在后面补上null；

- Arrays.fill（数组名arr,数据类型m）：数组元素的填充；使用数据类型m去填充数组（用m替换所有元素）；

- Arrays.equals（）：比较两个数组元素内容是否完全一致

- Arrays.asList（）：将一组值，转换成list集合

## 9.7 System类

#### 1、常见方法

- exit（状态值）：退出当前程序；

  > 状态值为0：表示正常状态退出

- arraycopy（src,srcPos,dest,destPos,length）：复制数组元素，比较适合底层调用，一般使用Arrays.copyOf完成复制数组；

  > src:源数组（数据来源）
  >
  > srcPos:从源数组的那一个索引开始拷贝
  >
  > dest:拷贝到目标数组
  >
  > destPos：拷贝到目标数组的哪一个索引位置
  >
  > length:从源数组拷贝多少长度到目标数组

- currentTimeMilens（）：返回当前时间距离1970-1-1的毫秒数

  > ```
  > System.out.println（System.currentTimeMilens()）
  > ```

- gc()：运行垃圾回收机制System.gc();

## 9.8 BigInteger和BigDecimal类

> - 应用场景：https://www.bilibili.com/video/BV1fh411y7R8?t=243.8&p=487
>
> - 用于保存高精度的数据
>
>   BigInteger适合保存比较大的整型
>
>   BigDecimal适合保存精度更高的浮点型（小数）
>
> - 使用这些类时进行运算时，需要使用自带的方法进行运算

#### BigInteger和BigDecimal

- 注意事项：赋值方式

  > ```
  > BigInteger bigInteger = new BigInteger("25555555555555555555555");
  > 用字符串赋值，底层会转为bigInteger
  > 
  > BigDecimal bigDecimal= new BigDecimal("2555.5555555555555555555");
  > 用字符串赋值，底层会转为BigDecimal
  > ```

- 加减乘除方法

> - add（）加法
>
> - subtract（）减法
>
> - multiply（）乘法
>
> - divide()除法
>
>   > 在BigDecimal类进行除法时可能会抛出异常（除不尽）;
>   >
>   > 解决办法：在divide()后面指定一个精度；divide（bigDecimal，BigDecimal.Round_CEILING）
>   >
>   > BigDecimal.Round_CEILING:这个精度就是保留和你赋值精度一样的精度；

## Date、Calender、LocalDate..（会查即可）

#### 第一代日期类Date

1、 Date：精确到毫秒，代表特定的瞬间

2、SimpleDateFormat：格式和解析日期的具体类.它允许进行格式化。（日期转文本）、解析（文本转日期）和规范化。

- 注意事项

  > 不要引错包，因为包含Date的有两个包
  >
  > java.util.Date正确
  >
  > java.sql.Date错误

- Date：获取系统时间,返回的是国外时间格式通常需要SimpleDateFormat格式转换

  > Date date = new Date();
  >
  > 用法一：Date（）；
  >
  > 用法二：Date（毫秒数）：也可以传入一个毫秒数，转成时间
  >
  > 用法三：可以把一个时间格式的字符串转成一个Date
  >
  > **必须使用的sdf格式和你字符串的时间格式一样，否则会抛出转换异常**
  >
  > ```
  > String s = "1996年01月01日 10:20:30 星期一";
  > SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 hh:mm:ss E");
  > Date pase = sdf.parse(s);
  > System.out.println(sdf.format(pase));
  > ```

- SimpleDateFormat（）：格式不能乱写

  > SimpleDateFormat simpleDateFormat = new SimpleDateFormat（“yyyy年MM月dd日 hh:mm:ss E”）；
  >
  > String format =sdf.format(d1);

![Date数据格式](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\Date数据格式.png)

#### 第二代日期类Calendar

- 主要是Calendar类（日历）

- Calendar类是一个抽象类，并且构造器是private

- 可以通过getInstance（）来获取实例

- 提供大量的方法和字段提供给程序员

  ```
  Calendar c =Calendar.getInstance();
  System.out.println("c="+c); 
  这里将现在的时间分割开，将信息存放在它的字段中；
  ```

- 使用对象获取对应的字段获取时间信息；

- Calendar没有专门的格式化方法，需要程序员自己来组合显示

![Calendar](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\Calendar.png)

- Calendar中的小时默认是12进制的，改成24进制-> Calendar.HOUR_OF_DAY

  > c.get(Calender.Hour_OF_DAY)

#### 第三代日期类LocalDateTime

#### 1、LocalDateTime类

> JDK1.0包含一个java.util.Date类，但是它的大多数方法已经在JDK1.1引入Calendar类之后被弃用了，而Calendar也存在问题：
>
> - 可变性：向日期和时间这样的类应该是不可变的
> - 偏移性：Date中的年份是从1900开始的，而月份都从0开始
> - 格式化：格式化只对Date有用，Calendar则不行
> - 此外线程不安全，不能处理润秒（每隔2天，多出1s）

- LocalDate（日期）类：只包含年月日，不含时分秒

- LocalTime（时间）类：包括时分秒

- LocalDateTime（日期时间）类:包含年月日时分秒

  > 提供方法可以对日期进行运算，加减

  - now()：返回当前日期时间的对象
  - 各种get方法获取年月日时分秒

  

#### 2、DateTimeFormatter格式日期类

> 对LocalDateTime进行格式化

```
LocalDateTime dt = LocalDateTime.now();
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy年MM月dd日 HH小时mm分钟ss秒");
String strDate = dtf.format(dt);
```

#### 3、  Instant类(时间戳)

> 类似于Date
>
> 提供一系列和Date类转换的方式
>
> Instant->Date
>
> Date date = Date.from(instant);
>
> Date->Instant
>
> Instant instant = date.toInstant();

#### 第三代日期类更多类和方法

- MonthDay类：检查重复事件
- 是否是闰年
- 增加日期的某个部分
- 使用plus方法测试增加时间的某个部分
- 使用minus方法测试查看一年前和一年后的日期

# 10 集合

> 难点：
>
> - 了解底层机制
> - 看源代码
> - 各个集合的应用场景：什么情况下选用什么集合

> 为什么需要集合？
>
> - 一开始保存数据使用数组，但是有不足的地方；
>
> - 数组的不足：
>
>   > - 长度开始时必须指定，而且一旦制定不能更改
>   > - 保存的必须是同一类型的元素
>   > - 使用数组进行操作元素比较麻烦
>
> - 集合解决不足
>
>   > - 动态保存任意多的对象，使用方便
>   > - 提供一系列方便的操作对象的方法add\remove\set\get
>   > - 使用集合添加，删除新元素更方便
>   > - 保存的数据类型也可以不一致了

## 10.1 集合框架体系！

> - 集合主要是分为两组；单列集合和双列集合
>
>   > - 单列集合：主要就是存放单个的数据；
>   >
>   > - 双列集合：主要是存放键值对形式的
>
> - Collection接口有两个重要的子接口List、Set，他们的实现子类都是单列集合
>
> - Map接口的实现子类是双列集合，存放的是Key-Value

![集合体系图](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\集合体系图.png)

## 10.2 Collection接口（单列）

> 这个里面装的都是对象，有个自动装箱的过程，而不是简单的数据。String类型则是常量

- Collection接口实现类的特点（继承了Iterable）

  > - Collection实现子类可以存放多个元素，每个对象可以是Object；（也就是任意对象）
  > - 有些Collection的实现类可以存放**重复**的元素，有些不可以；
  > - 有些Collection的实现类，有些是有序的（List），有些是不是有序的（Set）；
  > - Collection接口没有直接的实现子类，是通过它的子接口Set、List来实现的；

- Collection接口的常用方法

  > - add（）：添加单个元素
  >
  >   > 添加成功返回true，失败返回false
  >
  > - remove（）：删除指定元素
  >
  > - contains（）：查找元素是否存在
  >
  > - size（）：获取元素个数
  >
  > - isEmpty（）：判断是否为空
  >
  > - clear（）：清空
  >
  > - addAll（）：添加多个元素
  >
  > - removeAll（）：删除多个元素
  >
  > - containsAll（）：查找多个元素是否都存在
  >
  >   > 这些批量操作，只要是实现了Collection接口的类都可以当做参数传进来；

  ---

  > - 遍历元素的方法
  >
  >   - 方式一、使用Iterator（迭代器）（由父接口Iterable实现得来的）
  >
  >     > 快捷键itit
  >
  >     > > Iterator对象称为迭代器，主要用于遍历Collection集合中的元素；
  >     > >
  >     > > 所有实现了Collection接口的集合都有一个iterator（）方法，用以返回一个实现Iterator接口的对象，即可以返回一个迭代器
  >     > >
  >     > > Iterator的结构：https://www.bilibili.com/video/BV1fh411y7R8?t=358.9&p=502
  >     > >
  >     > > > 使用时先用hasNext（）检查判断一下，再用next（）方法下移和返回元素（Object类型）
  >     > > >
  >     > > > 如果不检查且下一个元素无效时，会报**NoSuchElementException**异常
  >     > > >
  >     > > > 如果希望再次遍历，从新使用iterator（）获取Iterator对象即可
  >     > >
  >     > > Iterator仅用于遍历集合，Iterator本身不存放对象
  >
  >   - 方式二、增强for循环
  >
  >     > 增强for循环，可以代替Iterator迭代器，特点是：增强for就是简化版的Iterator，本质一样底层仍然是Iterator迭代器，只能用于遍历集合或数组
  >     >
  >     > 基本语法：
  >     >
  >     > for(元素类型 元素名 ：集合名或数组名){
  >     >
  >     > 访问元素
  >     >
  >     > }

### List子接口

> List接口介绍
>
> - List集合中的元素有序（即添加顺序和取出顺序一致），且可以重复；
> - List集合中的每个元素都有其对应的顺序索引，即支持索引
> - List容器中的元素都对应着一个整型的序号记载其在容器中的位置，可以根据序号存取容器中的元素
> - List接口的实现类有很多，最常用的有ArrayList、LinkedList、Vector
> - 可以放入所有元素，null也能放入，并且多个

- List接口的常用方法

  > - void add(int index, Object ele):在index位置插入ele元素
  >
  >   > 没有返回值
  >
  > - boolean addAll（int index, Collection eles）：从index位置开始将eles中的所有元素添加进来
  >
  > - Object get (int index):获取指定index位置的元素
  >
  > - int indexOf(Object obj):返回obj在集合中首次出现的位置
  >
  > - int lastIndex(Object obj):返回obj在集合中最后出现的位置
  >
  > - Object remove（int index）:移除指定index位置的元素，并返回此元素
  >
  > - Object set（int index,Object ele）:设置指定index位置的元素为ele，相当于是替换
  >
  > - List subList(int fromIndex,int toIndex):返回从fromIndex到toIndex位置的子集合；

- 多一种遍历方法----普通for循环遍历

  > for(int i=0;i<list.size();i++){
  > Object obj = list.get(i);
  > System.out.println(obj);
  > }

#### - ArrayList类（数组形式的List）

- 注意事项：

  > - ArrayList是由数组来实现数据存储的；
  > - ArrayList基本等同于Vector，除了ArrayList是线程不安全的（执行效率高），在多线程情况下，不建议使用ArrayList，使用Vector；

##### ArrayList底层结构和源码分析

- ArrayList中维护了一个Object类型的数组transient Object[] elementData；

  > transient表示瞬间、短暂的；当一个属性倍transient修饰时，表示该属性不会被序列化；

- **无参构造器扩容机制：**当创建对象时，如果使用的是无参构造器，则初始elementData容量为0（JDK7是10）；第一次添加，需要扩容的话。则扩容elementData为10；如果需要再次扩容的话，则扩容elementData为1.5倍；

  > 视频：https://www.bilibili.com/video/BV1fh411y7R8?t=329.9&p=511
  >
  > 每次添加都要判断是否需要扩容

- **有参构造器扩容机制**：如果使用的是指定容量capacity的构造器则初始elementData容量为capacity；如果需要扩容，则直接扩容elementData的1.5倍

  > 视频：https://www.bilibili.com/video/BV1fh411y7R8?t=25.0&p=512
  >
  > 

#### - Vector类

##### 	Vector底层结构和源码分析

- Vector底层也是一个对象数组，protected Object[] elementData；
- Vector是线程同步的即线程安全，Vector类的操作方法带有synchrinized修饰
- 在开发中，需要线程同步安全时，考虑使用Vector

**Vector和ArrayList的比较：**

![ArrayList和Vector比较](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\ArrayList和Vector比较.png)

#### - LinkedList类（链表形式的List）

- 说明：

  > - LinkedList底层实现了双向链表和双端队列特点
  > - 线程不安全，没有实现同步

- LinkedList的底层操作机制

  > - LinkedList底层维护了一个双向链表
  > - LinkedList中维护了两个属性first和last分别指向首节点和尾结点
  > - 每个节点（Node）对象，里面又维护prev、next、item三个属性，其中通过prev指向前一个、next指向后一个节点，最终实现双向链表
  > - 所以LinkedList的元素的添加和删除通过双向链表效率较高

- LinkedList底层结构

  > - LinkedList的增删改查案例CRUD
  >
  >   > - LinkedList.remove（）默认删除的是第一个结点

- Vector和ArrayList的比较：

  ![ArrayList和LinkedList比较](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\ArrayList和LinkedList比较.png)

### Set子接口

> Set接口介绍
>
> - Set集合中的元素无序（添加和取出的顺序不一致），没有索引
>
>   > 虽然添加的顺序和取出的顺序不一致，但不是**取出的顺序是固定的**；
>
> - 不允许重复元素，所以最多只有一个null；
>
> - List接口的实现类有很多，最常用的有HashSet、TreeSet

- **其实底层也是双列，key存放的是对象，Value存放的是一个Object用来占位填充，没有用；**

- Set接口常用方法

  > - 和Collection接口的方法保持一致

- Set接口的遍历方式

  > - 和Collection接口的保持一致，迭代器和增强for循环

#### - HashSet类

> HashSet介绍
>
> - HashSet底层实际上是HashMap，因为底层构造器走的是HashMap
> - HashSet不保证元素是有序的，取决于hash后，再确定索引的结果

- HashSet不能加入同一个对象即元素不能重复

  视频详解https://www.bilibili.com/video/BV1fh411y7R8?t=30.1&p=521

  > 底层是通过hash（）+equals（）方法共同限制

  - HashSet添加一个元素的逻辑步骤和底层分析（putVal（）方法）

  > - HashSet底层是HashMap
  > - 添加一个元素时，先得到hash值，转换成索引值
  > - 找到存储数组table，看这个索引位置是否已经存放元素
  > - 如果没有，直接加入；如果有，调用**equals方法（这里的equals方法程序员自己重写，可以自定义认为相同的标准）**比较，如果相同，就放弃添加(也不是放弃添加，而是进行替换，只不过他们的Key相同看不出来，而Value默认都是默认的Object对象用来占位)，如果不同则添加到最后

- HashSet底层HashMap的数组**扩容机制**和**转成红黑树机制**

  > https://www.bilibili.com/video/BV1fh411y7R8?t=158.5&p=524
  >
  > - HashSet底层是HashMap，第一次添加时，table数组扩容到16，临界值threshold= 16乘以加载因子（loadFactor）是0.75 = 12；
  >
  > - 如果table数组的使用达到临界值12，就会扩容两倍到16*2=32，新的临界值就是32乘以0.75 = 24，以此类推；
  >
  >   > 这里的临界值不是代表加入数组的个数，而是整个数组加链表个数的总和
  >
  > - 在java8中，如果一天链表的元素个数到达TREEIFY_THRESHOLD（默认是8），**并且**table的大小（默认16）>=MIN_TREEIFY_CAPACITY（默认64）。就会进行树化（红黑树），否则仍然采用数组扩容机制
  >
  >   > 若链表的元素个数已经是8个了，而数组的大小还没有到64，仍会进行数组扩容

#### - LinkedHashSet类（元素有序）

> LinekHashSet说明
>
> - **LinkedHashSet是HashSet的子类**
>
> - LinkedHashSet底层是一个**LinkedHashMap**，底层维护了一个**数组+双向链表**
>
>   > HashMap维护的是：数组+单向链表
>   >
>   > LinkedHashMap是HashMap的子类；
>
> - LinkedHashSet根据元素的hashCode值来决定元素的存储位置，同时使用链表维护元素的次序（图），这使得元素看起来是以插入顺序保存的；
>
> - LinkedHashSet不允许添加重复元素；
>
> ![LinkedHashSet](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\LinkedHashSet.png)

#### - TreeSet类

> - 实现了Set接口
> - 可以排序
> - 

## 10.3 Map接口（双列）

> JDK8.0中Map接口特点
>
> - 应用场景比Set广泛
>
> - 用于保存具有映射关系的数据：Key-Value
>
> - Map中的Key和Value可以是任何引用数据类型，会封装到HashMap$Node对象中；
>
> - Map中的Key不允许重复（在HashSet中已经讲过原理）,Value可以重复
>
>   > **这里如果Key重复了，并不是放不进去，而是替换**
>
> - Map中的Key可以为null，Value也可以为null，注意Key为null，只能有一个
>
> - 常用String类作为Map的Key
>
> - Key-Value之间存在单向一对一关系，即通过Key总能找到唯一的Value
>
> - 元素无序
>
> - Map接口最常用的实现类：HashMap、Hashtable、Properties
>
> - HashMap是Map接口使用频率最高的实现类；

#### Map中存放数据的两个地方：

- Map存放数据的key-value是存放在一个Node中，因为Node实现了Entry接口

> > https://www.bilibili.com/video/BV1fh411y7R8?t=1773.9&p=532
> >
> > 存在两个存放数据的地方：
> >
> > **table中的Node（实际存储）**
> >
> > **EntrySet中的Node（相当于一个索引集合，方便遍历）**
> >
> > 数据确实是存放在Node节点里，底层为了方便程序员遍历，会创建一个EntrySet集合（使用的数据类型是Set集合），该集合定义存放的元素数据类型是Map.Entry接口类型，但是实际上存放的是Node类类型（因为Node类实现了Map.Entry接口，这里存在一个向上转型的操作），而这里的Map.Entry接口对象就是table中的Node向上转型存过来的，也就是说他们虽然对象地址不一样（因为向上转型了是不同对象）但是内部属性指向的地址一样，那key-value也就一样；
> >
> > > 为什么会方便程序员遍历？因为EntrySet提供了两个非常重要的方法（getKey()和getValue（）方法，比较容易获取属性值）
> > >
> > > EntrySet提供的两个方法：由存储的Map.Entry数据类型的变量调用
> > >
> > > - getKey()：获取Key值（通过Entry接口类型的对象调用）
> > > - getValue（）：获取Value值（通过Entry接口类型的对象调用）

![Map底层存放数据的结构](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\Map底层存放数据的结构.png)

- Map接口常用方法

  > - put（Object Key,Object  Value）:添加
  > - remove（Object  key）：根据key删除映射关系
  > - get（Object key）：根据key获取Value
  > - size（）：返回元素个数
  > - isEnpty（）：判断个数是否为0；
  > - clear（）：清空
  > - containsKey（Object Key）：查找键是否存在

  ---

  > - KeySet（）：只取出Set集合中全部的Key的值（直接通过Map子类调用）
  >
  >   > 因为在EntrySet集合内部有一个Set集合把Key封装进去，用于只存放Key的值
  >
  > - Values（）：只取出Collection集合中全部的Value的值（直接通过Map子类调用）
  >
  >   > 因为在EntrySet集合内部有一个Collection集合把Value封装进去，用于只存放Value的值

  ---

  > Map接口遍历方法（比List和Set复杂一点，但是基本原理是一样的）
  >
  > - 方式一：利用KeySet（）方法取出存放在**Set接口**数据类型的KeySet集合中的key，然后用get(key)取出Value
  >
  >   > 这里用Collection的两种遍历方法（增强for循环、迭代器）都可以（因为Set接口和Collection接口的遍历方式一样）
  >
  > - 方式二：利用Values（）方法取出存放在**Collection接口**数据类型的Values集合中所有的Value，然后用Collection的两种遍历方法（增强for循环、迭代器）都可以；
  >
  > - 方式三：通过entrySet（）方法来获取存放在**Set接口**数据类型的EntrySet集合中的Key-value，然后通过Set的两种遍历方法（与Collection一样）遍历
  >
  >   > 涉及一个向下转型Object到（Map.Entry），然后通过EntrySet接口提供的两个方法，用Map.Entry类型的变量调用
  >
  > 

### HashMap类

> 底层是数组（存放Node）+单链表+红黑树（当数组中某一个链表的数量达到一个限制会优化成红黑树）结构；
>
> ![HashMap底层](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\HashMap底层.png)
>
> - 初始时空数组，第一次添加时为16，之后扩容时两倍

- 注意事项：

  > - HashMap没有实现线程同步，因此是**线程不安全**的；
  >
  > - 元素无序

- 又一次的底层分析https://www.bilibili.com/video/BV1fh411y7R8?t=125.0&p=538

  ![HashMap底层分析2](E:\桌面文件夹\韩顺平循序渐进学java\韩顺平 2021零基础学Java 【软件 资料 代码 笔记】\HashMap底层分析2.png)

### LinkedHashMap类（是HashMap的子类）（有序）

> - table数组定义的还是Node[]数组，但是存放的数据元素类型是**Entry类类型**，不是Node类类型了，而**Entry**是Node类的子类，是多态数组；
>
>   > Node实现了Entry接口，注意不要把Entry接口和Entry类混淆；
>   >
>   > Entry接口:
>   >
>   > Node有：hash,key,value,next属性
>   >
>   > Entry类继承Node有：before、after、hash,key,value,next属性
>
> - 第一次添加时，table数组扩容到16

---

### Hashtable类

> HashTable介绍：
>
> - 存放的元素是键值对：即K-V
>
> - **hashtable的键和值都不能为null**，否则抛出NullPointException异常
>
> - HashTable使用方法和HashMap一样，都是用Map接口的；
> - HashTable是**线程安全的**，HashMap是线程不安全的
> - 与HashMap的底层代码逻辑相同，代码不同
> - 元素无序的；

- HashTable的底层

  > 1、底层有一个数组table是HashTable$Entry[] （$$代表内部类；这个Entry实现了Map.Entry）**初始值为 11大小**；实际上数组存放的数据元素类型也是Entry
  >
  > 2、**底层table数组的扩容机制：**
  >
  > 初始化为11，临界值threshold=8；之后扩容时2倍+1

**HashMap和Hashtable的对比**

|           | 版本 | 线程安全（同步） | 效率 | 允许null键null值 |
| --------- | ---- | ---------------- | ---- | ---------------- |
| HashMap   | 1.2  | 不安全           | 高   | 可以             |
| Hashtable | 1.0  | 安全             | 低   | 不可以           |



### Properties类（是HashTable的子类）

> - Properties继承了Hashtable类并实现了Map接口，也是使用一种键值对的形式来保存数据
>
> - 他的使用特点和Hashtable类似
> - **Properties主要应用场景是从xx.properties文件中，加载数据到Properties类对象并进行读取和修改**
> - 说明：工作后xxx.properties文件通常作为配置文件，这个知识点在IO流举例；

- 常用的方法

  > - 由Map继承来的方法，增加put、删除remove、修改put添加相同的key会进行替换、查get(key)
  > - 自己独有的getProperty（key）:获取

### TreeMap类



---

## 10.4开发中如何选择合适的集合实现类？

- 主要取决于业务操作特点

  > 1、先判断存储的类型：是一组对象还是一组键值对
  >
  > > - 一组对象：Collection接口
  > >
  > >   - 允许重复：List
  > >
  > >     > 增删多：LinkedList[底层维护了一个双向链表]
  > >     >
  > >     > 改查多：ArrayList[底层维护Object类型的可变数组]
  > >
  > >   - 不允许重复：Set
  > >
  > >     > 无序：HashSet[底层是HashMap，维护了一个Hash表（数组+单链表+红黑树）]
  > >     >
  > >     > 排序：TreeSet
  > >     >
  > >     > 插入和取出顺序一致：LinkedHashSet[底层是LinkedHashMap，维护了一个hash表（数组+双向链表）]
  > >
  > > - 一组键值对：Map接口
  > >
  > >   - 键无序：HashMap[底层是：哈希表 jdk7：数组+单链表；jdk8：数组+单链表+红黑树]
  > >   - 键排序：TreeMap
  > >   - 键插入和取出顺序一致：LinkedHashMap[维护了一个hash表（数组+双向链表）]
  > >   - 读取文件：Properties







## 10.5 Collections工具类

























































































