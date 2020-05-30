# Java基础与高级

## 概述

## 基本语法

### 数据类型

### 操作符

- 优先级
- 算术
- 逻辑

	- 短路

- 自动递增与自动递减

	- ++a

		- ++在前先++

	- a++

		- ++在后，后++

- 关系
- 直接常量

	- Java的指数记数法

- 按位操作符

	- 按位与&
	- 按位或|
	- 按位异或^
	- 按位非~
	- 与等号连用

		- 非~为一元操作符，所以不能连用

	- 与布尔类型运算

		- 与逻辑操作符运算效果相同，但不会短路

- 移位操作符

	- Java独有的>>>

- 三元操作符
- 字符串操作符

	- 在字符串后才会将+重载为字符串操作符

- 类型转换操作符

	- 结尾

		- 窄化

	- 舍入

		- Math.round()

### 流程控制

- 循环控制

	- break
	- continue
	- return
	- 带有标签的跳转

		- 不支持goto
		- break label
		- continue label

- 循环结构

	- for

		- 逗号操作符

	- while
	- do-while
	- foreach(jdk1.5+)

### 关键字

## 数组

### 基础

- 一维
- 二维
- 常见算法
- Arrays

	- 静态方法toString(a);

		- 将参赛中数组转化为字符串

- 声明数组的方式

	- 声明的只是引用

		- <类型>[]  name
		- <类型> name[]

	- 更推荐<类型>[]的方式，意义表达更好
	- 数组名字只是引用

- 数组需要初始化

	- 数组名只是引用，并没有声明有占用内存空间的数组
	- 使用列表初始化

		- int[] a={1,2,3};

	- 使用new关键字初始化

		- int[] a = new int[8];

- 数组涉及的异常Runtime Error

	- 下标越界

### 高级

- 数组的特性

	- 效率

		- 效率最高的存储和随机访问对象引用序列的方式
		- 简单线性序列，元素访问非常快
		- 大小被固定
		- ArrayList弹性但是效率低

	- 类型

		- 泛型前容器在处理对象时，视作Object处理
		- 数组需要指定某种具体类型，使得通过编译期检查

	- 保存基本对象的能力

		- 泛型前，只有数组能保存基础类型
		- 泛型后，加上自动包装机制，容器能持有基本类型

	- 何时使用数组

		- 效率->数组
		- 泛化->泛型容器

- 数组是第一级对象

	- 数组标识符只是一个引用，指向在堆中创建的一个真实对象，这个（数组）对象用以保存指向其他对象的引用。
	- length

		- 是数组对象的一部分，唯一一个可以访问的字段或方法
		- 是数组占内存的长度，与内容无关

	- 初始化

		- 所有的引用都被自动初始化为null
		- 数值被初始化为0
		- 字符被初始化为(char)0
		- 布尔为false

- Arrays数组工具类

	- 转化List（默认ArrayList对象）
	- 二分查找
	- 排序
	- 转化字符串
	- 复制

		- 浅复制

	- 填充
	- 数组比较

		- equals
		- 内部使用对象的equals方法比较

	- 数组元素比较

		- 实现java.lang.Comparable接口
		- 排序会使用上述接口进行比较

- 返回数组

	- C++不能返回数组，只能使用指针的方式，控制数组生命周期变的困难，容易造成内存泄漏
	- Java

		- “直接返回一个数组”
		- 需要就会存在，使用完后，垃圾回收器将清理掉它
		- public String[] getG();

- 多维数组

	- 实质

		- 指向数组的数组，即数组的内容为数组
		- length为当前所指数组的length

- 数组与泛型

	- 通常不能很好的结合，你不能实例化具有参数化类型的数组，即数组不能识别为泛型
	- 可以参数化数组本身的类型

		- 可以将泛型作为数组对象类型的参数
		- T[] t;

## 面向对象

### 类与对象

- 类的结构

	- 属性
	- 方法

		- 重载

			- 涉及基础类型转换

				- “小”数据被尽量小变动的提升
				- “大”数据不能够被自动适应，需要自己使用类型转换操作符

			- 区分

				- 方法名字相同
				- 参数不同
				- 返回类型可以相同也可以不同

		- 特征

			- 返回值
			- 名称
			- 参数列表

		- 可变参数列表JavaSE5

			- 方法参数中使用

				- (参数1,参数2,可变参数类型... 可变参数名称)

			- 应用场合

				- 可选的尾随参数

			- 特性

				- 不用显式编写数组语法
				- 编译器实际上会填充数组，获取的仍旧为一个数组
				- 可以传空

			- 易错

				- method(类型... name)
				- method()
				- 以上两种会产生混淆，编译器无法知道应该调用哪一种方法

	- 构造器

		- 目的

			- 类需要有初始化方法，进行初始化操作initialize
			- 确保在类使用之前一定有初始化操作

		- 特征

			- 目的是为了初始化对象（分配内存等），所以没有返回值
			- 方法名字与类名相同

		- 何时执行

			- 使用new关键字，在堆上创建对象，调用的就是构造方法

		- 有参
		- 无参

			- 又称默认构造器

		- 重载

			- 遵从方法的重载规则

				- 涉及基础类型转换

					- “小”数据被尽量小变动的提升
					- “大”数据不能够被自动适应，需要自己使用类型转换操作符

				- 区分

					- 利用特征

		- 调用另一个构造方法

			- 使用this

				- 只能使用一次

		- 默认构造器

			- 若没有定义构造方法，编译器会给类配置一个默认构造方法，该方法只做初始化操作
			- 特征

				- 参数为空，又叫“无参构造器”

			- 若已经存在了程序员自定的构造方法，而未定义默认构造器，则不能使用默认构造器构造新对象

	- 初始化属性

		- 指定初始化

			- 直接在类中给变量赋值

		- 构造器初始化

			- 利用构造器，对类的值进行初始化操作

		- 数组初始化

			- 

		- 静态成员的初始化，static成员

			- 静态数据只占用一份存储区域
			- 线程共享
			- 只在有必要初始化的时刻进行初始化

				- 不会初始化的情况

					- 未使用到该静态属性
					- 未创建对象

			- 注意在分布式的系统中，不同的系统有不同的内存区域，此时的静态数据就相当于有了多个存储区域

		- 默认值

			- 数字为0
			- boolean为false
			- 引用为null
			- 有new操作的成员执行new操作

		- 实例初始化语句

			- 非静态属性

				- 直接使用代码块

		- 显式静态初始化

			- 使用跟在static关键字够的代码块

		- 初始化顺序

			- 规律

				- 先静态后非静态
				- 先属性后构造器

			- 具体顺序

				- 类被首次使用到时，java解释器查找类路径，找到.class文件
				- 载入.class文件，会生成Class对象，执行有关静态初始化的操作
				- 使用new创建对象，在堆上为对象分配足够的空间
				- 改存储空间被清零，所有属性设置为默认值
				- 执行处于字段定义出的初始化操作
				- 执行构造器

	- 关键字this

		- this出处

			- 编译器在调用方法时会传入对象的引用

				- “发送消息给对象”

		- 方法调用另一个构造方法

			- 使用this，增加参数列表

				- 只能调用一次
				- 只能在构造方法内
				- 构造方法语句必须第一位

	- 关键字static

		- static方法

			- 与非静态方法的区别

				- 非静态方法会传入对象引用，static方法不会

					- static不需要创建对象

		- static属性

			- 属于类所有，不需要创建类就能使用

				- static方法使用类的属性，则该属性也必须为静态

		- 只占用一份内存
		- 线程共享

	- 关键字final

		- final数据

			- 用于基本类型

				- 数值不会改变

			- 用于对象引用

				- 引用的对象不能更换，不影响对象内容

					- 可以理解为地址不可变

			- 空白final

				- 被声明为final但又未给定初值的域
				- 无论什么情况，编译器都要确保在空白final使用前初始化域
				- 需要在构造方法中进行初始化
				- 可以使不同的对象有不同的值

			- final参数

				- Java允许在参数列表中以声明的方式将参数指明为final。
				- 你无法在方法中更改参数引用指向的对象

		- final方法

			- 将方法锁定，防止继承类修改它的含义
			- 效率，指明为final的方法，编译器将针对方法的所有调用都转为内嵌调用。用在小型方法上，效果明显

				- 不推荐使用来提高效率，运行的优化应该交给Java虚拟机进行操作

		- final类

			- 不允许被继承

		- final与private

			- 类中所有的private都隐式地指定为final

	- main函数

- 概述

### 复用类

- 组合语法

	- 在类中使用其他的类的方法

		- 声明一个其他类的成员

			- 初始化该成员

				- 定义处进行初始化

					- AClass a =new  AClass();

				- 构造器中初始化

					- 在构造器中进行初始化成员类

				- 实例初始化

					- 利用实例初始化语法，使用大括号包括

				- 惰性初始化

					- 在方法中，对成员进行检查，为空就进行初始化

- 继承语法

	- 详细在下方

- 代理

	- 继承会将基类的所有方法都暴露出来，若只需要一部分方法，应该采用代理的方式
	- 创建成员对象，在类的方法内，调用成员对象的方法，达到代理的目的

### 面向的对象的特征

- 封装：访问权限控制

	- 构造器
	- import

		- 导入包、类到当前类文件，使其他文件的代码文件可以在此类进行使用

			- 导入整个包

				- import  包名.*;

			- 导入指定类

				- import 包名.类名

		- 包冲突

			- 将含有同样名称的类库（.java文件)同时利用import导入

				- 不能使用全名导入，会编译报错
				- 使用导入库的方式，在使用该类会报错

	- package关键字

		- 要求

			- 位置：文件除注释外的第一行代码
			- 仅能使用小写
			- 习惯上，与项目文件夹对应（未强制，但是都这么做，也必须这样做）

		- 作用

			- 给类划分包
			- 将一组相互具有联系并组合起来完成某一功能的类聚集到一起，比如java中的工具库，通常一个库是由多个class所组成，为了方便组织我们把这组class放在同一个目录下，这个目录就是看作是一个java包（当然还需要在java文件开头用package声明一下）。

	- 包：库单元

		- 使用类的方式

			- 使用全名 包.类名
			- 使用import关键字导入该类，则不需要打出包地址
			- 使用import关键字导入该类所在包

		- 类库的概念

			- 包内含一组类，在单一的名字空间下被组织在一起

				- 一组类文件，每个文件都有一个public类，以及任意数量的非public类（一个java文件只有一个public类）

					- 该文件名与public类的名字相同

				- 每个文件都有自己的.java和.class文件，若希望这些构件从属一个群组，使用package关键字

		- 代码组织

			- 一个.java类型文件

				- 可能含多个类

					- 每个类都会生成.class 文件

				- 只有一个public类

					- 文件名与该类名相同
					- 只能是public的，否则无法访问

			- Java可运行程序

				- 一组可以打包并压缩为一个Java文档文件（JAR，使用Java的jar文档生成器）的.class文件
				- Java解释器负责这些文件的查找、装载和解释

		- 默认包，又称未命名包

			- 最简单的情况，未指定包名，用当前几个类就能完成使用，不需要合作其他包，不需要考虑封装
			- 同处于相同的目录，并且没有给自己设定包名
			- 新手会接触，后期基本所有代码都有组织分包

		- 创建一个不会重复的包

			- 可以类似将域名倒着书写，就是分配包的方法，较为整齐，不易混乱

				- com.alibaba.proj

	- Java访问权限修饰词

		- 默认，空白

			- 包访问权限

				- 有时候表示为friendly
				- 当前包中所有其他类对这个成员都有访问权限

		- public

			- 接口访问权限

				- 构造器一般为public，这样包外类才能使用该类（除了一些设计模式会不使用public）

		- private

			- 私有成员：你无法访问

				- 除了包含该成员的类之外，其他任何类都无法访问这个成员
				- 通常用于隐藏措施

		- protected

			- 保护的，只允许包内和子类访问

				- 默认+子类

	- 接口和实现

		- 封装

			- 把数据和方法包装进类中，以及具体实现的隐藏

		- 将接口方法（public方法）置于类的前部，方便阅读与使用

- 继承

	- 继承的概念

		- 使用特殊语法

			- extends关键字

		- 会自动得到基类中的所有的域和方法
		- 当创建了一个导出类的对象时，该对象包含了一个基准的子对象。这个子对象与你用基类直接创建的对象是一样的，二者的区别在于，后者（直接组合）的来自于外部，而基类的子对象被包装在导出类对象的内部
		- 特性

			- 只能有一个基类
			- 继承必须保证调用基类构造器进行初始化基类

	- 方法的重写

		- 在子类中可以定义与基类方法名字相同的方法，基类的方法就会被屏蔽，达到覆写的效果
		- 使用@Override注解（jdk1.5）

			- 注解了的方法不是覆写方法就会报错
			- 防止覆写误写为重载

	- 关键字super

		- 基类子对象的引用，（也可以理解为父类对象，但是并不是父类对象，而是隐式内置在类中的基类的子对象）

	- 向上转型

		- “新类是现有类的一种类型”

			- 将子类当做基类使用
			- 方法接受基类，传入基类，能正常运行

	- @Override与Overload

		- Override用在继承关系
		- Overload用在同一个类中

- 多态

	- 概念

		- 向上转型

			- 接受基类的方法，也能接受子类，因为子类就是基类的一种特殊类型
			- 使得方法与对象解耦，方法只需要设定为允许基类参数，使用基类确定的方法名（方法名，因为可以重载）

		- 方法的参数类型的绑定

			- 绑定

				- 将一个方法调用同一个方法的主体关联起来

			- 前期绑定

				- 在编译期间就确定了使用对象的类型

					- 不便于解耦，方法执行的实质是“已知”的，也就是参数类型对应的方法

			- 后期绑定

				- 在运行时根据对象的类型进行绑定，又作动态绑定或运行时绑定

					- 便于解耦，方法执行的实质要根据传入的对象参数的“实质”对象类型来确定

			- Java中的前期绑定与后期绑定

				- 使用final关键字

					- 前期绑定

				- 默认

					- 后期绑定

		- 多态

			- 利用后期绑定的性质，在调用某个方法时，该方法执行的结果与该对象的该方法的“实际”设定有关

				- 对象类型是由对象本质类型决定的
				- 向上转型过程中，变化的是引用的类型，对象的信息不会改变
				- 由于编译器不能预知传入的实际类型，所以只能使用参数中的引用类型对应的方法

			- 不同的对象对某个方法有自己的实现，在调用这个方法时，虽然利用基类调用方法，结果却有差距

	- 构造器与多态

		- 构造器中避免多态操作

			- 构造器作为特殊方法没有多态（实际上为static方法）

				- 基类构造器在导出类的构造器中被调用，按照继承层次一层层向上调用

			- 构造器内部的多态方法行为

				- 构造器调用的方法仍然是符合多态的，及动态绑定的，但构造器调用的时期，类并未初始化完成，得到的结果可能是危险的

	- 协变返回类型JavaSE5

		- 允许导出类中被覆盖方法可以返回基类方法的返回类型的某种导出类型（子类）

	- 向下转型

		- 向下转型是不安全的，因为不确定该类有子类的信息
		- 运行时类型识别

			- Java中，所有的转型操作都会得到检查
			- 如果不和要求，就会返回ClassCastException（类转型异常）

	- Object类

## 接口

### 关键字

- abstract

	- 定义虚拟方法或对象

- interface

	- 定义接口

- implements

	- 用于实现接口

### 抽象类和抽象方法

- 目的

	- 创建一个专门服务与多态与继承的类型 
	- 做到了规定方法，指定标准（指定需要实现的方法）

- 抽象类

	- 包含有抽象方法的类

		- 必须被声明为abstract
		- 可以含有普通方法

	- 编译器不允许抽象类被实现
	- 继承抽象类需要实现所有的抽象方法

		- 否则导出类仍为抽象类，被要求abstract

- 抽象方法

	- 不完整且没有方法体

		- abstract  类型  方法名();

### 接口

- 概念

	- interface是abstract类的进一步升级
	- 建立类与类之间的“协议”
	- 类使用接口，推荐使用实现而不是继承

		- 实现表示所有的方法都要实现
		- 继承在继承部分中讲到，不需要实现基类方法

- 特性&要求

	- 使用interface产生的是一个完全抽象的类，没有任何方法的具体实现
	- 允许创建者确定方法名，参数列表和返回类型，但是没有方法体
	- 访问权限

		- 接口可以使用public和默认两种
		- 接口方法默认且必须是public的
		- 接口内容只能且默认为public的

	- 禁用

		- 禁止实例初始化，只能直接就地初始化
		- 禁止使用private类型

			- 禁止私有成员
			- 默认无包类型，为public

- 完全解耦

	- 将接口作为基类，可以达到解耦
	- 使得方法从操作类升级到操作接口
	- 只需要关心方法的最终效果，不需要关心方法是谁实现的，怎样实现的，只要引入接口就可以做到

- 策略设计模式

	- 利用继承与多态，预设不同的继承类（如大小写装换，预设转大写的子类，转小写的子类）调用方法设置两个参数，一个参数选择策略，一个参数放待处理内容，方法中调用多态方法完成操作，Java的多态会根据类型来完成目的

- 适配器模式

	-  适配器模式将某个类的接口转换成客户端期望的另一个接口表示，目的是消除由于接口不匹配所造成的类的兼容性问题。主要分为三类：类的适配器模式、对象的适配器模式、接口的适配器模式。
	- 著名的设计模式“四人帮”这样评价适配器模式： 将一个类的接口转换成客户希望的另外一个接口。Adapter 模式使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。——Gang of Four
	- 将一个类的接口适配成用户所期待的
	- Adapter 设计模式主要目的组合两个不相干类，常用有两种方法

		- 第一种解决方案是修改各自类的接口
		- 如果没有源码，或者不愿意为了一个应用而修改各自的接口，则需要使用 Adapter 适配器，在两种接口之间创建一个混合接口。

			- 

- 接口与继承

	- 类似类，使用extends关键字，继承基类方法
	- 允许继承多个接口，因为接口没有存储于实现
	- 接口继承不需要实现基类接口的方法

- 接口与多重继承

	- Java中对象只能有一个基类（C++允许多重继承）
	- Java中，接口没有任何具体实现，也就是没有任何与接口相关的存储，因此无法阻止多个接口的组合
	- Java中类可以实现（implements）多个接口，使用逗号隔开，并且对象可以向上转型为每一个接口类型
	- 陷阱

		- 使用多重继承时，会出现返回类型不同，但接口方法名相同的情况，此时同时实现这两接口将报错
		- 在打算组合的不同接口中使用相同的方法名会造成方法可读性的混乱，需要尽量避免

- 接口中的域

	- 放入接口中的任何域都自动是static和final的
	- JavaSE5之前使用接口代替了枚举类
	- 接口中定义的域不能是“空final”,但是可以被非常量表达式初始化

- 接口嵌套

	- 接口可以与类和接口嵌套

		- 此时的接口可以拥有私有访问权限private
		- 类似类的一个属性，拥有组合类相同的访问管理方式

	- 与接口嵌套

		- 由于接口的属性不能被定义为private，接口中嵌套的接口也不能被定义为private

- 工厂模式完全解耦

	- 利用工厂设计模式，返回接口的实现对象，用户只需要使用工厂类，就能得到一个接口配对的实现类
	- 提高代码的复用性

- Java8的接口增强

	- default

		-  在接口中可以添加使用 default 关键字修饰的非抽象方法。即：默认方法（或扩展方法）

			- Java 8 允许给接口添加一个非抽象的方法实现，只需要使用 default 关键字即可，这个特征又叫做扩展方法（也称为默认方法或虚拟扩展方法或防护方法）。在实现该接口时，该默认扩展方法在子类上可以直接使用，它的使用方式类似于抽象类中非抽象成员方法。
			- 扩展方法不能够重写（也称复写或覆盖） Object 中的方法，却可以重载Object 中的方法。

				- toString、equals、 hashCode 不能在接口中被覆盖，却可以被重载。

	- static

		- 接口里可以声明静态方法，并且可以实现
		- 接口中的静态方法不会被继承,接口中的静态变量会被继承

	- default方法属于实例,static方法属于类(接口)
	- 如果一个实现类 继承并调用了两个接口中同名的默认方法，编译器将报错

		- 解决办法

			- 实现类重写该方法
			- 重写方法可以使用特殊语法 
@Override
    public void eat() {
        IUser.super.eat();
    }

				- 语法格式:XXinterface.super.重名method();

		- 如果两个含同名的默认方法,有继承关系，可以使用，使用为最近的基类

	- 特殊注解

		- @FunctionalInterface

			- 限定接口只能有一个抽象方法
			- package java.lang;
 
import java.lang.annotation.*;
 
@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
public @interface FunctionalInterface {}
			- 配合lambda表达式

## 内部类

### 定义

- 将一个内部类的定义放在另一个类的定义内部
- 允许将一些逻辑相关的类组织在一起，并控制与内部的类的可视性

### 特性

- 内部类作为外围类的一部分，可以拥有不同的访问权限修饰词（外围类作为该类库的接口类，只能为public）

	- private
	- 默认
	- public
	- protected

- 非静态的内部类不能拥有静态成员

	- 会无法初始化

- 不能直接调用

	- 内部类只是定义在外围类中，并没有实例
	- 要想使用需要初始化一个内部类

- 内部类可以独立的继承基类或实现接口，外围类对接口的实现不影响内部类

### 创建内部类

- 定义

	- 把类的定义置于外围类的里面即可
	- 内部类的定义不是程序运行语句，不能用冒号在最后结尾

- 初始化

	- 外部类对象.new 内部类构造方法
	- 静态内部类（嵌套类）不需要初始化

		- 类似静态成员
		- 内部全部要求静态

### 访问内部类

- 直接访问（需要有可访问权限）

	- OuterClassName.InnerClassName

- 表示内部类

### 内部类与外部类

- 内部类作为外围类的“成员”，拥有完全的访问外围类成员的权限
- 外围类的引用

	- 外部类.this

- 内部类访问其他类不受限制，与外围类相同

	- 组合
	- 继承
	- 实现接口

### 内部类向上转型

- 内部类可以实现接口，实现这个内部类，可以得到接口的引用
- private内部类可以让设计者完全阻止任何依赖与类型的编码，并且完全隐藏实现

### 在方法和作用域中的内部类

- 使用场景

	- 实现某类型的接口，创建并返回对其的引用
	- 创建一个类来辅助你的解决方案，但又不希望这个类是公共可用的

- 局部内部类

	- 定义在方法作用域中
	- 定义一个内部类不需要分号
	- 只能在作用域使用，离开无效

### 匿名内部类

- 描述

	- 在构造一个继承了基类的对象后，直接返回这个对象
	- 在上面的步骤中没有涉及给对象起名
	- 返回的是目标类的子类
	- 由于构造后直接返回，通常是只使用一次的内部类

- 实现

	- return new Content(){
private int i =1；
}；

- 初始化

	- 匿名内部类因为没有类名，不能使用构造函数初始化
	- 实例初始化
	- 就地初始化

- 利用匿名内部类设计工厂模式
- lambda表达式Java8

	- 若实现的是只有一个方法的接口，可以使用lambda表达式
	- @FunctionalInterface可以保证接口只有一个方法

### 嵌套类

- 定义

	- 如果不需要内部类对象与其外围对象的联系，可以将内部类声明为static
	- 要创建嵌套类的对象，并不需要外围类的对象
	- 不能从嵌套类的对象中访问非静态的外围类对象

- 与普通内部类的区别

	- 普通内部类不能拥有静态成员

		- 静态方法
		- 静态属性
		- 静态内部类/嵌套类

	- 普通内部类初始化需要借用外围类对象调用
	- 嵌套类可以拥有非静态的成员
	- 嵌套类初始化可以脱离外围对象存在，不需要借用外围类对象初始化

- 嵌套类的实质

	- 将类置于外围类的命名空间

### 接口内部类

- 默认是public 和 static的

### 为什么使用内部类

- 闭包与实现

	- 定义一个私有的内部类并通过方法返回实现

- 控制框架

### 继承内部类

- 在继承的模块讲过

	- 基类会作为一种特殊的对象存在在子类对象中，所以我们需要初始化基类对象

- 初始化内部类

	- 初始化内部类需要先获得外部类的对象，然后利用对象获得内部类

		- 因为内部类嵌套在外部类中，处于安全，防止内部类需要的外部类没有被初始化

- 继承内部类的操作

	- 先获得外部类对象
	- 子类构造方法传入外部类对象并调用

### 内部类不存在覆盖问题

- 内部类依托外部类存在，即使继承了外部类再加上相同的内部类名，两个内部类所在的命名空间也是不同的，不是同一种类
- 想要重写内部类的方法，怎么办？

	- 让这个类的内部类继承基类的内部类

### 局部内部类

- 在方法体内创建，只能作用于该方法块，可以调用外部方法与成员
- 方法块的死亡也会让这个局部内部类只能作用在该方法块
- 可以满足多次使用改类的需求

### 内部类标识符

- 内部类也会产生.class文件

	- 命名规则

		- 外围类$内部类.class

## 容器（持有对象、集合）

### JavaSE5为容器带来的关键内容——泛型

- 在JavaSE5前

	- 容器都使用的是Object
	- 允许向容器中插入不正确的类型

- JavaSE5之后

	- 在编译器防止错误类型的对象放置到容器中
	- 能使用foreach访问List集合

### 基础概念

- 用途

	- 保存对象

- 解决的问题

	- 程序根据运行时才知道的某些条件创建对象，所以不能依靠创建命名的引用来持有每一个对象
	- java提供了多种保存对象“引用”（注意是引用，而不是对象）的方式

		- 数组
		- 集合类

- Collection

	- 独立的元素序列，服从一条或多条规则
	- List

		- 按照插入顺序保存元素

	- Queue

		- 按照排队规则来确定对象产生的顺序

	- Set

		- 不能有重复元素

- Map

	- 成对的“键值对”对象
	- ArrayList

		- 允许使用数字查找值

	- HashMap

		- 默认使用该Map

	- 可以返回键的Set，Collection，键值对的Set

- 编写习惯

	- 大多数情况下，与接口交互，只在创建时设计具体的实现类

		- List<String> s= new ArrayList<String>()

### 工具类

- Arrays

	- asList()

		- 接收一个数组或是一个用逗号分隔的元素列表（参数列表，不是字符串,可变参数！！），将其转化为List对象
		- 返回的List类型

			- 默认返回Object
			- 显式类型参数说明

				- 通过List<YourClass> list= Arrays.asList()能制定类型，同时利用泛型进行编译时检查

	- toString()

		- 打印数组
		- 打印容器不需要，容器已经自带修改的toString

- Collections

	- addAll()

		- 接受一个Collection对象，一个数组或用逗号分隔的列表，将元素添加在Collection中

### List

- 将元素维护在特定的序列里
- 实现类

	- ArrayList

		- 随机访问元素

	- LinkedList

		- 插入和删除元素
		- 优化的顺序访问
		- 随机访问较慢

- 方法

	- contains

		- 查询是否包含

	- containsAll
	- remove

		- 移除

	- indexOf

		- 索引号

	- subList

		- 获取子集合

	- retainAll

		- 交集

### Stack

- 栈
- Stack有专用的类，是java1.5升级来的
- 不建议使用，因为LinkedList已经有了栈操作的实现，因为Linkedlist实现了queue接口

### Set

- 通常使用HashSet

	- Hash为Set提供了快速查找的特性
	- 创建有序序列可以使用参数选择排序方法，在new时传入构造函数

### Queue

- 先进先出的容器
- 实现

	- LinkedList
	- PriorityQueue

		- 优先级队列，在插入时会进行排序
		- 默认使用自然顺序，可以提供自己的Comparator来修改行为

- 双向队列

	- 在任意一段添加或移除元素
	- LinkedList
	- 没有接口的实现

### 迭代器

- 为一种设计模式也是java集合重要的接口
- 接口

	- Iterator

		- 单向移动

	- ListIterator

		- 双向移动

- 使用方法

	- 集合有返回迭代器的方法

		- 实现原理：匿名内部类

- 允许类被Foreach遍历

	- 实现Iterable接口

### 集合关系图

- 

### 高级

- Collections工具类

	- 填充
	- addAll()
	- 二分查找
	- 转化其他集合
	- 复制
	- 判断有没有交集
	- 生成空集合
	- 查找元素频率
	- 转化数组
	- 最大最小
	- 替换
	- 比较器
	- 交换位置
	- 返回线程安全类型集合
	- 返回不可修改类型集合

- Set和存储顺序

	- 不同类型Set之间的区别

		- Set维护存储顺序的方式
		- 在特定的Set中放置的元素的类型也有所不同

	- Set

		- 存入容器的每个元素唯一
		- 加入的元素需要自定义equals方法以确保对象唯一性
		- Set与Collection接口相同，所以不维护元素次序

	- *HashSet（无其他限制，默认选择）

		- 存入HashSet的元素必须自定义hashCode()

	- TreeSet

		- 保持次序的Set，底层为树
		- 必须实现Comparable接口

	- LinkedHashSet

		- 有HashSet的查询速度，内部使用链表维护元素次序（插入的次序）。
		- 遍历时会按照插入顺序显示
		- 需要定义hashCode方法

	- SortedSort

		- 实现：TreeSet
		- frist
		- last
		- subSet生成子集
		- headSet，生成子集，小于参数的元素组成
		- tailSet,大于参数的子集

- 理解Map

	- 实现

		- HashMap

			- 基于散列的实现，（取代HashTable）。通过构造器设置容量和负载因子
			- JavaSE8 对HashMap做了修改，当规模超出

		- TreeMap

			- 基于红黑树的实现。查看“键”或“键值对”时，它们会被排序
			- 唯一有subMap的类型

		- LinkedHashMap

			- 遍历顺序为插入顺序，或者为最少使用的次序LRU，迭代访问更快

		- WeakHashMap

			- 弱键映射，允许释放映射所指向的对象；映射之外没有引用，则可以回收

		- ConcurrentHashMap

			- 线程安全的Map，不涉及同步加锁。

		- IdentityHashMap

			- 使用==代替equals进行比较

		- SortedMap

			- TreeMap是唯一实现

		- LinkedHashMap

			- 散列化所有元素，在遍历键值对时又以插入顺序返回键值对，可以在构造器中设定LinkedHashMap,使之采用基于访问的最近最少使用算法，没有被访问过的元素就会出现在队列的前面。

	- 性能

		- 默认使用HashMap

			- 对速度进行了优化

- 散列与散列码

	- Object自带hashCode方法

		- 使用本地方法，为对象的地址
		- 在同一次运行中，相同的对象有相同的hash码
		- equals方法会使用hash码进行比较，以此确定是否为同一个对象
		- toSting方法也使用了hashCode

 getClass().getName() + "@" + Integer.toHexString(hashCode());

	- 实现自己的hashCode

		- 同一个对象一定要是同一个答案
		- 一般建议使用Java默认的，没必要不要修改
		- 要考虑碰撞效率，所以闲着没事干别动了

### 持有引用

- java.lang.ref

	- Reference

		- SoftReference

			- 内存高敏感的告诉缓存

		- WeakReference

			- 实现”规范映射“

		- PhantomReference

			- 调度回收前的清理工作，比Java终止机制更灵活

		- SoftReference，Weak，Phantom由强到弱排列

- 使用环境

	- 对象可获得的（reachable）

		- 此对象可在程序中的某处找到
		- 栈中的一个引用
		- 引用的对象中包含的引用

	- 希望继续持有某个对象的引用，且希望能够允许垃圾回收器释放它

- 地位

	- 你和普通引用之间的媒介

### Java 1.0/1.1容器

- Vector

	- 自我扩展序列 ，废弃

- Enumeration

	- 取代迭代器

- Stack

	- 继承Vector，设计不是很合理

- BitSet

	- 高效存储大量“0、1”

## 异常处理

### 概念

- Java的基本理念

	- “结构不佳的代码不能运行”

- 错误发生的时期

	- 运行期间
	- 编译时期

- 传统监测数据的缺陷

	- 每次调用方法的时候都彻底地进行错误检查，代码可读性很低

- “我对此感到意外”的意思
- 减低错误处理的复杂度

### 异常

- 异常情形

	- 指阻止当前方法或作用域继续执行的问题

- 处理步骤

	- 0.抛出异常
1.使用new在堆上创建异常对象
2.当前的执行路径被终止，并且从当前环境中弹出对异常对象的引用。
3.异常处理机制接管程序，并开始寻找一个恰当的地方来继续执行程序。（异常处理程序）

- 意义

	- 使得强制程序停止运行，并告诉我们出现了什么问题，或者强制程序处理问题，并返回到稳定状态
	- 将程序当做事务来考虑

- 异常参数

	- 所有标准异常类都有两个构造器

		- 默认
		- 字符串为 参数的构造器

- 异常根类

	- Throwable

- 异常信息（方法）

	- 栈轨迹

		- printStackTrace

			- 参数

				- printStackTrace()

					- 默认使用标准错误流

				- printStackTrace(PrintStream)
				- printStackTrace(java.io.PrintWriter)

		- getStackTrace()

			- 返回一个由栈轨迹中元素构成的数组，每一个元素都表示栈中的一帧
			- 元素0位栈顶，为调用序列中最后一个方法调用

### 捕捉异常

- 概念

	- 监控区域

		- 一段可能产生异常的代码，并且后面跟着处理这些异常的代码

- try-catch

	- 在try块内发生的错误，依次与catch块中的异常类型进行比较，匹配第一个进入catch块中进行处理

- 终止√、恢复×

	- 异常处理的两种模型

		- 终止模型

			- Java

		- 恢复模型

			- 修正错误，然后重新尝试，需要非通用性代码，被抛弃

- 异常匹配

	- ”最近“匹配的处理程序

- 捕获所有异常

	- 原理

		- 所有的异常都继承自Exception
		- 捕获Exception类型即为捕获所有异常

	- 注意

		- Exception将匹配所有异常，放在前面会干扰逻辑，一般都位于最后

- 重新抛出异常

	- 将参数再次throw

		- 将被外层捕捉
		- 异常信息 不会改变
		- 异常不会记录从哪里被重新抛出
		- e.fillInStackTrace()可以更新异常信息

	- throw new

		- 异常将发生改变

- 异常链

	- 在捕捉一个异常后抛出另一个异常，并保留异常的信息
	- JDK1.4接收cause对象作为参数的构造器

### 异常处理finally块

- 无论try中的异常是否抛出，finally块中的代码都将执行
- 功能

	- 通常用于内存之外的回收
	- 恢复内存之外的资源到初始状态

		- 网络连接
		- 屏幕上画的图形
		- 外部世界某个开关
		- 。。。

- 有return语句的情况

	- finally依然会执行，在何处返回无关紧要

### finally导致的异常丢失

- try块中包含了抛出异常的代码、抛出异常的finally块

	- 只会抓到finally中的异常

- 代码示例

  public class Demo1 {
  	
  	void f1() throws MyException1{
  		throw new MyException1();
  	}
  	void f2() throws MyException2{
  		throw new MyException2();
  	}
  	
  	public static void main(String[] args) {
  		Demo1 d = new Demo1();
  		try{
  			try {
  				d.f1();
  			}finally {
  				d.f2();
  			}
  		}catch (Exception e){
  			System.out.println(e);
  		}
   
  	}
   
  }
   
  class MyException1 extends Exception{
  	@Override
  	public String toString() {
  		return "MyException1...";
  	}
  }
  class MyException2 extends Exception{
  	@Override
  	public String toString() {
  		return "MyException2...";
  	}
  }

### 自定义异常

- 必须从已有的异常类进行继承
- 选择相近的异常类继承
- 使用编译器为你产生的默认构造器

	- 利用继承

- 打印的错误信息最好选择System.err

	- 防止标准输出被重定向
	- 默认的e.printStackTrace可以输出到标准错误流

### 异常说明

- Java鼓励人们把方法可能会抛出的异常告知使用此方法的客户端程序员
- 使得调用者能确切知道写什么代码可以捕获所有潜在的异常
- 强制要求方法命名时表明可能抛出的异常类型，即异常说明
- 可以声明可能抛出异常但是却不抛出

	- 占位效果，下次不需要修改
	- 编译时被检查的异常——被检查的异常

- 异常限制（继承）

	- 当覆盖方法时，只能抛出在基类方法的异常说明里列出的那些异常

		- 基类使用的代码应用到其派生类对象的时候，一样能工作

	- 对构造器不起作用

		- 派生类构造器如果不调用父类构造方法，是不会使用父类的构造方法的
		- 调用父类构造器则需要抛出

### Java标准异常

- Throwable

	- Error

		- 编译时和系统错误
		- 一般不需要关心

	- Exception

- 特例：RuntimeException

	- 不受检查的异常
	- 自动地被Java虚拟机抛出
	- 代表编程错误

		- 无法预料的错误
		- 作为程序员，应该在代码中进行检查的错误

	- 可以被throw同时不被声明

### try-with-resources

- try-with-resources 语句确保了每个资源在语句结束时关闭。所有实现了 java.lang.AutoCloseable 接口（其中，它包括实现了 java.io.Closeable 的所有对象），可以使用作为资源。
- try(Resource res = new Resource()) {
            res.doSome();
        } catch(Exception ex) {
            ex.printStackTrace();
        }
- try-with-resources 声明在 JDK 9 已得到改进。如果你已经有一个资源是 final 或等效于 final 变量,您可以在 try-with-resources 语句中使用该变量，而无需在 try-with-resources 语句中声明一个新变量。

### 构造器中的异常处理

- 在构造器执行失败时，可能有需要清理的内容

	- io，连接等等

### 异常使用指南

- 在下列情况使用异常

	- 在恰当的级别处理问题
	- 解决问题并且重新调用产生异常的方法
	- 进行少许修补，然后绕过异常发生的地方继续执行
	- 用别的数据进行计算，以代替方法预计会返回的值
	- 把当前运行环境下能做的事情尽量做完，然后把相同的异常抛至更高层
	- 把当前运行环境下能做的事情尽量做完，然后把不同的异常抛至更高层
	- 终止程序
	- 进行简化
	- 让类库和程序更安全

## 字符串

### 不可变String

- String类中每一个看起来会修改String值的方法，实际上都创建了一个全新的String对象
- String对象做参数，传的是引用，指的是同一个对象

### +与StringBuilder

- 使用+会导致创建新的String对象，加重垃圾回收负担
- 使用StringBuilder.append可以避免多次创建对象

	- 内部返回的是StringBuilder，不会新建对象

- 简单操作用+解决，循环使用StringBuilder解决

### 误用导致递归

- 在toString()方法中，打印字符串+(+已经被重载)this
- print("this is"+this);
- 将一直调用toSting方法，导致递归

### 正则表达式进行字符串匹配后操作

## 类型信息

### RTTI

- Runtime Type Informatica

	- 两种类型

		- 传统RTTI

			- 编译时了解所有类型

		- 反射

			- 在程序运行时发现和使用类的信息

	- 意义

		- 在运行时，使程序拥有识别对象类型的能力

### Class对象

- 用来创建所有的“常规”对象。
- Java使用Class对象来执行RTTI
- 产生

	- 每一个类都有一个Class对象
	- 编译产生的字节码文件.class将被类加载器加载
	- 所有类都是在对其第一次使用时，动态加载到JVM的。当程序创建第一个对类的静态成员的引用时，就会加载这个类
	- 类加载器首先检查这个类的Class对象是否已经被加载。若尚未加载，默认的类加载器就会根据类名查找.class文件
	- 一旦某个类的Class文件被载入内存，它就被用来创建这个类的所有对象

- 使用类而做的准备工作

	- 加载

		- 类加载器执行。
		- 查找字节码，并创建一个Class对象

	- 链接

		- 验证类中字节码
		- 为静态域分配空间
		- 必要的话解析这个类创建的对其他类的所有引用

	- 初始化

		- 如果该类具有超类，就对其进行初始化，执行静态初始化和静态初始化块

- 取得Class对象

	- Class.forName(String classname);
	- 类字面量

		- YourClass.class

			- 更安全

		- 不会自动初始化该Class对象
		- 不会引发Class类对象的初始化操作
		- 基础类型的包装类中有标准字段TYPE，指向对应的基本数据类型的Class 对象
		- 初始化被延迟到了 对静态方法或者非常数静态域进行首次引用

- 泛化的Class引用

	- Class引用总是指向某个Class对象，可以利用该对象生成实例。
	- Java SE5泛型的出现，使得Class的类型更为具体，允许对Class引用所指向对象的类型进行限定
	- 让编译器强制进行额外的类型检查
	- Class<?>优于Class

		- 表示不是错误编写，显式地说明自己希望能被转化

	- 表达派生类

		- Class<? extends N>
		- Class对象间是没有继承的，Class对象仅仅与类有关

	- Java SE5 新的转型语法

		- cast()方法

			- 将参数对象转型为Class类对应的类的对象

		- class Building {}
class  House extends Building {}
public class ClassCasts {
    public static void main(String[] args) {
        Building b=new House();
        Class<House> houseClass= House.class;
        House newb = houseClass.cast(b);
        House newb2 = House.class.cast(b);
        newb = (House) b;
    }
}


- 获取类信息的方法

	- getName()
	- isInterface()
	- getSuperClass()

- 生成对象

	- newInstance()

		- 改类需要有默认构造器

### 类型检查

- 确认对象是否为某个特定类型的实例
- instanceof关键字

	- instanceof

		- 返回布尔值

	- Java SE14 中对instanceof的增强

		- 使用instanceof，若为该类型的实例，就能转换

	- 大量使用会导致程序灵活性很低

- 动态的instanceof

	- Class.isInstance()

- 直接比较Class

	- a.class==b.class

- 区别

	- instanceof

		- 是否属于派系

	- Class == Class

		- 是否为同一个类型

### 反射：运行时的类信息

- 动机

	- 获取一个未知的对象
	- 提供跨网络的远程平台上创建和运行对象的能力：RMI（远程方法调用）

- 支持

	- java.lang.reflect
	- Class

- Class的方法

	- 常用方法

		- getMethods
		- getFields
		- getConstructors

	- 

### 动态代理

- 代理

	- ”中间人“，接到消息，进行初步处理，然后把消息送给目标
	- 给对象添加额外的操作，同时不修改源码

- Java动态代理

	- 动态地创建代理并动态地处理对所有代理方法的调用
	- 实现动态代理

		- 编写被代理的类与添加的功能类，使用接口，降低耦合

			- public interface SayChinese {
    String speakChinese(String name,String word);
}
public interface ForeignLanguage {
    void speak(String name);
}


		- 编写被代理类

			- public class Chinese implements SayChinese {
    @Override
    public String speakChinese(String name ,String word) {
        String say="我会说中文不信？:"+word;
        System.out.println(say);
        return say;
    }
}

		- 编写一个能利用参数处理的扩展类

			- public class EnglishForeignLanguageImpl implements ForeignLanguage {
    @Override
    public void speak(String name) {
        System.out.println("Hello,my name is "+name);
    }
}

		- 编写代理类，代理处理类实现InvocationHandler接口，重写invoke方法

			- public class CokeProxyHander implements InvocationHandler {
    private Object beProxy;
    private ForeignLanguage myForeignLanguage;
    public CokeProxyHander(Object beProxy,ForeignLanguage myForeignLanguage) {
        this.beProxy = beProxy;
        this.myForeignLanguage=myForeignLanguage;
    }

    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        System.out.println("我是Coke,不仅会");
        Object returned= method.invoke(beProxy,args);
        System.out.println("********参数内容**********");
        Arrays.stream(args).forEach(s-> System.out.println(s));
        System.out.println("*************************");
        myForeignLanguage.speak((String) args[0]);
        return null;
    }
}

		- 调用方法中，使用Java动态代理，动态地创建代理对象，实现代理
使用Proxy.newProxyInstance(ClassLoader,Class[],代理类)
生成的对象为被代理类的对象可以使用类型转换为被代理类对象（就好像无事发生，正常生成了对象一样，只不过已经被掉包）

			- public class ProxyMain {
    public static void doTest(SayChinese chinese) {
        chinese.speakChinese("coke", "中国话");
    }

    public static void main(String[] args) {
        Chinese chinese =new Chinese();
        SayChinese c=(SayChinese) Proxy.newProxyInstance(SayChinese.class.getClassLoader(),new Class[]{SayChinese.class},new CokeProxyHander(chinese,new EnglishForeignLanguageImpl()));
        doTest(c);
    }
}


	- 可以实现事务，成功就提交，失败则回滚

## 垃圾回收与内存管理

### 内存清理、分配方式

- 垃圾回收器能回收堆上的对象，即所有用Java new来申请的内存空间
- Java只能使用new来为对象分配内存空间
- 内存空间使用堆栈管理，分配内存只需要堆指针移动，速度快
- 在垃圾清理的同时会帮助整理内存，让内存连续
- 垃圾回收的方法

	- 停止-复制
	- 标记-扫描

### finalize()方法

- 用于回收内存，一般是其他语言申请的内存
- 用于做“临终”

	- 如绘图类，清除画板

- 执行步骤

	- 在Java进行标记扫描时，先扫描一次，选出“死”类，然后扫描第二次，将有finalize()方法的类放入F-Queue队列
	- Java虚拟机保证finalize方法的执行，但不保证完成

## 泛型JavaSE5

### 简单泛型

- 告诉编译器想使用什么类型，编译器帮你处理一切细节
- 类型后加一个<>里面放大写英文字母，代表传入的类
- 元组类库

	- 元组

		- 将一组对象直接打包存储于其中的一个单一对象

	- 利用泛型实现

		- public class TwoTuple<A,B> {
      public final A frist;
      public final B second;
      public TwoTuple(A a,B b){

- 堆栈类

	- List<T>

### 泛型接口

- 生成器：工厂方法设计模式的一种应用
- interface name<T>

### 泛型方法

- 泛型方法不依赖泛型类，可以给方法单独泛型
- 使用泛型方法>使用泛型类
- 泛型参数列表置于返回值之前
- public <T> void f(T x)
- 传入基本类型会触发自动打包
- 泛型类可以根据参数指定泛型类型
- 可以显式指定泛型类型
- 可以用泛型与可变参数列表

### 匿名内部类

- 可以用于内部类以及匿名内部类

### 擦除

- 可以声明ArrayList.class 但是不能声明 ArrayList<Integer>.class
- 在泛型代码内部，无法获得任何有关泛型参数类型的信息
- 使用泛型时，任何具体的类型信息都被擦除，唯一得知的是在使用一个对象。List<String>和List<Integer>在运行时是相同的类型
- 泛型类型将擦除到它的第一个边界

	- <T extends Ha>则可以使用Ha类的方法

- 泛型不能运用于显式地引用运行时类型的操作之中，因为所有关于参数的类型信息丢失

	- 转型
	- instanceof
	- new

### 擦除的补偿

- 类型缺失

	- 引入Class<T>
	- 初始化同时也初始化一下Class<T>就能利用该属性进行类型操作，使用动态的isInstance

- 泛型数组

	- 不能创建泛型数组
	- 可以使用ArrayList

### 边界

- 使在用于泛型参数类型上设置限制条件
- （潜在）允许你调用边界类型的方法
- <T extends YourClass>

### 通配符

- 任何的***的类
- <? extends Aa>
- 超类型通配符

	- <? super MyClass>
	- <? super T>

- 无界通配符

	- <?>

### 自限定类型

### 动态类型安全

### 异常

### 混型

### 潜在类型机制

## JavaI/O

### File

- 代表一个特定的文件的名称
- 代表一个目录下的一组文件的名称

	- list方法

- 过滤文件

	- 使用FilenameFilter接口，策略模式

### Java IO的架构

- 通过叠加多个对象来提供更有用的接口
- 装饰器设计模式
- 创建单一的结构流，需要创建多个对象

### 输入输出

- 输入
含read()方法

	- Inputstream

		- 表示从不同数据源产生输入的类

			- 字节数组
			- String对象
			- 文件
			- 管道
			- 流
			- 其他数据源，如Internet连接

		- ByteArrayInputStream

			- 允许将内存内的缓冲区当做InputStream使用
			- 如何使用

				- 缓存区，字节从中取出
				- 作为一种数据源：将其与FilterInputStream对象相连以提供有用接口

		- StringBufferInputStream

			- 将String转换成InputStream
			- 如何使用

				- 字符串。底层实现实际使用StringBuffer
				- 作为一种数据源：将其与FilterInputStream对象相连以提供有用接口

		- FileInputStream

			- 用于从文件中读取信息
			- 如何使用

				- 字符串，表示文件名、文件或FileDescriptior对象
				- 作为一种数据源：将其与FilterInputStream对象相连以提供有用接口

		- PipedInputStream

			- 产生用于写入相关PipedOutputStream的数据。实现“管道化”的概念
			- 如何使用

				- PipedOutputStream
				- 作为多线程中数据源：将其与FilterInputStream对象相连以提供有用接口

		- SequenceInputStream

			- 将两个或多个InputStream对象转换成单一InputStream
			- 如何使用

				- 两个InputStream对象或一个容纳InputStream对象的容器Enumeration
				- 作为一种数据源：将其与FilterInputStream对象相连以提供有用接口

		- FilterInputStream

			- 抽象类，作为“装饰器”的接口。控制特定输入流
			- DataInputStream

				- 与DataOutputStream搭配使用，因此我们可以按照可移植方式从流读取基本数据类型(int,char,long等等)
				- 如何使用

					- InputStream
					- 包含用于读取基本类型的数据的全部接口

			- BufferedInputStream

				- 使用它可以防止每次读取时都得进行实际写操作。代表“使用缓冲区”
				- 如何使用

					- InputStream，可以指定缓冲区大小
					- 本质上不提供接口，只不过是向进程中添加缓冲区所必需的。与接口对象搭配

			- LineNumberInputStream

				- 跟踪输入流中的行号；可以调用getLineNumber()和setLineNumber(int)
				- 如何使用

					- InputStream
					- 仅增加了行号，因此可能要与接口对象搭配使用

			- PushbackInputStream

				- 具有“能弹出一个字节的缓冲区”。因此可以将读到的最后一个字符回退
				- 如何使用

					- InputStream
					- 通常作为编译器的扫描器，之所以包含在内是因为Java编译器的需要，我们可能永远用不到

	- Reader

		- 提供兼容Unicode与面向字符的IO功能
		- 利用适配器InputStreamReader可以将InputStream转换为Reader

- 输出
含write()方法

	- OutputStream

		- 该类决定了输出所有要去往的目标
		- ByteArrayOutputStream

			- 在内存汇总创建缓存区。所有送往“流”的数据都要放置在此缓存区
			- 如何使用

				- 缓存区，字节从中取出
				- 作为一种数据源：将其与FilterOutputStream对象相连以提供有用接口

		- FileOutputStream

			- 将信息写至文件
			- 如何使用

				- 字符串，表示文件名、文件或FileDescriptior对象
				- 作为一种数据源：将其与FilterOutputStream对象相连以提供有用接口

		- PipedOutputStream

			- 产生用于写入其中的信息都会自动作为相关PipedInputStream的输出，实现“管道化”的概念
			- 如何使用

				- PipedInputStream
				- 作为多线程中的数据的目的地：将其与FilterOutputStream对象相连以提供有用接口

		- FilterOutputStream

			- 抽象类，作为“装饰器”的接口。
			- DataOutputStream

				- 与DataInputStream搭配使用，因此我们可以按照可移植方式从流写入基本数据类型(int,char,long等等)
				- 如何使用

					- OutputStream
					- 包含用于写入基本类型的数据的全部接口

			- PrintStream

				- 用于产生格式化输出。其中DataOutputStream处理数据的存储，PrintSteam处理显示
				- 如何使用

					- OutputStream，可以用boolean值指示是否在每次换行时清空缓冲区（可选）应该是对OutputStream对象的final封装，可能经常使用

			- BufferedInputStream

				- 使用它可以避免每次发送数据时都得进行实际写操作。代表“使用缓冲区”。可以调用flush()清空缓冲区
				- 如何使用

					- OutputStream，可以指定缓冲区大小
					- 本质上不提供接口，只不过是向进程中添加缓冲区所必需的。与接口对象搭配

	- Writer

		- 提供兼容Unicode与面向字符的IO功能
		- 利用适配器OutputStreamReader可以将OutputStream转换为Writer

- JavaSE5 PrintWriter

	- 简化将输出写入时的文件创建过程
	- 可以接受一个OutputStream作为参数的构造器

- RandomAccessFile

	- 适用于由大小已知的记录组成的文件
	- 使用seek()将记录从一处转移到另一处，然后读取或者修改记录
	- 支持搜寻方法
	- JDK1.4大多数功能被nio存储映射文件所取代

### 标准IO

- 从标准输入中读取

	- System.in

		- 为被包装的InputStream

	- System.out

		- 被事先包装为printStream对象
		- 可以包装为PrintStream等等

	- System.err

		- 被事先包装为printStream对象

- 标准IO重定向

	- System类提供了一些简单的方法来重定向
	- setIn(InputStream)
	- setOut(PrintStream)
	- setErr(PrintStream)

### 进程控制

- 背景

	- 在Java内部执行其他操作系统的程序，并且要控制这些程序的输入和输出

- Process

	- 代表一个进程

- java.lang.ProcessBuilder

	- 用于创建操作系统进程

- Process提供了输入流，可以用来获取进程信息流

### JDK1.4 新IO,NIO

- 目的

	- 提高速度
	- 将旧IO使用nio重新实现了

- 原理

	- 更接近于操作系统执行IO的方式

		- 通道
		- 缓冲器

- 唯一与通道交互的对象

	- ByteBuffer

		- 需要设置缓冲区大小

- 修改类库，生产FileChannel

	- FileInputStream
	- FileOutputStream
	- RamdomAccesssFile
	- Reader&Writer面向字符，不能产生通道

		- java.nio.channels.Channels提供了实用的方法，用以产生Writer&Reader

- 使用方法

  FileChannel fc=new FileOutputStream("./test.md").getChannel();
  fc.write(ByteBuffer.wrap("Something".getBytes()));
  fc.close();
  fc = new RandomAccessFile("test.md", "rw").getChannel();
  fc.position(fc.size());
  fc.write(ByteBuffer.wrap("Random".getBytes()));
  fc.close();
  fc = new FileInputStream("test.md").getChannel();
  ByteBuffer bf = ByteBuffer.allocate(BSIZE);
  fc.read(bf);
  bf.flip();
  while (bf.hasRemaining()) {
      System.out.print((char) bf.get());
  }

	- 写

		- 创建通道FileChannel，利用你要做的类型，创建通道，比如利用FileInputStream获得channel
		- 通道提供了读写接口，
		- 需要使用ByteBuffer做中间商，利用wrap接口可以将字符串写入
		- 写入的是字节，所以字符串要装换为字节

	- 读

		- 写出需要先设定ByteBuffer的大小
		- 将通道数据读入ByteBuffer
		- Buffer使用flip接口，让它做别人读取字节的准备

	- 通道直接对接

		- transferTo
		- transferFrom

- 编码工具

	- java.nio.charset.Charset

		- 编码
		- 解码

- 获取基本类型

	- ByteBuffer装换缓冲类型

		- asCharBuffer
		- ....

	- 然后进行get与put

- 视图缓冲器

	- IntBuffer
	- CharBuffer
	- 利用ByteBuffer.asXXXBuffer生成
	- get与put操作与原生效果相同

-  

### 压缩

- GZIP
- ZIP
- Checked

	- 产生校验和压缩的基类

### 序列化

- 实现Serializable接口

	- 一个标记接口，不包括任何方法

- 使用writeObject即可
- 必须保证虚拟机下有该类的类对象.class文件
- 在序列化时进行控制

	- 使用Externalizable接口
	- 使用Serializable接口，添加writeObject，readObject方法

- 关键字transient（瞬时）关键字

	- 关闭在该属性上的序列化

### XML

- javax.xml.*类库
- Element类

### Preferences

- 用于存储和读取用户的偏好以及程序配置项的设置
- 键值对集合

## 设计模式（不全面）

### 单例设计模式

- 通过静态实例对象，将构造方法禁用（private），然后单独设置一个返回该对象的方法

### 策略设计模式

- 利用继承与多态，预设不同的继承类（如大小写装换，预设转大写的子类，转小写的子类）调用方法设置两个参数，一个参数选择策略，一个参数放待处理内容

### 适配器模式

-  适配器模式将某个类的接口转换成客户端期望的另一个接口表示，目的是消除由于接口不匹配所造成的类的兼容性问题。主要分为三类：类的适配器模式、对象的适配器模式、接口的适配器模式。
- 著名的设计模式“四人帮”这样评价适配器模式： 将一个类的接口转换成客户希望的另外一个接口。Adapter 模式使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。——Gang of Four
- 将一个类的接口适配成用户所期待的
- Adapter 设计模式主要目的组合两个不相干类，常用有两种方法

	- 第一种解决方案是修改各自类的接口
	- 如果没有源码，或者不愿意为了一个应用而修改各自的接口，则需要使用 Adapter 适配器，在两种接口之间创建一个混合接口。

		- 

### 工厂模式

- 创建工厂类，可以生产需要的方法
- 多用于框架

## 枚举类型JavaSE5

### 应用场景

- 定义的静态名称等
- 枚举类型

### 特性

- 有限实例化
- 更符合对枚举类型的需要
- 使用enum定义的类，编译器会为你生成一个相关的类，继承Enum

	- java.lang.Enum

		- Comparable<E>
		- Serializable

- 可以实现接口
- 不可被继承
- 与普通类没什么不同
- 可以用在switch

### 使用

- enum关键字
- 请注意，当使用枚举类型作为集合的类型或映射中的键的类型时，可以使用专门且高效的set和map实现。 
- 随机选取random

### EnumSet、EnumMap

### 常量相关方法

- enum允许程序员为enum实例编写方法，从而为每个实例赋予各自不同的行为。
- 可以在Enum类中编写抽象方法，实例实现方法
- 可以直接在Enum中编写方法，作为基类方法

### Enum与Enum实例的关系

- Enum类似实例的超类

## JavaSE5 注解

### 简述

- 也称元数据
- 为我们在代码中添加信息提供了一种形式化的方法，使我们可以在稍后某个时刻非常方便地使用这些数据
- 将元数据与源代码文件结合

### java.lang中内置注解

- @Override

	- 表示将覆盖超类方法

- @Deprecated

	- 表示废弃的，编译器将发出警告

- @SuppressWarnings

	- 关闭不当的编译器警告信息，在JavaSE5之前可以添加，但是无效果

- 元注解
另外四种元注解，负责新注解的创建

	- @Target

	  @Documented
	  @Retention(RetentionPolicy.RUNTIME)
	  @Target(ElementType.ANNOTATION_TYPE)
	  public @interface Target {
	      /**
	       * Returns an array of the kinds of elements an annotation type
	       * can be applied to.
	       * @return an array of the kinds of elements an annotation type
	       * can be applied to
	       */
	      ElementType[] value();
	  }

		- 需要ElementType枚举类实例数组

		  /*
		   * Copyright (c) 2003, 2013, Oracle and/or its affiliates. All rights reserved.
		   * ORACLE PROPRIETARY/CONFIDENTIAL. Use is subject to license terms.
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   *
		   */
		  
		  package java.lang.annotation;
		  
		  /**
		   * The constants of this enumerated type provide a simple classification of the
		   * syntactic locations where annotations may appear in a Java program. These
		   * constants are used in {@link Target java.lang.annotation.Target}
		   * meta-annotations to specify where it is legal to write annotations of a
		   * given type.
		   *
		   * <p>The syntactic locations where annotations may appear are split into
		   * <em>declaration contexts</em> , where annotations apply to declarations, and
		   * <em>type contexts</em> , where annotations apply to types used in
		   * declarations and expressions.
		   *
		   * <p>The constants {@link #ANNOTATION_TYPE} , {@link #CONSTRUCTOR} , {@link
		   * #FIELD} , {@link #LOCAL_VARIABLE} , {@link #METHOD} , {@link #PACKAGE} ,
		   * {@link #PARAMETER} , {@link #TYPE} , and {@link #TYPE_PARAMETER} correspond
		   * to the declaration contexts in JLS 9.6.4.1.
		   *
		   * <p>For example, an annotation whose type is meta-annotated with
		   * {@code @Target(ElementType.FIELD)} may only be written as a modifier for a
		   * field declaration.
		   *
		   * <p>The constant {@link #TYPE_USE} corresponds to the 15 type contexts in JLS
		   * 4.11, as well as to two declaration contexts: type declarations (including
		   * annotation type declarations) and type parameter declarations.
		   *
		   * <p>For example, an annotation whose type is meta-annotated with
		   * {@code @Target(ElementType.TYPE_USE)} may be written on the type of a field
		   * (or within the type of the field, if it is a nested, parameterized, or array
		   * type), and may also appear as a modifier for, say, a class declaration.
		   *
		   * <p>The {@code TYPE_USE} constant includes type declarations and type
		   * parameter declarations as a convenience for designers of type checkers which
		   * give semantics to annotation types. For example, if the annotation type
		   * {@code NonNull} is meta-annotated with
		   * {@code @Target(ElementType.TYPE_USE)}, then {@code @NonNull}
		   * {@code class C {...}} could be treated by a type checker as indicating that
		   * all variables of class {@code C} are non-null, while still allowing
		   * variables of other classes to be non-null or not non-null based on whether
		   * {@code @NonNull} appears at the variable's declaration.
		   *
		   * @author  Joshua Bloch
		   * @since 1.5
		   * @jls 9.6.4.1 @Target
		   * @jls 4.1 The Kinds of Types and Values
		   */
		  public enum ElementType {
		      /** Class, interface (including annotation type), or enum declaration */
		      TYPE,
		  
		      /** Field declaration (includes enum constants) */
		      FIELD,
		  
		      /** Method declaration */
		      METHOD,
		  
		      /** Formal parameter declaration */
		      PARAMETER,
		  
		      /** Constructor declaration */
		      CONSTRUCTOR,
		  
		      /** Local variable declaration */
		      LOCAL_VARIABLE,
		  
		      /** Annotation type declaration */
		      ANNOTATION_TYPE,
		  
		      /** Package declaration */
		      PACKAGE,
		  
		      /**
		       * Type parameter declaration
		       *
		       * @since 1.8
		       */
		      TYPE_PARAMETER,
		  
		      /**
		       * Use of a type
		       *
		       * @since 1.8
		       */
		      TYPE_USE
		  }

			- Type

				- Class, interface (including annotation type), or enum declaration
注解在类上

			- FIELD

				- Field declaration (includes enum constants)
注解在属性上，包括enum的常量

			- METHOD

				- Method declaration
方法

			- PARAMETER

				- Formal parameter declaration
形式参数声明

			- CONSTRUCTOR

				- Constructor declaration
构造函数

			- LOCAL_VARIABLE

				- Local variable declaration
局部变量声明

			- ANNOTATION_TYPE

				- Annotation type declaration
注解在注解上

			- PACKAGE

				- Package declaration
包

			- TYPE_PARAMETER

				- Type parameter declaration
JavaSE8类型参数说明（用在泛型）

			- TYPE_USE

				- Use of a type
JavaSE8使用类型（所有的类型都能标注）

	- @Retention

	  @Documented
	  @Retention(RetentionPolicy.RUNTIME)
	  @Target(ElementType.ANNOTATION_TYPE)
	  public @interface Retention {
	      /**
	       * Returns the retention policy.
	       * @return the retention policy
	       */
	      RetentionPolicy value();
	  }

		- 定义该注解在哪一个级别可用

			- SOURCE

				- 源代码中

			- CLASS

				- 类文件中

			- RUNTIME

				- 运行时

	- @Document

		- 将此注解包含在Javadoc中

	- @Inherited

		- 允许子类继承父类注解

### 基础语法

- 定义

	- 类似接口，会被编译为class文件
	- 没有元素的注解称为标记注解
	- @Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Test {
    String value();
    public String name() default "JJ";
}
	- 元注解
	- 定义元素

		- 类似方法
		- 使用default关键字可以在没有给出值的时候使用默认值

- 使用

	- @Test(value = "AA",name = "Jir")
    public String get() {
        return "Mm";
    }
}
	- 直接注解在方法，类，属性上就行

- 注解元素

	- 注解只能使用下面的类型

		- 所有基本类型
		- String
		- Class
		- enum
		- Annotation
		- 以上类型的数组

- 默认值

	- 元素的值必须是确定的

		- 使用注解时提供的值
		- 默认值

	- 元素不可为空

		- 声明注解
		- 定义注解

- 注解不支持继承

	- 不能使用extends

### 编写注解处理器

- 基本原理

	- 反射

- JavaSE5工具类

  Test t=method.getAnnotation(Test.class);
  System.out.println("方法"+method.getModifiers()+" "+method.getGenericReturnType()+" "+method.getName()+"("+ Arrays.toString(method.getParameters())+")");
  if(t!=null){
      System.out.println("存在注解");
      System.out.println(t.name()+t.value());
  }else {
      System.out.println("不存在注解");
  }

	- method.getAnnotation()
	- AnnotatedElement接口
	- getAnnotations
	- getDeclaredAnnotations

### apt

- 注解处理工具：apt
- APT即为Annotation Processing Tool，它是javac的一个工具，中文意思为编译时注解处理器。APT可以用来在编译时扫描和处理注解。通过APT可以获取到注解和被注解对象的相关信息，在拿到这些信息后我们可以根据需求来自动的生成一些代码，省去了手动编写。

### 单元测试

- JUnit

## 并发

### 并发概念

- 为什么要并发

	- 提高单处理器上的程序性能
	- 顺序现代处理器多核的模式
	- 产生具有可响应的用户界面

- 阻塞

	- 该程序控制范围之外的某些条件（通常是I/O）而导致不能继续执行

- 实现并发的方式

	- 系统级别使用进程

		- 进程：运行在它自己的地址空间内的自包容程序。多任务操作系统可以通过周期性地将CPU从一个进程切换到另一个进程，来实现同时运行多个进程。
		- 操作系统通常会将进程隔离，进程彼此不会互相干涉

	- Java实现

		- 在顺序性语言的基础上提供对线程的支持

- 多线程最基本的困难

	- 协调不同线程驱动的任务之间对这些资源的使用

- 函数型语言

	- 每个函数都不会产生任何副作用（并因此不能干涉其他函数）
	- 可以作为独立的任务来驱动

### 线程、进程、程序

- 线程

	- 在进程中的一个单一的顺序控制流
	- 单个进程可以拥有多个并发执行的任务

- 进程

	- 运行在它自己的地址空间内的自包容程序。多任务操作系统可以通过周期性地将CPU从一个进程切换到另一个进程，来实现同时运行多个进程。
	- 拥有多个线程

- 程序

	- 特定的一系列动作、行动或操作，而这些活动、动作或操作必须以相同方式执行，借此在相同环境下恒常得出相同的结果（例如紧急应变程序）。
	- 粗略而言，程序可以指一序列的活动、作业、步骤、决断、计算和工序，当它们保证依照严格规定的顺序发生时即产生所述的后果、产品或局面。
	- 一个程序通常引致一个改变。 

### 多线程

- 定义任务

	- 实现Runnable接口，编写run方法

		- 一个只有一个方法的接口，可以使用Lambda

	- run通常有某种形式的循环，使得任务一直运行下去直到不再需要，通常被成无限循环的方式
	- Thread.yield()

		- 静态方法，在run中调用
		- 对线程调度器的一种建议

			- 线程调度器

				- Java线程机制的一部分，可以将CPU从一个线程转移给另一个线程

		- 声明“我已经执行完生命周期中最重要的部分了，此刻正是切换给其他任务执行一段时间的大好时机”
		- 将线程让出，然后调度器再次随机分配，注意这里只是让出，下一次分配给谁不能得知，也有可能被再次分配

	- run方法

		- 执行run方法并没有另外开启线程，只是简单执行在main中

- Thread

	- 作用

		- 将Runnable对象转变为工作任务

	- 使用方式

		- 将Runnable对象提交给构造器
		- 使用Thread.start方法开启另一个线程

	- 多线程执行的实际情况

		- 不同线程交替执行

	- 线程的几种状态

		- 新建

			- 当一个Thread类或其子类的对象被声明并创建时，新生的线程对象处于新建 状态 

		- 就绪

			- 处于新建状态的线程被start()后，将进入线程队列等待CPU时间片，此时它已 具备了运行的条件，只是没分配到CPU资源 

		- 运行

			- 当就绪的线程被调度并获得CPU资源时,便进入运行状态， run()方法定义了线 程的操作和功能 

		- 阻塞

			- 在某种特殊情况下，被人为挂起或执行输入输出操作时，让出 CPU 并临时中 止自己的执行，进入阻塞状态

		- 死亡

			- 线程完成了它的全部工作或线程被提前强制性地中止或出现异常导致结束

	- 生命周期

		- 
		- 

- jdk1.5新增创建线程方式

	- java.util.concurrent.Executor

		- 线程池。管理Thread对象
		- 管理异步任务的执行，无需显示管理线程生命周期
		- 工具类、线程池的工厂类
		- ExecutorService

			- 暴露要执行的单一方法
			- 使用Executor的静态方法获得
			- 在可能的情况下，线程池都会自动复用线程
			- 真正的线程池接口
			- 实例，使用Executor.newXXX

				- CachedThreadPool

					- 在程序执行过程中通常会创建与所需数量相同的线程
					- 回收旧线程时停止创建新线程
					- 合理的Executor的首选

				- FixedThreadPool

					- 预先分配线程所需资源
					- 直接从池中获得资源
					- 固定的线程数量

				- SingleThreadExecutor

					- 线程数量为1的FixedThreadPool

				- ScheduledThreadPool

					- 可安排在给定延迟后运 行命令或者定期地执行。

	- 从任务中产生返回值

		- 实现Callable<T>接口代替Runnable接口
		- 重写<T> call方法
		- 必须使用ExecutorService.submit()方法调用

- 休眠

	- 简单方法

		- 调用sleep()方法，参数为休眠时间，毫秒

	- JavaSE5新方法

		- TimeUnit.MILLISECONDS.sleep(int time)
		- 使用TimeUnit类，提供多种休眠的时间单位

- 优先级

	- 表示线程的重要性，只能影响调度器调用线程的概率！！

		- 较低优先级的线程有机会执行

	- 绝大多数情况下，线程应该以默认的优先级运行，试图操作优先级通常是一种错误
	- 使用getPriority()读取优先级
	- 在任何时刻使用setPriority()修改

		- JDK有10个优先级，但与多数操作系统不能很好映射
		- 在调整优先级的时候使用

			- MAX_PRIORITY
			- NORM_PRIORITY
			- MIN_PRIORITY

- 让步

	- 完成大多数功能后，让出CPU的使用权
	- 调用yield方法

- 守护线程

	- 后台线程，指在程序运行时在后台提供通用服务的线程，并且这种线程并不属于程序中不可或缺的部分。
	- 当所有非后台线程结束时，程序也就终止了，会杀死进程中所有的后台线程
	- 必须在线程启动前调用setDaemon()方法
	- isDaemon确定是否为守护线程

- 加入线程join

	- 调用另一个线程的join方法，将等待另一个线程的执行
	- 挂起本线程，直到另一个线程的isAlive为假

- 线程组

	- 别用，失败设计就行

- JavaSE5 捕捉异常

	- 无法在主类中使用try捕捉线程的异常
	- 使用Executor解决这个问题

		- 实现UncaughtExceptionHandler接口，可以将接口实现类设置给线程对象
		- 修改Executor产生线程的方式，实现ThreadFactory接口，以此添加Executor在生产线程时的操作，即利用异常处理类，对线程异常进行捕捉
		- 新建Executor线程池时，添加线程工厂类

### 共享受限资源

- 问题

	- 多个线程在使用同一个资源时，很可能出现与预估情况差距很大的结果

		- 线程1在写数据的一半，线程2也开始对数据的修改，导致数据异常
		- 线程1读取数据后，线程2对数据做了修改，数据出现异常
		- ...

	- 当多条语句在操作同一个线程共享数据时，一个线程对多条语句只执行了一部分，还没有 执行完，另一个线程参与进来执行。导致共享数据的错误。 

- 问题解决方法

	- 对多条操作共享数据的语句，只能让一个线程都执行完，在执行过程中，其他线程不可以 参与执行。

		- “锁”

- 同步

	- Synchronized

		-  Java对于多线程的安全问题提供了专业的解决方式：同步机制
		- 使用

			- 同步代码块

				- synchronized (对象){ 
     // 需要被同步的代码； 
}
				- 参数对象作为锁使用，多个线程使用一把锁必须保证是同一个对象！

			- 方法声明

				- public synchronized void show (String name){ …. }
				- 一个线程类中的所有静态方法共用同一把锁（类名.class），所有非静态方 法共用同一把锁（this）

		- 原理

			- 对对象的放问进行控制，
			- 给区域上锁，使用该区域需要申请
			- 已经被上锁，则不能访问

		- 缺陷

			- Synchronized锁需要访问操作系统，获得锁，过于“重”

		- 释放锁

			- 当前线程的同步方法、同步代码块执行结束。 
			- 当前线程在同步代码块、同步方法中遇到break、return终止了该代码块、 该方法的继续执行。 
			- 当前线程在同步代码块、同步方法中出现了未处理的Error或Exception，导 致异常结束。 
			-  当前线程在同步代码块、同步方法中执行了线程对象的wait()方法，当前线 程暂停，并释放锁。

		- 不能释放锁的操作

			- 线程执行同步代码块或同步方法时，程序调用Thread.sleep()、 Thread.yield()方法暂停当前线程的执行
			- 线程执行同步代码块时，其他线程调用了该线程的suspend()方法将该线程 挂起，该线程不会释放锁（同步监视器）。 应尽量避免使用suspend()和resume()来控制线程

		- 对单例设计模式的改进

			- 旧版本

				- 获取实例时，若没有就new
				- 问题：多个线程同时获取实例，同时进行了new，导致数据不一致

			- 加“锁”改进

				- 对生成操作进行加锁，保证只有一个线程能生成对象
				- 细节问题：

					- 只对new进行加锁的情况下

						- 问题描述

							- 线程1和2同时发现没有实例，准备进行new
							- 线程1获得锁，执行new，线程2等待
							- 线程2获得锁，又一次执行了new，发生数据不一致

						- 解决方式

						  class Singleton { 
						  	private static Singleton instance = null; 
						  	private Singleton(){} 
						  	public static Singleton getInstance(){ 
						  		if(instance==null){ 
						  			synchronized(Singleton.class){ 
						  				if(instance == null){ 
						  					instance=new Singleton();
						  				 }
						  			 } 
						  		} 
						  		return instance; 
						  	} 
						  }

							- 在获取锁后，再一次对对象为空进行验证，避免多次修改

					- 锁使用synchronized太“重”

						- 使用CAS轻量级锁

	- 线程死锁

		- 不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃 自己需要的同步资源，就形成了线程的死锁 
		- 出现死锁后，不会出现异常，不会出现提示，只是所有的线程都处于 阻塞状态，无法继续 
		- 解决方法

			- 专门的算法、原则 
			- 尽量减少同步资源的定义
			-  尽量避免嵌套同步

	- JavaSE5 Lock（锁）

		- 更强大的线程同步机制，通过显式定义同 步锁对象来实现同步。同步锁使用Lock对象充当。

			- 使用lock和unlock手动进行解锁与上锁

		- java.util.concurrent.locks.Lock接口是控制多个线程对共享资源进行访问的 工具

			- 锁提供了对共享资源的独占访问，每次只能有一个线程对Lock对象 加锁，线程开始访问共享资源之前应先获得Lock对象。


		- ReentrantLock

		  class A{
		  private final ReentrantLock lock = new ReenTrantLock(); public void m(){ lock.lock(); try{ //保证线程安全的代码; } finally{ lock.unlock(); } }
		  }

			- 实现了 Lock 
			- 拥有与 synchronized 相同的并发性和 内存语义，在实现线程安全的控制中，比较常用的是ReentrantLock，可以 显式加锁、释放锁。
			- 如果同步代码有异常，要将unlock()写入finally语句块

		- synchronized 与 Lock 的对比

			- Lock是显式锁（手动开启和关闭锁，别忘记关闭锁），synchronized是 隐式锁，出了作用域自动释放
			- Lock只有代码块锁，synchronized有代码块锁和方法锁
			- 使用Lock锁，JVM将花费较少的时间来调度线程，性能更好。并且具有 更好的扩展性（提供更多的子类）
			- 优先使用顺序： Lock 》同步代码块（已经进入了方法体，分配了相应资源） 》 同步方法 （在方法体之外）

	- 轻量锁

		- CAS

### 线程协作

- wait() 与 notify() 和 notifyAll()

	- wait()

		- 在当前线程中调用方法： 对象名.wait() 
		- 使当前线程进入等待（某对象）状态 ，直到另一线程对该对象发出 notify (或notifyAll) 为止。 
		- 调用方法的必要条件：当前线程必须具有对该对象的监控权（加锁） 
		- 调用此方法后，当前线程将释放对象监控权 ，然后进入等待 
		- 在当前线程被notify后，要重新获得监控权，然后从断点处继续代码的执行。

	- notify()

		- 唤醒正在排队等待同步资源的线程中优先级最高者结束等待 
		- 在当前线程中调用方法： 对象名.notify()
		- 调用方法的必要条件：当前线程必须具有对该对象的监控权（加锁）

	- notifyAll()

		- 唤醒正在排队等待资源的所有线程结束等待.

	- 这三个方法只有在synchronized方法或synchronized代码块中才能使用，否则会报 java.lang.IllegalMonitorStateException异常
	- 因为这三个方法必须有锁对象调用，而任意对象都可以作为synchronized的同步锁。 因此在Object类中声明这三个方法。

### 死锁问题

- 两个线程互相占了对方的资源，导致死锁

### 性能调优

## 包装类

### 目的

- Java是纯面向对象的语言，在一些情况下，基础的类型无法用于方法等等的情况，让基础类型拥有对应的类
- 基础数据类型有了对象的特性
- 重写了toString，提供了大量便捷的构造方法
- 提供大量的转化类型的方法

### 类型

- Byte
- Short
- Integer
- Long
- Float
- Double
- Boolean
- Character

## Java常用类以及util包

### String

### StringBuffer、StringBuilder

### Date

## （新增）JavaSE8 的新特性

### 并行API
优秀的多任务处理

- 并行数组处理

	- 允许程序员使用多核体系结构的Lambda表达式对数组的元素进行排序、过滤、分组等操作
	- 多核对数组排序

		- Arrays.parallelSort(numbers); 

	-  根据特定的条件（比如：素数和非素数）对数组进行分组

		- Map<Boolean, List<Integer>> groupByPrimary = numbers.parallelStream().collect(Collectors.groupingBy(s -> Utility.isPrime(s))); 

	- 对数组进行过滤

		- Integer[]  prims = numbers.parallelStream().filter(s -> Utility.isPrime(s))     .toArray();

### 函数式接口

- What

	- 只包含一个抽象方法的接口，称为函数式接口
	- 你可以通过 Lambda 表达式来创建该接口的对象。（若 Lambda 表达式 抛出一个受检异常(即：非运行时异常)，那么该异常需要在目标接口的抽 象方法上进行声明）。 
	- @FunctionalInterface 

		- 在一个接口上使用 @FunctionalInterface 注解，这样做可以检 查它是否是一个函数式接口。同时 javadoc 也会包含一条声明，说明这个 接口是一个函数式接口。 

	- java.util.function包下定义了Java 8 的丰富的函数式接口
	- OOF（面向函数编程）

		- Java是面向对象的，方法必须依托对象
		- OOF中，函数与对象有一样的地位

	- Java如何支撑OOF

		- 让函数成为一个接口，相当于利用接口提升函数的地位
		- 所以以前用匿名实现类表示的现在都可以用Lambda表达式来写。

	- Lambda作为参数

		- 接收接口类就行

	- Java内置函数式接口

		- 

### lambda表达式

- Lambda 是一个匿名函数，我们可以把Lambda 表达式理解为是一段可以
传递的代码（将代码像数据一样进行传递）。使用它可以写出更简洁、更 灵活的代码。作为一种更紧凑的代码风格，使Java的语言表达能力得到了提升。
- 
- 
- ->操作符

	- Lambda 操作符 或箭头操作符
	- 将 Lambda 分为两个部分：

		- 左侧：指定了 Lambda 表达式需要的参数列表
		- 右侧：指定了 Lambda 体，是抽象方法的实现逻辑，也即 Lambda 表达式要执行的功能。

- 语法格式

	- 1.无参，无返回值

		- Runnable r=  ()-> {System.out.println();}

	- 2.一个参数，无返回值

		- Consumer<String> c = (String name)->{ System.out.println(name);}

	- 3.(改进2)数据类型可省略，由编译器类型推断得出

		- Consumer<String> c = (name)->{ System.out.println(name);}

	- 4.(改进3)只有一个参数时，可以省略小括号

		- Consumer<String> c =  name->{ System.out.println(name);}

	- 5.（扩展3）多参数，多条语句，有返回值

		- Conparator<Integer> c = (x,y)->{ 
    System.out.println(x+""+y);
    return Integer.compare(x,y);
}

	- 6.（改进4）Lambda只有一条语句，省略大括号与return

		- Conparator<Integer> c = (x,y)-> Integer.compare(x,y);

- 类型推断

	- Javac根据程序上下文，自动推断类型

### 方法引用，构造器引用

- 当要传递给Lambda体的操作，已经有实现的方法了，可以使用方法引用！ 
- 方法引用可以看做是Lambda表达式深层次的表达。换句话说，方法引用就 是Lambda表达式，也就是函数式接口的一个实例，通过方法的名字来指向 一个方法，可以认为是Lambda表达式的一个语法糖。
- 要求：实现接口的抽象方法的参数列表和返回值类型，必须与方法引用的 方法的参数列表和返回值类型保持一致！
- 格式：使用操作符 “::” 将类(或对象) 与 方法名分隔开来。
- 概述

	- 将函数表达式接口作为变量，值为其他类中已经实现好的方法

- 三种主要使用情况： 

	-  对象::实例方法名 
	-  类::静态方法名 
	-  类::实例方法名

- 
- 
- 

### Stream API

- 简介

	- Java8带来重要功能之一，另一个是Lambda
	- 把真正的函数式编程风格引入到Java中。这 是目前为止对Java类库最好的补充，因为Stream API可以极大提供Java程 序员的生产力，让程序员写出高效率、干净、简洁的代码。
	-  Stream 是 Java8 中处理集合的关键抽象概念，它可以指定你希望对集合进 行的操作，可以执行非常复杂的查找、过滤和映射数据等操作。 
	- 使用 Stream API 对集合数据进行操作，就类似于使用 SQL 执行的数据库查询。 也可以使用 Stream API 来并行执行操作。简言之，Stream API 提供了一种 高效且易于使用的处理数据的方式。

- Stream是什么

	- 是数据渠道，用于操作数据源（集合、数组等）所生成的元素序列。
	- 用“流”的方式表达数据，借用了I/O流的概念，你可以对流进行过滤操作，得到一个新的流
	- 注意

		- Stream 自己不会存储元素。
		- Stream 不会改变源对象。相反，他们会返回一个持有结果的新Stream。
		- Stream 操作是延迟执行的。这意味着他们会等到需要结果的时候才执行。

- 使用Stream

	- 创建

		- 从一个数据源（集合或数组）中获取stream流
		- 集合创建

			-  default Stream<E> stream() : 返回一个顺序流 
			-  default Stream<E> parallelStream() : 返回一个并行流

		- 数组创建

			- Java8 中的 Arrays 的静态方法 stream() 可以获取数组流：

				- static <T> Stream<T> stream(T[] array): 返回一个流
				- public static IntStream stream(int[] array)
				- public static LongStream stream(long[] array) 
				- public static DoubleStream stream(double[] array)

		- 通过Stream的of()

			- 可以调用Stream类静态方法 of(), 通过显示值创建一个 流。它可以接收任意数量的参数。

				- public static<T> Stream<T> of(T... values) : 返回一个流

		- 创建无限流

			- 使用静态方法 Stream.iterate() 和 Stream.generate(), 创建无限流。

				-  迭代 public static<T> Stream<T> iterate(final T seed, final UnaryOperator<T> f) 
				- 生成 public static<T> Stream<T> generate(Supplier<T> s) 

	- 中间操作

		- 一个中间操作链，对数据源进行处理
		- 筛选与切片

			- filter(Predicate p)

				- 接收 Lambda ， 从流中排除某些元素

			- distinct()

				- 筛选，通过流所生成元素的 hashCode() 和 equals() 去除重复元素

			- limit(long maxSize)

				- 截断流，使其元素不超过给定数量 

			- skip(long n)

				- 跳过元素，返回一个扔掉了前 n 个元素的流。若流中元素不足 n 个，则返回一 个空流。与 limit(n) 互补

		- 映射

			- map(Function f)

				- 接收一个函数作为参数，该函数会被应用到每个元素上，并将其映射成一个新的元素。

			- mapToDouble(ToDoubleFunction f)

				- 接收一个函数作为参数，该函数会被应用到每个元 素上，产生一个新的 DoubleStream。

			- mapToInt(ToIntFunction f)

				- 接收一个函数作为参数，该函数会被应用到每个元素上，产生一个新的 IntStream。

			- mapToLong(ToLongFunction f)

				- 接收一个函数作为参数，该函数会被应用到每个元 素上，产生一个新的 LongStream。

			- flatMap(Function f)

				- 接收一个函数作为参数，将流中的每个值都换成另 一个流，然后把所有流连接成一个流

		- 排序

			- sorted() 

				- 产生一个新流，其中按自然顺序排序

			- sorted(Comparator com) 

				- 产生一个新流，其中按比较器顺序排序

	- 终止操作

		- 执行操作链并产生结果流
		- 终端操作会从流的流水线生成结果。其结果可以是任何不是流的值，例 如：List、Integer，甚至是 void 。 
		- 流进行了终止操作后，不能再次使用。
		- 匹配与查找

			- allMatch(Predicate p) 
			- anyMatch(Predicate p) 
			- noneMatch(Predicate p) 
			- findFirst()
			- findAny()
			- count()
			- max(Comparator c)
			- min(Comparator c) 
			- forEach(Consumer c)

				- 内部迭代(使用 Collection 接口需要用户去做迭代， 称为外部迭代。相反，Stream API 使用内部迭 代——它帮你把迭代做了)

		- 归约

			- reduce(T iden, BinaryOperator b)

				- 可以将流中元素反复结合起来，得到一 个值。返回 T

			- reduce(BinaryOperator b)

				- 可以将流中元素反复结合起来，得到一 个值。返回 Optional<T>

		- 收集

			- collect(Collector c)

				- 将流转换为其他形式。接收一个 Collector 接口的实现，用于给Stream中元素做汇总 的方法

- 并行流
- 串行流

### 接口增强

- 静态方法
- 默认方法

### Optional类

- 目的

	- 解决空指针异常
	- Google公司著名的Guava项目引入了Optional类， Guava通过使用检查空值的方式来防止代码污染，它鼓励程序员写更干净的代 码。受到Google Guava的启发，Optional类已经成为Java 8类库的一部分。

- 简介

	- Optional<T> 类(java.util.Optional) 是一个容器类，它可以保存类型T的值，代表 这个值存在。或者仅仅保存null，表示这个值不存在。原来用 null 表示一个值不 存在，现在 Optional 可以更好的表达这个概念。并且可以避免空指针异常。
	- Optional类的Javadoc描述如下：这是一个可以为null的容器对象。如果值存在 则isPresent()方法会返回true，调用get()方法会返回该对象。

- 创建Optional

	- Optional.of(T t) : 创建一个 Optional 实例，t必须非空； 
	- Optional.empty() : 创建一个空的 Optional 实例
	- Optional.ofNullable(T t)：t可以为null 

- 判断Optional容器中是否包含对象： 

	- boolean isPresent() : 判断是否包含对象 
	- void ifPresent(Consumer<? super T> consumer) ：如果有值，就执行Consumer 接口的实现代码，并且该值会作为参数传给它。 

- 获取Optional容器的对象： 

	- T get(): 如果调用对象包含值，返回该值，否则抛异常 
	- T orElse(T other) ：如果有值则将其返回，否则返回指定的other对象。
	- T orElseGet(Supplier<? extends T> other) ：如果有值则将其返回，否则返回由 Supplier接口实现提供的对象。 
	- T orElseThrow(Supplier<? extends X> exceptionSupplier) ：如果有值则将其返 回，否则抛出由Supplier接口实现提供的异常。

- 实例

  @Test public void test1() { Boy b = new Boy("张三"); Optional<Girl> opt = Optional.ofNullable(b.getGrilFriend()); // 如果女朋友存在就打印女朋友的信息 opt.ifPresent(System.out::println); }
  @Test public void test2() { Boy b = new Boy("张三"); Optional<Girl> opt = Optional.ofNullable(b.getGrilFriend()); // 如果有女朋友就返回他的女朋友，否则只能欣赏“嫦娥”了 Girl girl = opt.orElse(new Girl("嫦娥")); System.out.println("他的女朋友是：" + girl.getName()); }
  @Test public void test3(){ Optional<Employee> opt = Optional.of(new Employee("张三", 8888)); //判断opt中员工对象是否满足条件，如果满足就保留，否则返回空 Optional<Employee> emp = opt.filter(e -> e.getSalary()>10000); System.out.println(emp); } @Test public void test4(){ Optional<Employee> opt = Optional.of(new Employee("张三", 8888)); //如果opt中员工对象不为空，就涨薪10% Optional<Employee> emp = opt.map(e -> {e.setSalary(e.getSalary()%1.1);return e;}); System.out.println(emp); }

### 新的时间和日期API

- java.time包

	- 

- 解决了线程不安全的问题

### 对HashMap做了重要改进

- 由数组+链表转化为了数组+链表+红黑树的方式

### 其他新特性

- 重复注解
- 类型注解
- 通用目标类型判断
- JDK的更新

	- 集合的流式操作
	- 并发
	- Arrays
	- Number和Math
	- IO/NIO的改进
	- Reflection的改进
	- String.join
	- Files

- 新编译工具

	- jjs，jeps

- JVM中Metaspace取代PermGen空间

## 图形化用户界面

### 了解，使用很小

