C#笔记



## 输入与输出

```c#
Console.Write("Hello World");		//输出不换行
Console.WriteLine("Hello World");	//输出换行
Console.WriteLine("sada" + <变量>);
Console.WriteLine("dasd{0}",<变量>);
Console.ReadLine();					//等待玩家输入完毕(按回车之后)才会执行后面的代码
string str = Console.ReadLine();
Console.ReadKey();					//按下键盘任意键则输入结束
char c = ReadKey(true).KeyChar;		//获得输入的内容,若里面为true,则控制台不显示输入内容
```



## 变量

### 变量类型

```c#
//折叠代码
#region MyRegion		//可以让这里面的代码折叠起来  region后面跟着的是折叠后显示的名字
	    
#endregion
    
//变量声明与C++一致
//有符号整型
sbyte sb = 1;			//sbyte -128~127
short s = 3;			//short -32768~32767

//无符号整型
//byte 0~255
//uint 0~42e8
//ushort 0~65535
//ulong 0~18百万兆

//浮点数
float f = 0.123456789f;	//c#中申明的小数默认为double型,加f让他变成float型,不然就是double 7/8位
double d =0.1111111111;	//15~17位
decimal de = 0.1m; 		//27~28位 末尾m与上面f同理

//特殊类型
bool bo = true;
char c = '唐';
string = "aaaa";
```



### 变量命名规则

```c#
//驼峰命名法
string myName = "11";
//帕斯卡命名法
string MyName = '11';
```



## 常量

```c#
//必须初始化,不能修改
const int i = 10
```



## 转义字符

| \\"  |                “                 |
| :--- | :------------------------------: |
| \n   |               换行               |
| \t   |       制表符 一个tab的距离       |
| \b   | 光标退各格,如123\b123打印出12123 |
| \a   |            发出警告音            |
| \0   |       空字符,什么都不输出        |
| @    |  @“hah\hah”会把里面的转义符取消  |



## 类型转换

### 隐式转换

```c#
//隐式转换(大范围转换成小范围)
int i = 1;
long j = 1;
j=i;			//int转换为long型
//bool char不同与c++,无法存整型变量,整型变量存不了bool但能存char
```



### 显式转换

```c#
//变量类型 变量名 = (变量类型)变量;
int i = 1;long x = 1;i = (int)x;//可以小范围存强转后的大范围

//Parse法,将字符串转换成其他类型
int i = int.Parse("123");
float i = float.Parse("123.13");
bool b = bool.Parse("true");

//Convert法
int a = Convert.ToInt32("12");	//按照存储空间来
a = Convert.ToInt32(1.458f);  	//a会输出1,四舍五入
a = Convert.ToInt32(true);		//true为1,flase为0
sbyte sb = Convert.ToSByte("1");
short sh = Convert.ToInt16("1");
long l = Convert.ToInt64("1");

byte sb = Convert.ToByte("1");
ushort sh = Convert.ToUInt16("1");
ulong l = Convert.ToUInt64("1");

float f = Convert.ToSingle("1.1");
double d = Convert.ToDouble("1.1");
decimal de = Convert.ToDecimal("1.1");

bool bo5 = Convert.ToBoolean("true");
char c = Convert.ToChar("a");
string str = Convert.ToString("dasda");

//其他类型转string
string str = 1213.ToString(); 	//任何类型都可以,true.ToString() 1.1f.ToString() 

```



## 异常捕获

```c#
//避免代码报错时造成程序卡死的情况
try						//try和catch必备
{
    					//放入可能异常的代码块,如果出错则会立马跳入catch,不会执行剩下代码
    
}
catch		
{
    
}
finally					//可选部分
{						//不管有没有出错都会执行这里的代码			

}
```



## 运算符

### 算术运算符

```c#
//与c++一致
```



### 字符串拼接

```c#
//方式1
string str = str1 + str2;
str = "1" + 1;					//输出11,不用双引号也可以,默认调用1.ToString()
str += 1 + 2 + 3 + 4;			//输出10,因为1和2拼出来是数字,后面3+3拼起来也是数字
str += "" + 1 + 2 + 3 + 4; 		//输出则是1234,因为""和1拼起来是字符串

//方式2
str2 = string.Format("内容{1}啊,内容{2}啊,内容{3}啊",1,"2","三");

//控制台打印拼接
Console.WriteLine("内容{1}啊,内容{2}啊,内容{3}啊",1,"2","三")
```



### 条件运算符

```c#
result = 1 < 5;			//输出false  与c++一致
```



### 逻辑运算符

```c#
//&&　｜｜　　与ｃ＋＋一致
```



### 位运算符

```c#
//& ^ >> << ~(取反)  与c++一致
```



### 三目运算符

```c#
bool flag = false;
int a = flag ? 1 : 2;			//a输出2   与c++一致
```



### 条件分支语句

```c#
if()			//与c++一致
{
    
}
else
{
    
}
else if
{
    
}

switch(<变量>) 		//与c++一致
{
	case <常量>:
        代码;
        break;
}
```





## 循环语句

```c#
//与c++一致
```



## 控制台相关

```c#
char c = Readkey(true).KeyChar;			//则输入的内容不会显示在在控制台上
Console.clear();						//控制台清空

//设置控制台大小
//窗口大小  缓冲区大小
//先设置窗口大小  再设置缓冲区大小
//缓冲区大小不能小于窗口大小
//窗口大小不能大于控制台的最大大小
Console.SetWindowSize(100,50);			//窗口大小
Console.SetBufferSize(1000,1000);		//缓冲区

//设置光标位置
Console.SetCursorPosition(x,y);			//左上角为(0,0) 右侧x轴正方向,下侧y轴正方向

//设置颜色相关
Console.ForegroundColor = ConsoleColor.Red;//文字会变成红色

//背景颜色
Console.BackgroundColor = ConsoleColor.White;
Console.Clear();								//重置背景颜色后要clear一次才行

//光标显隐
Console.CursorVisible = false;			//隐藏光标

//关闭控制台
Environment.Exit(0);

//检测是否有按键输入
if (Console.KeyAvailable);
```



## 随机数

```c#
//Random 随机数变量名 = new Random();
Random rand = new Random();
int i = rand.Next();				//生成一个非负数的随机数
i = rand.Next(100);					//0~99的随机数
i = rand.Next(5,100);				//5~99 左闭右开
```



## 复杂数据类型

### 枚举

```c#
//声明枚举语法 枚举名以E或E_开头作为命名规范
enum E_PlayerType
{
    自定义枚举名字1 = 5,//第一个项变成5,后面累加,所以下一个就是6,若后面再设100,则更下一个101
    自定义枚举名字2,
    Main,
    Other,
}
//一般放在namespace语句块下(常用),不能再函数语句块中声明

//枚举的使用
//声明枚举变量 
E_PlayerType playertype = E_PlayerType.Main;
if(playertype == E_PlayerType.Main)
{
    ....
}
else if(playertype == E_PlayerType.Other)
{
    ....
}

switch (playertype)
{
    case E_PlayerType.Main:
        ....
        break;
    ....
}

//枚举的类型转换
int i = playertype;
string str = playertype.ToString();	//打印枚举的名字
playertype = (E_PlayerType)Enum.Parse(typeof(E_PlayerType),"Other");//字符串转换为枚举,只能有枚举里面有的名字才能转
```



### 数组

```c#
//数组声明
int[] arr1;
int[] arr2 = new int[5];
int[] arr3 = new int[5] {1, 2, 3, 4, 5};	//大括号内要放满5个
int[] arr4 = new int[] {};					//[]内不写东西,则{}想写几个写几个
int[] arr5 = {};							//直接在{}写内容

//数组的使用
int[] array = {1, 2, 3, 4, 5};
Console.WriteLine(array.Lenth);				//数组长度
array [4] = 0;								//修改数组
//遍历数组与c++一致

int[] array2 = {....};
array = array2;								//可以直接赋值成另一个数组,跟指针类似

//二维数组
//二维数组声明
int[,] arr;
int[,] arr = new int[3,3];					//声明三行三列的二维数组
int[,] arr = new int[3,3] {{1,2,3},			//第一行
                           {4,5,6},			//第二行
                           {7,8,9}};		//第三行
int[,] arr = {{},{},{}}						//直接在{}写内容

//二维数组长度
array.GetLength(0);							//得到有多少行
array.GetLength(1);							//得到有多少列

//获取二维数组中的元素
array[0,1];									//获得第一行第三列

//交错数组(有n行,每行的元素个数可以不一样)
//交错数组的声明
int[][] arr1;
int[][] arr2 = new int[3][];	//第二个[]不能填东西,因为只能指定行,每行有多少列不定
int[][] arr3 = new int[3][] {new int[] {1, 2, 3},
                             new int[] {2,3},
                             new int[] {1}};
int[][] arr3 = new int[][] {new int[] {1, 2, 3},
                            new int[] {2,3},
                            new int[] {1}};
int[][] arr4 = {new int[] {1, 2, 3},
                new int[] {2,3},
                new int[] {1}};

//获取交错数组的长度
array.GetLength(0);				//获得行数
array[0].Length;				//获得第一行中元素的个数
array[0][0] = 1;				//修改交错数组中的元素
```



## 值类型和引用类型

```c#
//引用类型 string,数组,类
//值类型 其他,结构体

//string虽然是引用类型,但是具备值特征,它变我不变
```



## 函数

### 函数基础

```c#
//写在class或struct中
//基本语法 static 返回类型 函数名(参数类型 参数名1, 参数类型 参数名2, ......) {}
//static 非必须  但在学习类和结构体之前都是必须写的
static void SayHello()
{
    Console.Write("Hello");
}
//一个函数返回两个值
static int[] Calc(int a, int b)
{
    return new int[] {a, b};
}
```



### ref和out(引用)

```c#
//ref相当于c++中的引用&
static void Change(ref int val)
{
    val = 1;						//就是引用 若a = 0 Change(a)后 a变成1
}
//使用和声明一致  区别:ref接受的变量必须初始化 out的可以不用初始化 但是在函数内必须给他赋值
Change(ref a);						//传参前面也要加ref
```



### 变长参数和参数默认值

```c#
//边变长参数关键字 params params后必须为数组 且一定作为最后一个参数
static int Sum(params int[] arr)
{
    ....
    return sum;
}
Sum(1,2,3,4);						//可以填任意多个数 不用传数组因为有params
    
//参数默认值
static void Speak(str = "Hello")
{
    Console.Write(str);				//可以传参数可以不传 不传的话就是默认Hello
}
```



### 函数重载

```c#
//与c++一致
```



###　递归函数

```c#
//与c++一致
```



## 结构体

```c#
//基本语法(写在namespace下面)
struct Node				//和c++区别 结构体内不能包含自己类型的变量 如 Node a不能写在里面
{
    public
    int b;				//私有 外部不能访问 在前买加private是私有 默认不写也是私有
    Node a;				//错误 不能这么写 与c++不同
    public int c;		//公有 外部可以访问
    public void Speak() {}
    public Node(int a)	//构造函数 必须对所有的参数赋值 而且必须要有参数 就是必须传参
    {
        ....			//若重名可以用this this.a = a;
    }
}

//构造函数的使用
Node n = new Node(1);

//结构体可以继承接口
```



## 面向对象

### 封装

#### 类和对象

```c#
//类的声明
class Student
{
 	  
}

//实例化
Student student = new Student();

//class是引用类型
GameObject A = new GameObject();
GameObject B = A;					//若更改B中的内容,则A中的内容一并更改,相当于A和B指向一块地址
B = nullptr;						//B指向空,但是A的地址并不会改变,有点像指针
//把AB看成独立个体, B = A代表他们住同一个房子,B改房子中的内容A的也会改,但是B = nullptr就相当于B这个人搬家了,但是A并没有动,还在原先的家里


```



#### 成员变量

```c#
//与c++几乎一致 都有public private protected
class Person
{
    int age;			//不声明默认私有
    public string name;	//公有
    //若不赋值则 int默认为0 bool默认为false 引用类型都是nullptr
}
```



#### 成员方法

```c#
//不加static 受到访问修饰符影响
class Person
{
    public void say()			//不加修饰符默认为私有
    {
        Console.Write("Hello");
    }   
}
```



####　构造函数和析构函数与垃圾回收

```c#
//构造函数 无特许需求时都是public 其他与c++几乎一致
class Person
{
    public Person()								//允许无参构造,但是结构体不允许
    {
        
    }
    
    public Person(string name)
    {
        
    }
    
    public Person(int age, string name):this()	//构造函数特殊用法 会先调用无参的构造函数 再调用这个构造函数
    {											//若是:this(name) 则会调用只有一个参数的构造函数
        ....		
    }
    
    public Person():this("shabi")				
    {											//无参构造函数后面this加常量则调用上面写的一													个参数的构造函数
        
	}
}
//其他this用法与c++一致

//析构函数 几乎不使用 因为c#有自己的垃圾回收机制 与c++几乎一致
~Person() {...}

//主动垃圾回收
GC.Collect();		//在loading条时使用 防止之后游戏过程中内存满了再回收导致卡顿
```



#### 成员属性

```c#
//成员属性的基本用法
class Person
{
    private string name;
    private int money;
    public string Name
    {
        set							//get与set可以只有一个
        {
            //value用于表示外部传入的值
            name = value;
        }
        get
        {
            //可以添加理解 如 name = name + "..";
          	//意味着这个属性可以获得的内容
        	return name;  
        }
    }
    
    public int Money
    {
        set
        {
            if (value < 0) Console.Write("不能小于0"), money = 0;
            else money = value + 5;	//加密
        }
        get
        {
            return money - 5;		//解密
        }
    }
}

p.Name = "xxx";				//执行其中的set语句块
Console.Write(p.Name);		//执行其中的get语句块

//get和set前可以加访问修饰符
//1.默认不加 会使用属性中声明的访问权限
//2.加的访问修饰符要低于属性的访问权限
//3.不能让get和set的访问权限都低于属性的访问权限

public int Money
    {
        set
        {
            if (value < 0) Console.Write("不能小于0"), money = 0;
            else money = value + 5;
        }
        private get						//则只能修改不能获得 但不能同时set和get都设置private
        {
            return money - 5;		
        }
    }


//自动属性
class Person
{
    public float Height			//没有对应的成员变量 同时set私有 只能得不能改 
    {
        get;
        private set;
    }
}
```



#### 索引器

```c#
//索引器的语法
class Person
{
    private string name;
    private int age;
    private Person[] friends;
    
    private int[,] array = new array[3, 3];
    
    //访问修饰符 数据类型 this[数据类型 变量]
    public Person this[int index]		//和成员属性很像 不过是返回类中的数组对应索引的值
    {
        get
        {
         	if (friends == null || index < 0 || index > friends.Length - 1) return null;
            return friends[index];
        }
        set
        {
            
        }
    }
    
    public int this[int i, int j]		//重载
    {
        get
        {
            return array[i, j];
        }
        set
        {
            if (array == null) 
            {
                array = new int[3][3];
                array[i, j] = value;
            }        						
            array[i, j] = value;
        }
    }
    
    public string this[string str]		//可以随便设置括号内变量 有点像map的映射
    {
        get
        {
            if (str == name) return name;
            else return "sb";
        }
    }
    
}

Person p = new Person();
p[0] = new Person();
p[0, 0] = 10;
Console.Write(p[0, 0]);
```





#### 静态成员

```c#
//static
public class Test
{
    public static int a;		//static和int的位置可以互换
}

Console.Write(Test.a);			//可以直接类名.变量直接使用 所有生成的对象的静态成员的值都是一样的

//const若也写在类里面也可以 直接类名.变量直接使用 其他用用法和c++一致


```





#### 静态类和静态构造函数

```c#
public static class Test			//静态类 无法被实例化 如Test t = new Test(); 是错的 其中的所有方法和变量都可以类名.变量直接使用
{
    static Test()					//静态类中的静态构造函数 不能有参数 不能有访问修饰符 只会静态调用一次 
    {
        
    }
    
    public static int testIndex = 0;//只能包含静态的成员
}

public static class Test
{
    static Test()					//普通类中的静态构造函数 只会执行一次(当你第一次使用类中的内容的时候就执行)
    {
        
    }
    
    public Test()					//普通构造函数 每次new一个都会调用一次
    {
        
    }
}
```



#### 拓展方法

```c#
//基本语法 访问修饰符 static 返回值 函数名(this 拓展类名 参数名, 参数类型 参数名, 参数类型 参数名, ....)
//只能为现有的非静态类拓展方法 静态类不能拓展
public static class Tools				//一定写在静态类里面
{
    //为int拓展了一个成员方法 value代表使用该方法的实例化对象
    public static void SpeakValue(this int value)
    {
        Console.WriteLine("拓展方法" + value);
    }
    
    public static void fun(this string str1, string st2)
    {
        Console.Write("{0}喜欢{1}", str1, str2);
    }
    
    public static void fun3(this Test t)
    {
        Console.Write("为Test的拓展方法")
    }
}

class Test
{
    public void fun2()
    {
        ..
    }
}

//使用
int i = 10;
i.SpeakValue();					//输出 拓展方法10
string a, b;
a.fun(b);						//输出 a喜欢b
Test t = new Test();
t.fun3();						//会多出一个fun3的函数可以用 拓展方法和原有的方法重名 则会先调用自己的方法
```





#### 运算符重载

```c#
class Point		
{
    public int x;
    public int y;
    
    public static Point operator +(Point p1, Point p2)		//重载加号 与c++相似
    {
        Point p = new Point;
        p.x = p1.x + p2.x;
        p.y = p1.y + p2.y;
        return p;
    }
    
    public static Point operator +(Point p1, int value)		//必须有一个是当前类的类型 其他的任意 只能有两个参数
    {
        Point p = new Point;
        p.x = p1.x + value;
        p.y = p1.y + value;
        return p;
    }
}

p3 = p1 + p2;			

//可重载与不可重载的运算符 

//可重载的 逻辑运算符 !(仅有!可以)
//为运算符 & ~ >> << ^
//条件运算符 > < <= >= == !=(要成对重载 如果重载了小于 则必须重载大于)

//不可重载 逻辑与&& 索引符[] 强转运算符() 特殊运算符 点. 三目运算符 ? : 赋值运算符 =
```





#### 内部类和分布类

```c#
//内部类
class Person
{
    
    public Body body;
    
    public class Body						//不写public外部类点不出自己
    {
        Arm leftArm;
        Arm rightArm;
        
        class Arm
        {
            
        }
    }
}

Person p = new Person();
Person.Body body =new Person.Body();		//要用外面的类点出自己才能使用

//分部类
partial class Student
{
    public bool sex;
    
    partial void Speak();
}

partial class Student						//这两个是一个类 只不过是分开来写 他们的内容是共用 但两个分部类中内容不能重复 类的访问修饰符要一致
{
    public string name;
    partial void Speak()					//分部方法 前面的分部类中没定义的方法在这里写 但是前面如果方法中有内容就不能写
    {
        ...
    }
}
```



### 继承



#### 继承的基本规则

```c#
//只能有一个父亲 其他基本与c++一致 没什么好说的
class Teacher
{
    
}

class TeachingTeacher : Teacher
{
    
}
```



#### 里氏替换原则

```c#
//父类容器装载子类对象
class GameObject
{
   
}

class Player : GameObject
{
    void PlayerAtk()
    {
        
    }
}

class Monster : GameObject
{
    
}

GameObject player = new Player();		//父类容器装载子类对象
GameObject monster = new Monster();

player.PlayerAtk();						//错误 无法直接使用 所以有接下来的is和as

GameObject[] objects = new GameObject[] {new Player(), new Monster()};		//这才是里氏替换原则的意义 存多个不同类型的对象在一个数组里

//is 判断一个对象是否为指定对象
if ( player is Player )					//判断这个对象是不是指定类对象 是的话返回true
{
    
}

//as 将一个对象转换为指定类对象 成功返回指定类型对象 失败则返回null
Player p = player as Player;			//成功
Player p = monster as Player;			//失败 因为monster中是Monster对象

if (player is Player)
{
    Player p = player as Player;		//配合使用防止转换错误
    p.PlayerAtk();
    
    (player as Player).PlayerAtk();		//也可以
}

for (int i = 0; i < objects.Lenght; i++)
{
    if (object[i] is Player)
    {
        (object[i] as Player).PlayerAtk();
    }
    if (object[i] is Monster)
    {
        .....
    }
}
```





#### 继承中的构造函数

```c#
//子类通过base关键字调用父类的构造函数
//无参构造子类会自动调用父类的无参构造函数 所以若子类只有无参构造则父类必须要有无参构造函数
class GameObject
{
    public GameObject()
    {
        Console.Write("1");
    }
    
    public GameObject(int x)
    {
        
    }
}

class Player:GameObject
{
    public Player()						//会自动调用父类的无参构造函数 什么都不用写
    {
        Console.Write("2");
    }
    
    public Player(int x) : base(x)		//这样的话父类就可以没有无参构造
    {
        
    }
    
    public Player(int x, string name) 	//若父类没有无参构造则会报错
    {
        
    }
}

Player player = new Player();			//输出 1 2
```



#### 万物之父和装箱拆箱

```c#
//万物之父 object是所有类型的基类 object是引用类型
class Father
{
    
}

class Son
{
    
}

Son f = new Son();
Object o = new Son();			//可以装载任意对象 所以可以用Object数组存任何东西 int bool 任何数据类型

object o2 = 1f;					//object转换任何数据
float f1 = (float)o2;
object str = "1234";			
string str2 = str as string;
object[] arr = new int[10];
int[] arr = arr as int[];


//装箱拆箱

//装箱
//把值类型用引用类型来存储
//栈内存迁移到堆内存中

//拆箱
//把引用存储的值类型取出来放入值类型对象
//堆内存迁移到了栈内存中

//好处:不确定类型时可以使用object来存储任何类型 方便传递和存储
//坏处:存在内存迁移 增加性能消耗

object o2 = 1f;					//装箱 用object存值类型 把值类型转化为引用类型
float f1 = (float)o2;			//拆箱 再把object转化为值类型 涉及性能消耗
object str = "1234";			
string str2 = str as string;	
object[] arr = new int[10];
int[] arr = arr as int[];

static void TestFun(params Object[] array)
{
    
}

TestFun(1, 2, "2313", true)		//传什么都可以
```





#### 密封类

```c#
//密封类是使用sealed密封关键字修饰的类 让类无法被继承

class Father
{
    
}

sealed class Son:Father			//无法被继承
{
    
}
```







### 多态



#### 多态\_vob

```c#
//与c++一致
//v virtual(虚函数) o override(重写) b base(父类) 没有vob这个概念 唐老狮自己编的

public GameObject
{
	public void Atk()
    {
        Console.Write("1");
    }
}

public Player:GameObject
{
    public void Atk()
    {
        Console.Write("2");
    }
}


GameObject player = new Player();
player.Atk();						//输出1 执行父类
(player as Player).Atk();			//输出2

public GameObject
{
	public virtual void Atk()		//虚函数 GameObject player = new Player(); 只要装的是子类对象 那一定会调用父类虚函数对应的子类函数
    {
        Console.Write("1");
    }
}

public Player:GameObject
{
    public override void Atk()
    {
        base Atk();					//可以保留父类的信息
        ......						//自己的逻辑
    }
}

GameObject player = new Player();
player.Atk();						//输出2 执行子类 因为父类那里是虚函数
(player as Player).Atk();			//输出2
```





#### 抽象类和抽象方法

```c#
//抽象类 abstract修饰的类 不能被实例化 可以包含抽象方法且抽象方法只能写在抽象类当中 继承抽象类必须重写其抽象方法
//相当于一个专门用来继承的类
abstract class Thing
{
    public string name;
 	
    public abstract void Test();	//不能有函数体
}

class Water:Thing
{
    public override void Test()		//必须重写父类的抽象方法
    {
      
    }
}
```





#### 接口

```c#
//接口不包含成员变量 接口只包含方法 属性 索引器 事件  成可以不用访问修饰符 成员不能是私有的  接口不能继承类但是可以继承另一个接口
//类只能继承一个类但是可以继承多个接口必须实现接口中的所有成员且必须是公共的
//接口是用来继承的 接口不能被实例化

//接口的声明
Interface IFly
{
	public void Fly();			//不能被实现 不能有函数结构体
    
    string Name
    {
        get;					//同样不能被实现
        set;	
    }
    
    int this[int index]
    {
        get;					//同样不能被实现
        set;
    }
}

class Animal
{
    
}

class Person : Animal, IFly		//逗号后面跟的是接口
{
    public void Fly()			//实现接口的方法必须加public 也可以加virtual写成 public virtual void Fly()
    {
        
    }
    
    public string Name			//实现接口的方法必须加public
    {
        get;
        set;
    }
    
    public int this[int index]	//实现接口的方法必须加public
    {
        get;					
        set;
    }
}

//接口也遵循里氏替换原则
IFly f = new Person();			//因为Person继承自IFly接口

Intereface IWalk
{
    void Walk();
}

Intereface IMove : IFly, IWalk	//接口继承接口
{
    
}

//显示实现接口 当一个类继承了两个接口且存在同名方法时
interface IAtk
{
    void Atk();
}

interface ISuperAtk
{
    void Atk();
}

class Player : Atk, SuperAtk
{
    public void IAtk.Atk()
    {
     	....   
    }
    
    public void ISuperAtk.Atk()
    {
        ....
    }
    
    void Atk()						//自己的 不来自接口
    {
        
    }
}

IAtk ia = new Player();
ia.Atk(); 						//调用IAtk中的方法
ISuperAtk isa = new Player();
isa.Atk();						//调用ISuperAtk中的方法

Player p = new Player();
(p as IAtk).Atk();				//这样才能分别调用对应的方法
(p as ISuperAtk).Atk();			
```





#### 密封方法

```c#
//用密封关键字sealed修饰的重写函数 让虚函数或者抽象方法之后不能被重写 和override一起出现

abstract class Animal
{
    public string name;
    
    public abstract void Eat();
}

class Person
{
    public sealed override void Eat()
    {
        ...
    }
}

class WhitePerson : Person
{
    public override void Eat()				//报错 因为Person已经对Animal中的抽象方法密封 WhitePerson无法重写
    {
        
    }
}
```





### 面向对象相关联知识





#### 命名空间

```c#
//命名空间的基本概念 命名空间可以理解为c++中的头文件

//命名空间的基本使用
namespace MyGame
{
    class GameObejct
    {
        
    }
}

namespace MyGame						//可以分开写 相当于同一个命名空间分块写
{
    class Player:GameObject
    {
        
    }
}

//不同命名空间相互使用 需要引用命名空间或者指名出处
using MyGame							//引用命名空间 和c++的头文件很像 引用之后就可以用命名空间里面定义的类
MyGame.Object = new MyGame.Object();	//也可以 很像c++中的std::cout

//不同命名空间可以有同名类
namespace MyGame2
{
    class Object
    {
        
    }
}

//引用
using MyGame
using MyGame2
    
MyGame.Object = new MyGame.Object();			//若引用的命名空间有同名类 要这样子指名出处
MyGame2.Object = new MyGame2.Object();


//命名空间可疑包裹命名空间
namespace MyGame
{
    namespace UI
    {
        class Image
        {
            
        }
    }
    
    namespace Game
    {
        class Image
        {
            
        }
    }
}

using MyGame.UI
using MyGame.Game
MyGame.UI.Image image = new MyGame.UI.Image();

//关于访问修饰
//命名空间中的类默认为public
//internal 修饰符
namespace MyGame
{
	interal class Person		//则这个类只能在这个文件中使用 就算分文件引用了该命名空间也不能使用这个类
    {
        
    }		
}
```



#### 万物之父中的方法

```c#
//object中的静态方法
//Equal方法 按照左侧对象的方法规则来进行比较
Console.WriteLine(Object.Equeals(1,1));				//判断这两个值是否相等 
Test t1 = new Test();
Test t2 = new Test();
Console.WriteLine(Object.Equals(t1,t2));		//判断两个对象指向的内存是否相同 因为都是新内存空间所以返回false

//ReferenceEquals用来比较两个对象是否相同的引用 主要是用来比较引用类型的对象
//值类型的对象返回值始终是false
t1 = t2;
Console.WriteLine(Object(t1,t1));				//返回true

//object中的成员方法
//普通方法GetType 获取对象运行的时的类型Type
Type type = t.GetType();						//因为所有类型都是Object类型 所以都有GetType方法

//普通方法MemberwiseClone 用于获取对象的浅拷贝对象 会返回一个新的对象 但是新的对象与老的对象一致 !!!老对象中的值类型改变新对象不会变 但是老对象中的引用类型改变 新对象中的也会跟着改变
class Test
{
    public i = 1;
    public Test Clone()
    {
        return MemberwiseClone() as Test;	//因为MemberwiseClone是保护类型外部没法用所以必须内部使用 且默认返回为object类 所以要as Test
    }
}
Test t3 = t1.Clone();							//t3就会和t1一致了

//object中的虚方法
//虚方法Equals 默认实现还是比较两者是否为同一引用 即相当于ReferenceEquals
//其实意思就是输Equals可以用来重写
class Test
{
    private int i = 1;
    public override bool Equals(object obj)
    {
        return base.Equals(obj);
    }
    
    public override bool GetHashCode()
    {
        return base.GetHashCode();
    }
    
    public override bool ToString()
    {
        return base.GetHashCode();
    }
    
    public override string ToString()
    {
        return string.Format("hahaha{0}", i);			//重写后Console.Write(t1);	会打印出hahaha1
    }
}

//虚方法GetHashCode 获取对象哈希码 可以重写

//虚方法ToString 用于返回当前对象代表的字符串 可以重写他定义我们自己的对象转字符串规则

Console.Write(t1);					//打印的内容是根据ToString内定义的 所以要是想指定对象中的输出内容可以重写ToSting方法 默认输出的是命名空间名字
```





#### string

````c#
//字符串指定位置的获取
string str = "abcdefggfedcba";
Console.Write(str[0]);				//只能获取不能设置 所以str[0] = "a";是不可以的
char[] char = str.ToCharArray();	//将string转为字符数组
str.Length							//获取字符串的长度
    
//字符串拼接
str = string.Fomat("dad{0}{1}", 变量1, 变量2);

//正向查找字符位置
int index = str.IndexOf("c");		//获得c在str中的位置 正着查第一次出现的位置 若没有找到会返回-1

//反向查找字符串的位置
int index = str.LastIndexOf("c");	//获得c在str中的位置 倒着查第一次出现的位置 若没有找到会返回-1

//移除指定位置后的字符
str = str.Remove(4);				//4及4以后的都会被删掉 必须用另一个字符串存 不会改变自身
str = str.Remove(1, 2);				//从第一个位置开始删除两个字符 前面一个是位置 后面一个是删除字符的个数

//替换指定字符串
str = str.Replace("abc", "jkl");	//将字符串里面的abc全部换为jkl 同样不会改变自身 要用一个新的字符串去存

//大小写转换
str = str.ToUpper();				//转换为大写 同样不会改变自身 要用一个新的字符串去存
str = str.ToLower();				//转化为小写 同样不会改变自身 要用一个新的字符串去存

//字符串截取
str = str.Substring(2);					//截取从指定位置开始之后的字符串 同样不会改变自身 要用一个新的字符串去存
str = str.Substring(2, 3);				//截取第二个位置后的三个字符 前面一个是位置 后面一个是截取字符的个数 若字符串长度小于截取字符的长度则会报错所以要注意 同样不会改变自身 要用一个新的字符串去存

//字符串切割 
string str = "1,2,3,4,5,6,7";
string[] strs = str.Split(',');			//会根据括号内选定的逗号将字符串中的内容分开一个个存进strs数组中
````





#### stringbuilder

```c#
//c#提供的一个用于处理字符串的公共类
//修改字符串而不是创建新的对象,需要频繁修改和拼接字符串可以使用它,可以提升性能
//使用前 需要引用命名空间 using System.Text
using System.Text
    
//初始化
StringBuilder str = new StringBUilder("123123123", 100);	//后面的100可以不写 写的就代表容量大小

//每次往里面加内容的时候会自动扩容 产生垃圾的垃圾比string小的多 假设原来容量为8 扩容后就会变成16 再扩就是32(之前的8和16都变成垃圾) 不像string每次增加内容都要开一个新内存 
//获得容量
Console.Write(str.Capacity);

//增删查改
//增
str.Append("444");
str.AppendFormat("{0}{1}", 100, 999);

//插入
str.insert(0,"567");			//索引和要插入的内容

//删
str.Remove(0,10);				//从哪个位置开始删 删多少个
    
//清空
str.clear();

//查
str[1];

//改
str[0] = '7';					//字符串只能读取不能改

//替换
str.Replace("1", "2");			//把1都换成2 不像string要重新赋值 str = str.Replace("1", "2"); StringBuilder会修改自身

//判断是否相等
str.Equals("123123");			//判断str是否和"123123"相等
str.Equals(str2);				//判断str是否和str2相等
```





### 单例模式

```c#
public class Singleton		
{
    private static Singleton instance = new Singleton();	//这个类只有唯一的实例化对象 减少内存消耗	

    private Singleton() { }									//将构造函数设为私有 防止再次实例化对象	
 
  	public static Singleton Instance						//通过Singleton.Instance获得唯一的实例对象
    {
        get
        {
            return instance
        }
    }
}

//有继承的单例模式
public class BaseSingleton<T>
{
    private static T instance = new T();
    
    private T() {}
    
    public static T Instance => instance;
}

public class Singleton : Basesingleton<Singleton>	//这样这里面就直接会有个单例成员可以直接用
{
    
}
```





## 简单数据结构类

### ArrayList

```c#
//声明 要引用命名空间 using System.Collections
ArrayList array = new ArrayList();

//增删查改
//增
array.Add(1);
array.Add("123");
array.Add(new object());		//什么都能加 因为ArrayList的类型是Object
array.insert(1, "325");			//第一个位置插入325

ArrayList array2 = new ArrayList();
array.AddRange(array2);			//把array2中的内容都加到array中

//删
array.Remove(1);				//若有两个1则会删除第一个
array.RemoveAt(2);				//删除指定位置2的元素
array.Clear();					//清空

//查
Console.Write(array[0]);		//可以直接使用索引
if (array.Contains("123"));		//判断是否存在123
int index = array.IndexOf(1);	//将第一个出现的1的位置返回 没有找到则返回-1
index = array.LastIndexOf(1);	//将最后一个出现的1的位置返回 没有找到则返回-1

//改
array[0] = 999;					//直接使用索引改即可

//遍历
array.Capacity					//获得容量
array.Count						//得到长度
for (int i = 0; i < array.Count; i++)
{
    Console.WriteLine(array[i]);
}

//迭代器遍历
foreach (vat item in array)		//很像c++的for(auto x : a)
{
    Console.WriteLine(item);
}

//装箱拆箱
//当往ArrayList中进行值类型存储时就是在装箱 当值类型对象取出来转换使用时就存在拆箱 所以ArrayList要尽量少用

array.Reverse();				//翻转
```



### Stack

```c#
//声明 引用命名空间 using System.Collections
Stack stack = new Stack();

//增取查改
//增
stack.Push(1);
stack.Push("123");				//同样是object类型 什么都能压入栈中

//取
object v = stack.Pop();			

//查 只能查看栈顶
v = stack.Peek();				//只是看了一看 没有弹出来
if (stack.Contains(1));			//查看1是否存在栈中

//改
stack.Clear();					//清空

//遍历
foreach (var item in stack)
{
    Console.WriteLine(item);	//从栈顶遍历
}

object[] array = stack.ToArray();//变成数组后遍历 也是从栈顶开始
for (int i = 0; i < array.Length; i++)
{
	...
}

while (stack.Count > 0)			//循环弹栈遍历
{	
    object o = stack.Pop();
    Console.WriteLine(o);	
}
```





### Queue

```c#
//声明 引用命名空间 using System.Collections
Queue q = new Queue();

//增取查改
//增
q.Enqueuq(1);
q.Enqueuq(new Test());			//同样存什么都可以

//取
object v = q.Dequeuq();			//取出

//查
v = q.Peek();					//只看不取
if (q.Contains(1));				//判断是否存在于队列中

//改
q.Clear();						//清空
q.Enqueue("123");				//往后面加东西

//遍历
q.Count							//长度
foreach (var item in q)			//遍历
{
    ....				
}
object[] array = q.ToArray();	//变成数组后遍历
for (int i = 0; i < array.Length; i++)
{
	...
}

while (q.Count > 0)				//循环出队遍历
{	
    object o = q.Dequeue();
    Console.WriteLine(o);	
}
```





### Hashtable(c++中的map)

```c#
//声明 using System.Collections
Hashtable h = new Hashtable();

//增删查改
//增
h.Add(1, "123");			//也是什么值都能放 因为是object类型 左边是key 右边是value
//!注意:不能出现相同的键 key不能重复 但是value可以重复

//删
h.Remove(1);				//把key为1的一对键值对删除
h.Clear();					//清空

//查
Console.WriteLine(hashtable[1]);	//key为1对应的value打印出来
if (h.Contains(1));			//判断有没有key为1的
if (h.ContainsKey(1));		//和上面一样没区别	
if (h.ContainsVaule(1));	//判断有没有value为1的

//改
h[1] = "1234";				//改变key为1对应的值

//遍历
Console.WriteLine(h.Count);	//获得键值对数量

foreach (var item in h.Keys)//遍历所有键
{
    ...
}

foreach (var item in h.Values)//遍历所有值
{
    ...
}

foreach (DictionaryEntry item in h)	//键值一起遍历
{
    Console.WriteLine(item.key + item.Value);
}

IDictionaryEnumerator myEnumerator = h.GetEnumerator();	//迭代器遍历
bool flag = myEnumerator.MoveNext();
while (flag)
{
    Console.WriteLine(myEnumator.Key + myEnumator.Value);	
}
```



## 泛型



### 泛型

```c#
//泛型是什么 像c++的类模板

//泛型分类

//泛型类和泛型接口
//class 类名<泛型占位字母>
//interface 接口名<泛型占位字母>

//泛型函数
//函数名<泛型占位字母>(参数列表)
class TestClass<T>
{
    public T value;
}

TestClass<int> t = new TestClass<int>();			//实例化

class TestClass2<T1, T2, K>							//可以有多个泛型占位符
{
    public T1 value1;
    public T2 value2;
    public K key;
}

TestClass2<int, string, float> t2 = new TestClass2<int, string, float>();

Testinterface TestClass2<T1, T2, K>					//泛型接口
{
    T Value
    {
        get;
        set;
    }
}

class Test : Testinterface<int, string, float>		//继承泛型接口
{
    ...
}

   
//泛型方法
//普通类中的泛型方法

class Test2
{
    public void TestFun<T>(T value)
    {
        //用泛型做逻辑处理
        T value2 = deafult(T);	//获得类型的默认值 传进来什么类型就获得该类型的默认值
        Console.WriteLine(value + value2);
    }
    
    public T TestFun<T>()		//返回值为T
    {
        return default(T);
    }
    
    public void TestFun<T, K, M>(T value, K value2, M value3)	//多个泛型占位字母
    {
        ...
    }
}

Test2 t2 = new Test2();
t2.TestFun<string>("12313");

//泛型类中的泛型方法
class Test3<T>
{
    public T value;
    public void TestFun(T t)		//这个T来自泛型类 所以不是泛型方法
    {
        
    }
    
    public void TestFun<K>(K value)	//这个才是泛型方法
    {
        ...
    }
}
Test3<int> t3 = new Test3<int>();
t.TestFun<stirng>("123");			//<string>可以省略不写 会根据括号里的类型自动判断
t.TestFun(1);						//这个用的就是没重载的非泛型方法
```





### 泛型约束

```c#
//让泛型的类型有一定的限制
//关键字:where
//一共有6种
//1.值引用							where 泛型字母: struct
//2.引用类型						where 泛型字母: class
//3.存在无参公共构造函数(不能是抽象类)	where 泛型字母: new()
//4.某个类本身或者其派生类				where 泛型字母: 类名
//5.某个接口的派生类型				where 泛型字母: 接口
//6.另一个泛型类型本身或者派生类型		where 泛型字母: 另一个泛型字母

class Test1<T> where T:struct		//传进来的T只能是值类型 其他一样 
{
    
}

class Test2<T> where T:new()		//传进来的T必须是一个有公共无参构造函数的类(不能是抽象类)
{
    
}
Test2<Test1> t = new Test2<Test1>();

interface IFly
{
    
}

class Test4 : IFly
{
    
}

class Test3<T, U> where T:U			//传进来的T和U是相同类型或者T是U的派生类型
{
    
}

Test3<Test4, IFly> t3 = new Test3<Test4, IFly>();


//约束的组合使用
class Test5<T> where T:class, new()	//传进来的T必须是类且这个类一定要有公共无参构造
{
    
}

//多个泛型有约束
class Test6<T, K> where T:class, new() where K:struct	//分别约束T和K 
```



## 常用泛型数据结构类



### List

```c#
//可以理解为有泛型的ArrayList
//声明 要命名空间 using System.Collections.Generic
List<int> list = new List<int>();	//相当于一个只能存int型的ArrayList

//增删查改
//增
list.Add(1);						//只能存一开始指定好的类型
list.AddRange(list2);				//可以加入另一个同类型的List
list.Insert(0, 99);					//第0个位置插入99

//删
list.Remove(1);						//删值
list.RemoveAt(0);					//删位置

//查
list[0];							//下标访问
if (list.Contains(1));				//判断是否存在1
int index = list.IndexOf(1);		//正向查找 找到返回位置 没找到返回-1
int index = list.LastIndexOf(1);	//反向查找 找到返回位置 没找到返回-1

//改
list[0] = 9;						//直接用下标改

//遍历
list.Count							//长度
for (int i = 0; i < list.Count; i++)
{
    Console.WriteLine(list[i]);
}

foreach (var item in list)
{
    Console.WriteLine(item);
}
```





### Dictionary

```c#
//可以理解为有泛型的Hashtable c++中的map呗
//声明 要命名空间 using System.Collections.Generic
Dictionary<int, string> d = new Dictionary<int, int>();

//增删查改
//增
d.Add(1, "5");

//删
d.Remove(1);			//删除对应的键 要是没有对应的键则没反应
d.Clear();				//清空

//查
d[1];					//查键为1对应的值 要是没有对应的键会报错 而Hashtable则会返回空 和这个不一样
if (d.ContainsKey(1));	//通过键
if (d.ContainsValue("5"));	//通过值 不像Hashtable 不能用d.Contains(..)查键

//改
d[1] = "0";				//直接通过下标改

//遍历
foreach (var item int d.Keys)
{
    Console.WriteLine(item);
    Console.WriteLine(d[item]);				//遍历键然后打印键对应的值
}

foreach (var item int d.Values)
{
    Console.WriteLine(item);				//遍历并打印所有值
}

foreach (KeyValuePair<int, string> item in d)
{
    Console.WriteLine(item.Key + item.Value);	//直接遍历键值对
}
```





### 顺序存储和链式存储

```c#
//顺序存储 地址连续的存储单元存数据
//链式存储 任一存储单元存储线性表中的各个元素

//实现一个单向链表

class LinkedNode<T>						//充当c++中struct作用存数据还有下一个数据的地址
{
    public T value;
    public LinkedNode<T>nextNode;
    
    public LinedNode(T value)
    {
        this.value = value;
    }
}

class LinkedList<T>
{
    public LinkedNode<T> head;
    public LinkedNode<T> last;
    
    public void Add()
    {
        LinkedNode<T> node = new LinedNode<T>(value);
        
        if (head == null)
        {
            head = node;
            last = head;
            return;
        }
    
    	last.nextNode = node;
        last = node;
    }
    
    public void Remove(T value)
    {
        if (head == null) return;
        
        if (head.value.Equals(value))	//因为value是泛型 没有重载运算符 所以不能用 == 要用Equals
        {
            head = head.nextNode;
            if (head == null)			//只有一个节点的时候尾要清空
            {
                last = null;
            }
            return;
        }
        
        LinkedNode<T> node = head;
        LinkedNode<T> q = head;
        while (node.nextNode != null)
        {
            if (node.nextNode.value.Equals(value))
            {
                node.nextNode = node.nextNode.next.Node;
            }
            node = node.nextNode;
        }
	}
}

//遍历
while (node != null)
{
    Console.WtireLine(node.Value);
    node = node.nextNode;
}
```





### Linklist

```c#
//可变类型的泛型双向链表
//声明 要命名空间 using System.Collections.Generic

LinkedList<int> linkedList = new LinkedList<int>();

//增删查改
//增
linkedList.AddLast(10);			//尾部添加
linkedList.AddFirst(10);		//头部添加
LinkedList<int> node = linked:ist.Find(10);	//找值为10的节点
linkedList.AddAfter(node, 15);	//配合上面那一行 在值为10的节点后面差一个值为15的节点

//删
linkedList.RemoveFirst();		//删除头结点
linkedList.RemoveLast();		//删除尾节点
linkedList.Remove(20);			//删除值为20的节点
linkedList.Clear();				//清空

//查
LinkedList<int> first = linkedList.First;	//得到头结点
LinkedList<int> last = linkedList.Last;		//得到尾节点
LinkedList<int> node = linked:ist.Find(10);	//找值为10的节点
if (linkedList.Contains(10));				//判断10是否存在

//改
LinkedList<int> node = linked:ist.Find(10);	//找值为10的节点
node.value = 1;								//配合上面那行使用 先得到节点再改

//遍历
foreach (int item in linkedList)
{
    Console.WriteLink(item);
}

LinkedList<int> nowNode = linkedList.First;
while (nowNode != null)
{
    ...
    nowNode = nowNode.Next;
}

LinkedList<int> nowNode = linkedList.Last;
while (nowNode != null)
{
    ...
    nowNode = nowNode.Previous;
}
```





### 泛型栈和队列

```c#
Stack<int>stack = new Stack<int>();
Queue<int>queue = new Queue<int>();
//就是把object改为指定类型 使用方法不变
```





## 委托和事件

### 委托

```c#
//有点像c++的函数指针 就是定义一个函数A 然后把A赋值给指针函数 指针函数使用的时候就是A的功能
//委托是函数的容器 用来存储传递函数方法

//基本语法 关键字 delegate 
//delegate 返回值 委托名(参数列表);
//写在namespace和class块中 更多写在namespace中 访问修饰符默认不写为public 一般使用public

delegate void MyFun();		//可以用来存储无返回值函数的容器
delegate int MyFun2(int a);	//不存在重载 两个委托不能重名

static void Fun()
{
    ...
}

static void Fun2(int a)
{
    ...
}

MyFun f = new MyFun(Fun);	//装函数
MyFun f = Fun;				//也可以这样写 注意别写括号
f.Invoke();					//调用f里面装着的函数
f();						//也可以这样写 直接调用f中装着的函数

class Test
{
    public MyFun fun;		//把函数存在类内
    public MyFun2 fun2;
    
    public void TestFun(MyFun fun, MyFun2 fun2)
    {
        this.fun = fun;
        this.fun2 = fun;
    }
}

//委托变量可以存多个函数
MyFun ff = Fun;
ff += Fun;					//ff里面存了两个Fun 所以调用一次ff();会执行两次Fun

//删掉里面存的函数
ff -= Fun;					//减多也不会报错 没反应
ff = null;					//直接清空

//系统定义好的委托
Action f = Fun;				//系统定义好的无参无返回值委托
static int Fun3()
{
    ...
}
Func<int> ff = Fun3;		//泛型委托 无参泛型返回值委托

static void Fun4(int i, string s)
{
    ...
}

Action<int, string> action = Fun4;	 		//可以传n个参数 (最多可以传16个) 注意类型要对应 有参但是无返回值
    
Func<int, int, string> fff = Fun4;			//最后一个是返回值类型 前面的是对应参数类型 (最多传16个)    

//委托支持泛型
delegate T MyFun3<T, k>(T a, K b)
{
    ...
}
```



### 事件

```c#
//一种特殊的变量类型 让委托更具有安全性

//事件的使用 用法和委托几乎一样
//1.不能在类外 赋值 虽然不能赋值 但是可以 加减 去添加或移除记录的函数 如: t.myEvent += Fun; t.myEvent -= Fun;
//2.不能在类外 调用

//声明语法
class Test
{
    public event void myEvent;		//在前面加个Event
}

Test t = new Test();
```





### 匿名函数

```c#
//没有名字的函数 配合委托和事件使用
//基本语法
delegate()
{
    //函数逻辑
};

//使用
//无参无返回
Action a = delegate()
{
    Console.WriteLine("匿名函数逻辑");
}

a();

//有参
Action<int, string> b = delegate (int a, string b)
{
    Console.WriteLine(a);
    Console.WriteLine(b);
}
b(100, "123");

//返回值
Func<string> c = delegate()
{
    return "123";		//直接返回 自动判断返回值类型
}

Console.WriteLine(c());

//一般情况作为函数参数传递 或者 作为函数返回值
class Test
{
    public void Dosomthing(int a, Action fun)
    {
        Console.WriteLine(a);
        fun();
    }
    
    public Action GetFun()
    {
        return delegate()
        {
            ...				
        };
    }
}
Test t = new Test();
t.Dosomething(100, delegate(){
   ....					//要传入的函数逻辑 
});

Action ac = delegate()
{
  ...					//也可以  
};

Action ff = t.GetFun();	//接收返回值
ff();					//调用
t.GetFun()();			//这样直接调用也可以
```





### lambda表达式

````c#
//可以理解为匿名函数的简写 除了写法不同使用上和匿名函数一模一样

//表达式语法
//(参数列表) =>
//{
//	函数体
//}

//无参
Action a = () => 
{
    Console.WriteLine("无参数");
};
a();

//有参
Action<int> a2 = (int value) =>
{
    Console.WriteLine("有参数");
};

Action<int> a3 = (value) =>			//value前的int可以省略 直接匹配a3前面定义的类型
{
    Console.WriteLine("有参数");
};

//有返回值
Func<string, int> a4 = (value) =>
{
    Console.WriteLine(value);
    return 1
}
Console.WriteLine(a4("123123"));	//输出为 123123  1

//闭包

class Test
{
    public event Action action;
    
    public Test()
    {
        int value = 10;					//正常情况当构造函数执行完毕时value会被释放
        
        action = () =>
        {
            Console.WtireLine(value);	//value在事件或委托中使用 生命周期改变 即使构造函数执行完毕value也不会被释放 这就是闭包
        };
        
        for (int i = 0; i <= 10; i++)
        {
            action += () =>
            {
              Console.WriteLine(i);	//如果运行action()会输出十个11(本质都是i) 因为i本来应该被释放 但是产生了闭包 而闭包只会提供最终值则是11
            };
        }
        
        for (int i = 0; i <= 10; i++)
        {
            int index = i;
            action += () =>
            {
              Console.WriteLine(index);		//这个就会依次输出1到10 因为每次循环index都会被清除 每个index都是不一样的
            };
        }
    }
}
````





## List排序

```c#
//引用命名空间 using System.Collections.Generic
//List自带的排序方法
List<int> list = new List<int>();
list.Add(3);
list.Add(2);
list.Add(6);
list.Sort();		//自带的排序 默认为升序排序 即从小到大 ArrayList用法一样

//自定义类的排序
class Item : IComparable<Item> 	//系统自带的接口 <>里是泛型的类型 相当于c++的重载＜用来排序 不写泛型也可以 但是下面的类型要用object 注意用as点出类型
{
    public int money;
    
    public Item(int money)
    {
        this.money = money;
    }
    
    public int CompareTo(Item other)
    {
        //返回值的含义
        //小于0 放在传入对象的前面
        //等于0 保持当前位置不变
        //大于0 放入传入对象的后面
        
        //可以简单理解 传入对象的位置是0
        //如果返回为负数就放在左边
        //如果为整数 就放在他的右边
        if (this.money > other.money) return 1;	//如果比其他的money大就返回正数放在后面 相当于升序排序
        else return -1;
    }
}

static int SortItemMoney (Item a, Item b)
{
    //返回值规则和之前一样
    //以b为基准 相当于b位置为0 返回正数放右边 负数放左边
    if a(a.money > b.money) return 1;	//如果a大于b返回正数放到b的右边 实现升序排序
    else return -1;						
}

List<Item> itemlist = List<Item>();
itemlist.Add(new Item(2));
itemlist.Add(new Item(1));	
itemlist.Sort();						//根据类内重写好的规则排序 也就是按照money进行降序排序
itemlist.Sort(SortItemMoney);			//通过函数写比较规则
itemlist.Sort(delegate (Item a, Item b) //通过匿名函数实现
              {
 	   				if a(a.money > b.money) return 1;
    				else return -1;
              });
itemlist.Sort((a, b) => 	
              {
                  return a.money > b.money ? 1 : -1;
              });						//lambda表达式和三目运算符实现
```





## 协变逆变

```c#
//协变 和谐的变化 如子类变父类 string 变 object
//逆变 逆常规变化 如 object 变 string
//用于在泛型中 修饰泛型字母 只有泛型接口和泛型委托可以使用

//用out修饰的泛型 只能作为返回值
delegate T TestOut<out T>();	//T类型只能作为返回值 不能作为参数之类

 //in修饰的泛型 只能作为参数 
delegate void TestIn(in T)(T t);//T类型只能作为参数

class Father
{
    ...
}

class Son : Father
{
    ...
}

//协变
TestOut<Son> os = () =>
{
    return new Son();
};

TestOut<Father> of = os;	//如果上面的delegate T TestOut<out T>();中没有out则会报错 因为有父子关系判断不出来 加了out才行
Father fa = of();			//这里面实际装的是Sun

//逆变
TestIn<Father> iF = (value) =>
{
    
};
TestIn(Son) iS = iF;
iS(new Son());				//传入的是Son实际上调用的是iF 而iF中的value装的是Son 本质还是父类装子类
```



##　多线程

```c#
//语法相关 引用命名空间using System.Threading;
//声明一个新的线程 
//注意 线程执行的代码需要封装到一个函数内
//线程就相当于另外多开了一个程序页 然后两个程序页的内容同时执行
Thread t = new Thread(NewThreadLogic);
static void NewThreadLogic()
{
    while (ture)
    {
        Console.WriteLine("dasd");
    }
}

//启动线程
t.start();     				//会执行存在里面的逻辑

//设置为后台线程 
//主线程(即主函数)中只有Thread t = new Thread(NewThreadLogic); t.start(); 两个语句 调用完t.start()相当于开了另一个程序页并且已经开好了,那么我这个程序页的东西已经执行完了应该马上关闭 不管里面是否有循环 因为主线程已经结束了 所以相当于住程序页结束了 其他程序页执行的也该停下 所以不应该被卡住
//直接调用
t.start();					//会一直被循环卡住 不断输出
t.IsBackground = true;		//设置为后台线程
t.start();					//只输出几行 因为设置为后台线程 前台线程结束后台线程也跟着结束 可以理解主函数就是前台线程 执行完t.start()不管里面的内容是什么 都会直接结束 t.start()只能在他结束的时间里赶紧输出几行出来

//关闭释放一个线程 (不是死循环的线程可以不用关闭释放)
t = null;
t.Abort();				//部分版本会报错 建议配合try catch使用

//线程的休眠
Thread.Sleep();			//休眠多少毫秒 写在哪都可以 主函数里也可以
static void NewThreadLogic()
{
    while (ture)
    {
        Thread.Sleep(10);			//每个循环休眠10毫秒
        Console.WriteLine("dasd");
    }
}

//各个线程的内存是共享的 如果同时改同一个内存区 难以区分先后 会出现问题
//比如一个线程将输出颜色设置为红色 另一个设置为黄色 那么画出来的图形黄红闪烁 因为他们是同时执行 没有先后
//通过加锁解决 lock 影响线程效率
static object obj = new object();	//可以理解为这就是仅有一个的宝物 多个线程去抢 如果obj正被别的线程锁住 那么其他线程都不会执行 等拥有这个宝物的线程执行完之后他会解锁这个宝物 给其他的线程抢去用 然后别的线程又要等锁了宝物的那个线程执行完 就是只有有obj的线程才能执行他里面的代码
lock(引用对象)
{
    ...				//里面写代码
}

static void NewThreadLogic()
{
    lock(obj)
    {
        Console.ForegroundColor = ConsoleColor.Red;
        Console.SetCursorPosition(0, 0);
        Console.WriteLine("111");
    }
}

static void NewThreadLogic2()
{
    lock(obj)
    {
        Console.ForegroundColor = ConsoleColor.Yellow;
        Console.SetCursorPosition(2, 2);
        Console.WriteLine("222");
    }
}

```





### 预处理器指令

```c#
//在比你以前对信息进行预处理 如c++中的#define int long long
//常见预处理指令

//define
#define Unity5			//定义一个没有意义的符号 配合后面使用
#define Unity6
#define Unity4
#undef Unity4			//取消定义
    
//#if #elif #else #endif 
#if Unity5	&& Android							//可以用关系运算符
    Console.WriteLine("版本为Unity5");			//如果上面有#define Unity5 就会执行其中的代码
	#waring 这个版本 不合法						//这样就会在下面的提示栏提示 就是黄色三角的提示
    #error 这个版本不准执行							//直接编译都编译不了 直接报错 
#elif Unity6 && IOS								//如果没有Unity5则看看有没有Unity6
    ....
#else
 	...											//如果上面都没有 
#endif											//必须和#if配对出现
```



## 反射和特性

### **反射（Reflection）**

#### **1. 概念**

- **程序集（Assembly）**：代码集合，如 `.dll` 和 `.exe` 文件。
- **元数据（Metadata）**：程序中的类、方法、变量等信息，保存在程序集中。
- **反射（Reflection）**：通过反射可以查看程序集中的元数据，并动态调用代码。

#### **2. 基本用法**

- **类定义(自己编就可以了)**

	```c#
	//语法相关
	class Test
	{
	    public int i = 1;
	    public int j = 0;
	    public string str = "123";
	
	    public Test() { }
	    public Test(int i) { this.i = i; }
	    public Test(int i, string str) :this(i) {this.str = str; } //前面的this(i)相当于限制性一次上面的那个构造函数在执行自己的内容
	
	    public void Speak()
	    {
	        Console.WriteLine(str);
	    }
	
	    public int GetAge()
	    {
	       return 25;
	    }
	}
	```

- **获取 `Type` 对象**

	```csharp
int a = 42;
	Type type = a.GetType(); // 通过对象获取 Type
	Type type2 = typeof(int); // 通过类型名获取 Type
	Type type3 = Type.GetType("System.Int32"); // 通过完整类型名获取 Type Type是一个类 所以这里得到的Type这个类的类型
	```
	
- **获取程序集信息**

	```csharp
	Console.WriteLine(type.Assembly); // 获取程序集信息 (很少用)
	```

- **获取类的公共成员**

  ```csharp
  Type t = typeof(Test); // 获取 Test 类的 Type 对象 如果是别的程序集中的类要用命名空间.类名来获取
  MemberInfo[] infos = t.GetMembers(); // 获取所有公共成员 (包括函数和变量)
  foreach (var info in infos)
  {
      Console.WriteLine(info);
  }
  //以下是打印出来的内容 .ctor是构造函数 有无参和有参   还有公共成员变量 和 公共成员函数
  Void .ctor()
  Void .ctor(Int32)
  Void .ctor(Int32, System.String)
  Int32 i
  Int32 j
  System.String str
  Void Speak()
  Int32 GetAge()
  ```

- **获取构造函数**

	```csharp
	ConstructorInfo[] ctors = t.GetConstructors(); // 获取所有构造函数
	foreach (var ctor in ctors)
	{
	    Console.WriteLine(ctor);
	}
	//Void .ctor()  打印出来是这样的 三个构造函数
	//Void .ctor(Int32)
	//Void .ctor(Int32, System.String)
	```

- **通过构造函数创建对象**

	```csharp
	ConstructorInfo info = t.GetConstructor(new Type[0]); // 获取无参构造函数
	Test obj = (Test)info.Invoke(null); //执行无参构造 括号内传null 并且通过无参构造创建了个一个Object类的对象 as之后赋给Test类对象 则obj是一个完整的Test对象(即是一个实例 这句话相当于 Test obj = new Test())包含里面的所有属性和方法
	Console.WriteLine(obj.j);	//这个时候obj已经是一个实例了 可以直接访问里面的成员变量j
	
	ConstructorInfo info2 = t.GetConstructor(new Type[] { typeof(int) }); // 获取有参构造函数
	obj = (Test)info2.Invoke(new object[] { 2 }); // 创建对象
	Console.WriteLine(obj.str);	//打印出这个实例对象了的str成员变量
	
	ConstructorInfo info3 = t.GetConstructors(new Type[]{typeof(int), typeof(string)});//有两个参数 一个为int 一个为string的构造函数
	obj = info3.Invoke(new object[]{ 2, "22222" }) as Test;
	```

- **获取和设置对象的值**

  ```csharp
  FieldInfo[] fieldInfos = t.GetFields(); // 获取所有公共成员变量
  foreach (var field in fieldInfos)
  {
      Console.WriteLine(field);
  }
  //Int32 i      Int32 j           System.String str打印出来会是这种 都是公共成员变量的类型
  
  FieldInfo infoJ = t.GetField("j"); // 获取指定名称的成员变量 j是变量名
  Test test = new Test();
  test.j = 99;
  //获取对象的值 看着很鸡肋啊 但是是因为这是在一个程序集里面 如果在不同的程序集你都不知道这个test是什么类型 他就默认是object类 不能像上面用as创建出来实例化对象的Test对象 并且你也new不出来一个实例化对象 因为Test根本不在一个程序集里面 你只能用反射去访问
  Console.WriteLine(infoJ.GetValue(test)); // 获取变量 因为infoJ上面设定好了是j 所以下面两个都是在对j操作
  infoJ.SetValue(test, 100); // 设置变量 
  ```

- **获取和调用方法**

	```csharp
	//获得类中的公共成员方法 (下面获得是c#自带的string类中公共成员的方法)
	Type strType = typeof(string);
	//如果方法存在重载 用typeof表示参数类型
	MethodInfo[] methods = strtype.GetMethods();	//获得string类型的公共成员方法
	for (int i = 0; i < methods.Length; i++)
	{
	    Console.WriteLine(methods[i]);
	}
	MethodInfo subStr = strType.GetiMethod("Substring",
	                                      new Type[] {typeof(int), typeof(int)});//获得string类中的Substring方法
	
	//调用该方法
	//如果是静态方法 Invoke中传null即可
	string str = "Hello,World!";
	//第一个参数相当于是哪个对象要执行这个成员方法
	object result = subStr.Invoke(str, new object[]{ 6, 6}); //这段代码相当于 result = str.Substring(6, 6);
	Console.WriteLine(result);			//打印World!
	```

------

### **Activator 和 Assembly **

#### **1. Activator**

- **快速实例化对象**

	```csharp
	//用于快速实例化对象的类
	//用于将Type对象快捷实例化为对象
	Type testType = typeof(Test);//注意代码和类不在一个程序集要用 命名空间.类名
	//这里的Test类和上面那个笔记中的Test类定义是一样的
	//无参构造
	Test testobj = Activator.CreatInstance(testType) as Test;	//如果Test不在一个程序集里要用Object来接
	Console.WriteLine(testobj.str);
	
	//有参构造
	testobj = Activator.CreatInstance(testType, 99) as Test;	//只有一个参数的 
	testobj = Activator.CreatInstance(testType, 99, "123") as Test;	//两个参数的 
	
	```

#### **2. Assembly**

- **加载程序集**

	```csharp
	//主要用来加载其他程序集
	//加载后才能用Type来使用他程序集中的信息
	//先加载一个指定程序集
	Assembly assembly = Assembly.LoadForm(@"绝对路径(或相对路径?)");	//@是取消双引号里面的转义字符不然路径的斜杠用不了 也可以用双斜杠代表一个斜杠
	Type[] type = assembly.GetTypes();
	Type icon = assembly.GetType("Lesson_18练习题.Icon");			//获得对应程序集里面的Icon类
	MemberIcon[] members = icon.GetMembers();		//获得类中的公共成员 (包括方法和变量)
	```

- **通过反射实例化对象**

	```csharp
	//通过反射 实例化一个icon对象
	Type moveDir = assembly.GetType("Lesson_18练习题.E_MoveDir");		//获得要传入的参数类型
	FieldInfo right = moveDir.GetField("Right");					//得到E_MoveDir中的一个成员变量 这还只是一个反射信息 并不是一个E_MoveDir的类型 right.GetValue(null)才是E_MoveDir类型
	//直接实例化对象 这段代码相当于 Icon iconObj = new Icon(10, 5, right);	//第三个参数是Icon类里面的枚举类型变量
	Object iconObj = Activator.CreateInstance(icon, 10, 5, right.GetValue(null));
	//FieldInfo fildwidth = icon.GetField("width");
	//fildwidth.SetValue(iconObj, 15);			相当于iconObj.width = 15 可以通过这种方法更改类中成员变量的值
	```

- **调用对象方法**

	```csharp
	//通过反射得到对象中的方法
	Method move = icon.GetMethod("Move");
	Method draw = icon.GetMethod("Draw");
	Method clear = icon.GetMethod("Clear");
	
	Console.Clear();
	while(true)			//调用创建好的iconObj类 中的成员方法实现之前Lesson_18中实现的蛇头移动
	{
	    Thread.Sleep(1000);
	    clear.Invoke(iconObj, null);
	    move.Invoke(iconObj, null);
	    draw.Invoke(iconObj, null);
	}
	
	//类库工程的创建 
	//新建项目 新建类库(.NET framework) 在里面写代码 运行不了只能写代码 在vs中对文件右键 生成
	//.dll文件会存在他对应文档的bin中
	```

---

### **特性（Attributes）**

#### **1. 自定义特性**

- **定义特性**

	```csharp
	//特性是个类 可以利用特性类为元数据添加额外信息
	
	//自定义特性 继承自特性基类 Attribute
	class MyCustomAttribute : Attribute
	{
	    public string info;
	    
	    public MyCustomAttribute(string info)
	    {
	        this.info = info;
	    }
	    
	    public void TestFun()
	    {
	        ...
	    }
	}
	
	```

- **使用特性**

	```csharp
	//特性的使用
	//基本语法: [特性名(参数列表)]
	[MyCustom("额外信息")]	//虽然类名是MyCustomAttribute 但是Attribute系统会自动帮你省略 你光写MyCustom系统也认得出来
	class MyClass
	{
	    [MyCustom("这是一个用于计算加法的函数")]				//函数 参数 类都可以加特性
	    public TestFun([MyCustom("函数参数")int a])
	    {
	        ...
	    }
	    
	    [MyCustom("这是一个变量")]
	    int x;
	}
	
	```
	
- **获取和使用特性**

	```csharp
	MyClass mc = new MyClass();
	Type t = mc.GetType();
	Type t = typeof(MyClass);	//和上面那句效果是一样的
	
	//参数1: 特性的类型 参数2: 代表是否搜索继承链(属性和事件忽略此参数) 就是可能自己没有特性但是父类可能会有
	if (t.IsDefined(typeof(MyCustomAttribute), false));		//只会检测类是不是有特性 类中的成员变量成员方法都不检测
	{
	    Console.writeLine("该类型应用了MyCustom特性")
	}
	
	object[] array = t.GetCustomAttribute(true);	//得到所有的修饰特性 括号内也是是否搜索继承链
	//array中输出的内容将是每个特性的类型名称和构造函数参数，类似于以下格式：
	//MyNamespace.MyCustomAttribute
	
	Type attribute = typeof(MyCustomAttribute);
	if (t.GetCustomAttribute(MyCustomAttribute) != null);	//可以用来判断t中有没有MyCustomAttribute特性
	for (int i = 0; i < array.Length; i++)
	{
	    if (array[i] is MyCustomAttribute)
	    {
	        Console.WriteLine((array[i] as MyCustomAttribute).info);	//打印对应类 变量 函数的特性中写的信息
	        (array[i] as MyCustomAttribute).TestFun();	//甚至可以调用他们对应特性中的方法
	    }
	}
	
	//通过为特性类 加特性 限制其使用范围
	[AttributeUsage(AttributeTargets.Class | AttributeTargets.Struct, AllowMultiple = true, Inherited = true)]
	//参数一: AttributeTargets - 特性能用在哪些地方 上面写的就是能用在类和结构体 按住ctrl点进去可以查看变量和函数是什么类型 如变量是Filed
	//参数二: AllowMultiple - 是否允许多个特性实例用在同一个目标上
	//参数三: Inherited - 特性是否能被派生类和重写成员继承 就比如有人继承上面的MyClass那么他也会有MyClass中的特性信息
	```

#### **2. 系统自带特性**

- **过时特性（Obsolete）**

  ```csharp
  //系统自带特性-过时特性 Obsolete
  //用于提示用户 使用的方法等成员已经过时 建议使用新方法
  class TestClass
  {
      //参数一:调用过时方法时　提示的内容
      //参数二: true-使用该方法时会报错(程序直接终止) flase-使用该方法时直接警告(就是黄色三角的提示 不会使程序终止)
      [Obsolete("OldSpeak方法已经过时了, 请使用Speak方法"), true]
      public void OldSpeak()
      {
          ...
      }
      
      public void Speak()
      {
          ...
      }
      
      public void SpeakCaller(string str, [CallerFilePath]string fileName = "", [CallerLineNumber]int line = 0, [CallerMemberName]string target = "")	{..}
  ```

- **调用者信息特性（Caller Information）**

	### 代码解析

	```csharp
	public void SpeakCaller(string str, 
	                        [CallerFilePath] string fileName = "", 
	                        [CallerLineNumber] int line = 0, 
	                        [CallerMemberName] string target = "")
	{
	    // 在这里可以使用 fileName、line 和 target
	    Console.WriteLine($"Message: {str}");
	    Console.WriteLine($"Called from file: {fileName}");
	    Console.WriteLine($"Line number: {line}");
	    Console.WriteLine($"Member name: {target}");
	}
	//这段代码展示了如何使用 `CallerMemberName`、`CallerFilePath` 和 `CallerLineNumber` 特性来自动填充调用方法的相关信息。这些特性是 C# 提供的内置特性，用于在运行时获取调用方法的信息，而无需手动传递这些信息。
	```

	### 特性的作用

	1. **`[CallerMemberName]`**：
		- 自动填充调用方法的名称。
		- 如果没有显式传递参数，编译器会自动将调用方法的名称作为参数值。
	2. **`[CallerFilePath]`**：
		- 自动填充调用方法所在的文件的路径。
		- 如果没有显式传递参数，编译器会自动将调用方法所在的文件路径作为参数值。
	3. **`[CallerLineNumber]`**：
		- 自动填充调用方法所在的行号。
		- 如果没有显式传递参数，编译器会自动将调用方法所在的行号作为参数值。

	### 参数的默认值

	- **`fileName = ""`**：
		- 这是一个默认值。如果没有显式传递参数，编译器会自动填充调用方法所在的文件路径。
		- **注意**：必须提供默认值（如 `""`），否则编译器会报错。
	- **`line = 0`**：
		- 这是一个默认值。如果没有显式传递参数，编译器会自动填充调用方法所在的行号。
		- **注意**：必须提供默认值（如 `0`），否则编译器会报错。
	- **`target = ""`**：
		- 这是一个默认值。如果没有显式传递参数，编译器会自动填充调用方法的名称。
		- **注意**：必须提供默认值（如 `""`），否则编译器会报错。

	### 示例

	假设你有以下代码：

	```csharp
	public class MyClass
	{
	    public void SpeakCaller(string str, 
	                            [CallerFilePath] string fileName = "", 
	                            [CallerLineNumber] int line = 0, 
	                            [CallerMemberName] string target = "")
	    {
	        Console.WriteLine($"Message: {str}");
	        Console.WriteLine($"Called from file: {fileName}");
	        Console.WriteLine($"Line number: {line}");
	        Console.WriteLine($"Member name: {target}");
	    }
	}
	
	public class Program
	{
	    public static void Main()
	    {
	        MyClass obj = new MyClass();
	        obj.SpeakCaller("Hello, World!");
	    }
	}
	```

	运行时输出：

	```
	Message: Hello, World!
	Called from file: C:\path\to\Program.cs
	Line number: 10
	Member name: Main
	```

	### 解释

	- **`Message: Hello, World!`**：
		- 这是传递给 `SpeakCaller` 方法的 `str` 参数。
	- **`Called from file: C:\path\to\Program.cs`**：
		- 这是调用 `SpeakCaller` 方法的文件路径，由 `CallerFilePath` 特性自动填充。
	- **`Line number: 10`**：
		- 这是调用 `SpeakCaller` 方法的行号，由 `CallerLineNumber` 特性自动填充。
	- **`Member name: Main`**：
		- 这是调用 `SpeakCaller` 方法的方法名称，由 `CallerMemberName` 特性自动填充。

	### 注意事项

	- **默认值的必要性**：
		- 必须为这些特性参数提供默认值，否则编译器会报错。
		- 默认值通常为空字符串 `""` 或 `0`。
	- **用途**：
		- 这些特性通常用于日志记录、调试信息、性能监控等场景，可以减少手动传递调用信息的繁琐操作。

- **条件编译特性（Conditional）**

  ```csharp
  //系统自带特性-条件编译特性 Conditional
  //他会预处理指令 #define配合使用 需要有引用命名空间 using System.Diagnostics;
  //主要用在调试代码上 有时想执行又是不想执行的代码
  
  [Conditional("Fun")]				
  static void Fun()
  {
      Console.WriteLine("Fun执行")
  }
  Fun();								//如果上面有#define Fun 那么这个函数才会被执行 不然不会被执行
  ```

- **外部 DLL 特性（DllImport）**

	```csharp
	//系统自带特性-外部Dll包函数特性
	//用来标记非.Net(c#)的函数, 表明该函数在一个外部的Dll中定义
	//一般用来调用 C或者C++的Dll包写好的方法
	//需要引用命名空间 using System.Runtime.InteropServices
	
	[DllImport("Test.dll(dll包的文件名或者路径)")]
	public static extern int Add(int a, int b);		//用的是C或C++中写好的方法 执行的是C或C++中的逻辑
	```

------

### **总结**

1. **反射**：通过反射可以动态获取程序集中的元数据，并调用方法、访问字段等。
2. **Assembly 和 Activator**：`Assembly` 用于加载程序集，`Activator` 用于快速实例化对象。
3. **特性**：特性用于为元数据添加额外信息，系统自带特性（如 `Obsolete`、`CallerMemberName` 等）提供了丰富的功能。



## 迭代器

```c#
//标准迭代器的实现方法
//关键接口: IEnumerator, IEnumerable
//命名空间: using system.Collections;
//可以通过同时继承IEnumerator和IEnumerable实现其中的方法
class CustomList : IEnumerable, IEnumerator
{
    int list[];
    
    int position = -1;
    
    public CustomList
    {
        list = {1, 2, 3, 4, 5};
    }
    
    //public IEnumerable GetEnumerator()		//实现(IEnumerable)接口里的方法
    // {
    //     throw new NotImplementedException();
    // }
    
    // public IEnumerator GetEnumerator()		//实现(IEnumerator)接口里的方法
    // {
    //     throw new NotImplementedException(); 
    // }
    
    // public object Current => throw new NotImplementedException();
    
    // public bool MoveNext()
    // {
    //     throw new NotImplementedException();
    // }
    
    // public void Reset()
    // {
    //     throw new NotImplementedException();
    // }
    
    //以下是对(IEnumerator)接口里的方法 当然上面的那些是要删掉的
    public IEnumerator GetEnumerator()
    {
        Reset();
        return this;
    }
    
    public object Current
    {
        get
        {
            return list[position];		//迭代器得到的是什么
        }
    }
    
    public bool MoveNext()
    {
        //用来判断迭代器是否遍历结束的
        ++position;
        return position < list.Length;
    }
    
    public void Reset()
    {
        //结束之后的复原 放在public IEnumerator GetEnumerator()里面用
        position = -1;
    }
}

CustomList list = new CutomList();
//foreach本质
//1.先获取in后面这个对象 IEnumerator会调用对象其中的GetEnumerator方法来获取
//2.执行得到这个IEnumerator对象中的 MoveNext方法
//3.只要MoveNext方法的返回值是true 就会去得到Current 然后复制给item
foreach (int item in list)
{
    Console.WriteLine(item);			//根据上面重写了GetEnumerator中的逻辑这里就会输出CustomList类中的list数组的内容
}


//用yield语法糖实现迭代器 将复杂逻辑简单化 增加程序可读性 
//关键接口: IEnumerable 命名空间: using System.Collections;

class CustomList2 : IEnumerable			//和上面的用迭代器的效果一样
{
    int[] list;
    
    CustomList2()
    {
        list = {1, 2, 3, 4};
    }
    
    public IEnumerator GetEnumerator()
    {
        for (int i = 0; i < list.Length; i++)
        {
            yield return list[i];
        }
        //yield return list[0]; yield return list[1];...也可以 
    }
}
```





## 特殊语法

```c#
//var隐式类型 C++中的auto 可以用来表示任意类型的变量 但是必须要初始化且不能作为类的成员 只能用于临时变量的声明 
var i = 1; var str = "123";		//一旦定义下来类型就不会变了

//设置对象初始值 声明对象时 直接通过大括号初始化公共成员变量和属性
class Person
{
    public int money;
    public bool gender;
}
Person p = new Person() {gender = true, money = 0};		//会先执行构造函数再执行大括号里面的内容

//设置集合初始值
int[] array = new int[] {1, 2, 3};
List<int>listInt = new List<int>(){1, 2, 3};
List<Person>listInt = new List<Person>(){1, 2, 3}
{
  new Person(),
  new Person(){money = 1}
};
Dictionary<int, string> dic = new Dictionary<int, string>()
{
    {1, "123"},
    {2, "123321"}
}

//匿名类型
var v = new{age = 10, money = 11};			//相当于一个匿名类 只能存变量不能存函数
Console.WriteLine(v.age);

//可空类型
int? c = null;
if (c.HasValue) Console.WriteLine(c);		//一定要判断他是否为空才能输出不然会报错
int? value = null;
Console.WriteLine(value.GetValueDefault());	//如果是空就会返回值类型的默认值 (100)若括号里面填了一百且是空就会返回100

object o = null;
Console.WriteLine(o?.ToString());			//如果o是空就不会执行ToString() 防止o是空时执行报错
//委托 数组 类为空的时候都可以这样判断是否要执行

//空合并操作符
int? intV = null;
int intI = intV == null ? 100 : intV.Value;	//右边不能直接写intV要写intV.Value因为是用的int存null 所以会报错
intI = intV ?? 100;			//相当于上面的三目运算符的简便写法 左边值为空就赋右边 否则赋左边 ??帮忙特殊处理了intV所以不用写成intV.Value

//内插字符串
//关键符号: $
string name = "xxx";
Console.WriteLine($"{name},好好学习");

//单句逻辑简略写法
if (true) 					//一句代码省略大括号
    Console.WriteLine("123");	
//在类中成员属性的简略写法
public string Name
{
    get => "xxx";
    set => sex = value;
}
//函数也可以
public int Add(int x, int y) => x + y;	//有返回值就直接把这个当返回值返回回去
public void Speak(string str) => Console.WriteLine(str);	//有逻辑就直接执行逻辑
```









## —————C#进阶——————



# 补充未讲解全面的内容：命名和可选参数

- 命名参数允许调用方法时按参数名指定参数值，不必匹配参数顺序。
- 可选参数允许跳过某些参数，直接赋值后面的默认参数。

```c#
//有了命名参数，我们不用匹配参数在所调用方法中的顺序
//每个参数可以按照参数名字进行指定
Test(1, 1.2f, true);
Test(f: 3.3f, i: 5, b: false);
Test(b: false, f: 3.4f, i: 3);

//命名参数可以配合可选参数使用,让我们做到跳过其中的默认参数直接赋值后面的默认参数
Test2(1, true, "234");
Test2(1, s: "234");

//好处：可以让我们更方便的调用函数，少写一些重载函数

public void Test(int i, float f, bool b)
{

}

public void Test2(int i , bool b = true, string s = "123")
{

}
```





# 补充未讲解的内容：动态类型

- `dynamic`关键字用于绕过编译时类型检查，改为运行时解析操作。
- 动态类型在大多数情况下行为类似`object`类型，但编译器不会对包含`dynamic`类型的表达式进行解析或类型检查。
- 注意：
  1. 使用`dynamic`功能需要将Unity的.NET API兼容级别切换为.NET 4.x。
  2. IL2CPP不支持C# `dynamic`关键字。
  3. 动态类型无法自动补全方法，书写时需保证方法拼写正确。

```
dynamic dyn = 1;
object obj = 2;

dyn += 2;

print(obj.GetType());
print(dyn.GetType());
print(dyn);

object t = new Test1();
dynamic tmp = t;
tmp.TestTest();
```









# 回顾线程 学习线程池

## 回顾知识点——线程

1. Unity 支持多线程。
2. 在 Unity 中开启的多线程不能使用主线程中的对象。
3. 在 Unity 中开启多线程后，必须记住关闭线程。

示例代码：
```csharp
Thread t = new Thread(() => {
    while (true) {
        print("123");
        Thread.Sleep(1000);
    }
});
t.Start();
print("主线程执行");

private void OnDestroy()	//就算Unity停止运行线程也还是会执行 所以要在这里关闭线程
{
    t.Abort();
}
```

## 补充知识点——线程池

命名空间：`System.Threading`
类名：`ThreadPool`（线程池）

在多线程应用程序开发中，频繁创建和删除线程会带来性能消耗和内存垃圾。为了避免这种开销，C# 推出了线程池 `ThreadPool` 类。

线程池中有若干数量的线程，当有任务需要处理时，会从线程池中获取一个空闲的线程来执行任务。任务执行完毕后，线程不会销毁，而是被线程池回收以供后续任务使用。当线程池中所有的线程都在忙碌时，又有新任务要处理时，线程池才会新建一个线程来处理该任务。如果线程数量达到设置的最大值，任务会排队，等待其他任务释放线程后再执行。线程池能减少线程的创建，节省开销，可以减少垃圾回收（GC）的触发。

线程池相当于一个专门装线程的缓存池。优点是可以节省开销，减少线程的创建，进而有效减少 GC 触发。缺点是不能控制线程池中线程的执行顺序，也不能获取线程池内线程取消/异常/完成的通知。

`ThreadPool` 是一个静态类，里面提供了很多静态成员，其中相对重要的方法有：

1. 获取可用的工作线程数和 I/O 线程数。
2. 设置线程池中可以同时处于活动状态的工作线程的最大数目和 I/O 线程的最大数目。
3. 获取线程池中工作线程的最大数目和 I/O 线程的最大数目。
4. 设置工作线程的最小数目和 I/O 线程的最小数目。
5. 获取线程池中工作线程的最小数目和 I/O 线程的最小数目。
6. 将方法排入队列以便执行，当线程池中线程变得可用时执行。

示例代码：
```csharp
//获取可用的工作线程数和I/O线程数 即整个系统可以开的最大数量
int num1, num2;
ThreadPool.GetAvailableThreads(out num1, out num2);
print(num1);
print(num2);

//设置线程池中可以同时处于活动状态的工作线程的最大数目和I/O线程的最大数目
//更改成功返回true，失败返回false
if (ThreadPool.SetMaxThreads(20, 20))
{
    print("更改成功");
}

//获取线程池中工作线程的最大数目和I/O线程的最大数目  如果没有设置过就默认是系统最大的数量
ThreadPool.GetMaxThreads(out num1, out num2);
print(num1);
print(num2);

//设置工作线程的最小数目和I/O线程的最小数目
if (ThreadPool.SetMinThreads(5, 5))
{
    print("设置成功");
}

//获取线程池中工作线程的最小数目和I/O线程的最小数目	没设置的话默认是 16 16 就是默认池子里有多少个线程可以用
ThreadPool.GetMinThreads(out num1, out num2);	
print(num1);
print(num2);

//将方法排入队列以便执行，当线程池中线程变得可用时执行	第一个参数就是线程函数 第二个参数就直接传给了obj用
for (int i = 0; i < 10; i++)	//打印出来是乱序的 无法控制
{
    ThreadPool.QueueUserWorkItem((obj) =>
    {
        print("第" + obj + "个任务");
    }, i);
}

print("主线程执行");
```









# Task任务类

### 认识 Task
- **命名空间**：`System.Threading.Tasks`
- **类名**：`Task`
- **描述**：`Task` 是对线程的封装，基于线程池，简化了多线程开发，易于控制。

### 创建无返回值 Task 的三种方式
1. **通过 `new Task` 对象传入委托函数并启动**
   ```csharp
   Task t1 = new Task(() =>
   {
       while (isRunning)
       {
           Console.WriteLine("方式一:" + i);
           ++i;
           Thread.Sleep(1000);
       }
   });
   t1.Start();
   
   private void OnDestroy()	
   {
       isRunning = false;
   }
   ```
2. **通过 `Task.Run` 静态方法传入委托函数**
   ```csharp
   Task t2 = Task.Run(() =>
   {
       while (isRunning)
       {
           Console.WriteLine("方式二:" + i);
           ++i;
           Thread.Sleep(1000);
       }
   });
   ```
3. **通过 `Task.Factory.StartNew` 静态方法传入委托函数**
   ```csharp
   Task t3 = Task.Factory.StartNew(() =>
   {
       while (isRuning)
       {
           Console.WriteLine("方式三:" + i);
           ++i;
           Thread.Sleep(1000);
       }
   });
   ```

### 创建有返回值的 Task
1. **通过 `new Task` 对象传入委托函数并启动**
   ```csharp
   Task<int> t1 = new Task<int>(() =>
   {
       while (isRunning)
       {
           Console.WriteLine("方式一:" + i);
           ++i;
           Thread.Sleep(1000);
       }
       return 1;
   });
   t1.Start();
   
   print(t1.Result); 
   ```
   
2. **通过 `Task.Run` 静态方法传入委托函数**
   ```csharp
   Task<string> t2 = Task.Run<string>(() =>
   {
       while (isRunning)
       {
           Console.WriteLine("方式二:" + i);
           ++i;
           Thread.Sleep(1000);
       }
       return "1231";
   });
   
   print(t2.Result); 
   ```
   
3. **通过 `Task.Factory.StartNew` 静态方法传入委托函数**
   
   ```csharp
   Task<float> t3 = Task.Factory.StartNew<float>(() =>
   {
       while (isRunning)
       {
           Console.WriteLine("方式三:" + i);
           ++i;
           Thread.Sleep(1000);
       }
       return 4.5f;
   });
   
   print(t3.Result); 
   ```
   
4. ```
	注意：
	Resut获取结果时会阻塞线程
	即如果task没有执行完成
	会等待task执行完成获取到Result
	然后再执行后边的代码,也就是说 执行到这句代码时 由于我们的Task中是死循环 
	所以主线程就会被卡死
	print(t1.Result);
	print(t2.Result);
	print(t3.Result);
	```





### 同步执行 Task

```csharp
Task t = new Task(() =>
{
    Thread.Sleep(1000);
    Console.WriteLine("哈哈哈");
});
t.RunSynchronously();
Console.WriteLine("主线程执行");
```

- 会先等待一秒 输出“哈哈哈” 然后再输出“主线程执行”





### Task 中线程阻塞的方式（任务阻塞）

1. **`Wait` 方法**：等待任务执行完毕。
   
   ```csharp
   t1.Wait();	//在这之后的逻辑全都得等t1执行完之后才能执行
   ```
2. **`WaitAny` 静态方法**：传入任务中任意一个任务结束就继续执行。
   ```csharp
   Task.WaitAny(t1, t2);
   ```
3. **`WaitAll` 静态方法**：任务列表中所有任务执行结束就继续执行。
   
   ```csharp
   Task.WaitAll(t1, t2);
   ```

### Task 完成后继续其它 Task（任务延续）
1. **`WhenAll` 静态方法 + `ContinueWith` 方法**
   ```csharp
   Task.WhenAll(t1, t2).ContinueWith((t) =>
   {
       Console.WriteLine("一个新的任务开始了");
   });
   ```
2. **`WhenAny` 静态方法 + `ContinueWith` 方法**
   ```csharp
   Task.WhenAny(t1, t2).ContinueWith((t) =>
   {
       Console.WriteLine("一个新的任务开始了");
   });
   ```

### 取消 Task 执行
1. **通过加入 `bool` 标识控制线程内死循环的结束**
2. **通过 `CancellationTokenSource` 取消标识源类来控制**
   ```csharp
   CancellationTokenSource c = new CancellationTokenSource();
   c.CancelAfter(5000);
   //c.Cancel() //或者手动取消
   c.Token.Register(() =>		//取消之后会自动执行这个函数
   {
       Console.WriteLine("任务取消了");
   });
   Task.Run(() =>
   {
       int i = 0;
       while (!c.IsCancellationRequested)
       {
           Console.WriteLine("计时：" + i);
           ++i;
           Thread.Sleep(1000);
       }
   });
   ```











# 异步方法async和await关键字

### 什么是同步和异步
- **同步方法**：调用者需要等待方法执行完毕后才能继续执行。
- **异步方法**：调用者立即返回，方法在另一个线程中执行，调用者无需等待方法执行完毕。

### 简单理解异步编程
- 将不需要立即得到结果且耗时的逻辑设置为异步执行，提高程序运行效率，避免线程阻塞。

### 什么时候需要异步编程
- 当需要处理的逻辑严重影响主线程执行的流畅性时，使用异步编程。
  - 复杂逻辑计算
  - 网络下载、网络通讯
  - 资源加载

### 异步方法 `async` 和 `await`
- `async` 和 `await` 通常与 `Task` 配合使用。
  - `async` 用于修饰函数，表示该函数是异步的。
  - `await` 用于等待某个逻辑结束，挂起异步方法，将控制权返回给调用者。

### 使用 `async` 修饰异步方法
1. 在异步方法中使用 `await` 关键字。
2. 异步方法名称建议以 `Async` 结尾。
3. 异步方法的返回值只能是 `void`、`Task`、`Task<>`。
4. 异步方法中不能声明使用 `ref` 或 `out` 关键字修饰的变量。

### 使用 `await` 等待异步内容执行完毕
- 遇到 `await` 关键字时，异步方法将被挂起，将控制权返回给调用者，当等待的内容执行结束后，继续执行异步函数内部逻辑。

### 举例说明
1. 复杂逻辑计算（利用 `Task` 新开线程进行计算）
2. 计时器
3. 资源加载（Addressables 的资源异步加载可以使用 `async` 和 `await`）

### 注意事项
- Unity 中大部分异步方法是不支持异步关键字 `async` 和 `await` 的，通常使用协同程序。
- 存在第三方工具（如 [Unity3dAsyncAwaitUtil](https://github.com/svermeulen/Unity3dAsyncAwaitUtil)）可以让 Unity 内部的一些异步加载的方法支持异步关键字。

### 总结
- 异步编程 `async` 和 `await` 是一个重要的功能，可以配合 `Task` 进行异步编程。
- 虽然 Unity 自带的一些异步加载原本不支持异步方法关键字，但可以利用第三方工具让它们支持。

### 示例代码
```csharp
public async void TestAsync()
{
    print("进入异步方法");
    await Task.Run(() => Thread.Sleep(5000));	//当这个线程执行完毕之后才会继续执行后面的逻辑
    print("异步方法后面的逻辑");
}

public async void CalcPathAsync(GameObject obj, Vector3 endPos)
{
    print("开始处理寻路逻辑");
    int value = 10;
    await Task.Run(() => {
        Thread.Sleep(1000);
        value = 50;
    });
    print("寻路计算完毕 处理逻辑" + value);	
    obj.transform.position = Vector3.zero;
}

public async void Timer()
{
    UnityWebRequest q = UnityWebRequest.Get("");
    CancellationTokenSource source = new CancellationTokenSource();
    int i = 0;
    while (!source.IsCancellationRequested)
    {
        print(i);
        await Task.Delay(1000);
        ++i;
    }
}

void Update()
{
    if (Input.GetKeyDown(KeyCode.Space))
        source.Cancel();
}
```





# 静态导入 异常筛选器 nameof



## C# 6 的新增功能

1. **`=>` 运算符**  
   - **用途**：用于简化方法和属性的定义，类似于匿名方法。  
   - **示例**：  
     ```csharp
     public int Add(int x, int y) => x + y;
     ```

2. **Null 传播器（`?.`）**  
   - **用途**：在访问对象的成员之前，自动检查对象是否为`null`，避免`NullReferenceException`。  
   - **示例**：  
     ```csharp
     string name = person?.Name;
     ```

3. **字符串内插（`$`）**  
   - **用途**：在字符串中嵌入变量，使代码更易读。  
   - **示例**：  
     ```csharp
     string name = "Alice";
     int age = 30;
     string message = $"Hello, {name}! You are {age} years old.";
     ```

4. **静态导入**  (有点像命名空间)
   
   - **用途**：通过`using static`语句直接访问静态类的成员，无需指定类名。  
   - **示例**：  
     ```csharp
     using static System.Math;
     double result = Sqrt(16); // 直接调用 Math.Sqrt
  ```
   
5. **异常筛选器（`when`）**  
   - **用途**：在`catch`块中添加条件，只有满足条件时才捕获异常。  
   - **示例**：  
     ```csharp
     try
     {
         // 可能引发异常的代码
     }
     catch (Exception e) when (e.Message.Contains("301"))
     {
         // 当异常消息包含 "301" 时执行
     }
     catch (Exception e) when (e.Message.Contains("404"))
     {
         // 当异常消息包含 "404" 时执行
     }
     ```

6. **`nameof` 运算符**  
   
   - **用途**：获取变量、类型或成员的名称字符串。  
   - **示例**：  
     ```csharp
     int i = 10;
     string name = nameof(i); // 输出 "i"
     ```

---

## 静态导入

- **用法**：在`using`语句中添加`static`关键字，直接访问静态类的成员。  
- **示例**：  
  ```csharp
  using static System.Math;
  using static System.Console;

  class Program
  {
      static void Main()
      {
          double result = Sqrt(16); // 直接调用 Math.Sqrt
          WriteLine(result);        // 直接调用 Console.WriteLine
      }
  }
  ```
- **优点**：代码更简洁，减少重复的类名引用。

---

## 异常筛选器

- **用法**：在`catch`语句后使用`when`关键字，添加条件表达式。  
- **示例**：  
  ```csharp
  try
  {
      // 可能引发异常的代码
  }
  catch (Exception e) when (e.Message.Contains("301"))
  {
      Console.WriteLine("Error 301: " + e.Message);
  }
  catch (Exception e) when (e.Message.Contains("404"))
  {
      Console.WriteLine("Error 404: " + e.Message);
  }
  catch (Exception e)
  {
      Console.WriteLine("Other error: " + e.Message);
  }
  ```
- **优点**：更精确地处理不同类型的异常，避免捕获过多不必要的异常。

---

## `nameof` 运算符

- **用法**：通过`nameof`获取变量、类型或成员的名称字符串。  
- **示例**：  
  ```csharp
  int i = 10;
  Console.WriteLine(nameof(i)); // 输出 "i"

  Console.WriteLine(nameof(List<int>)); // 输出 "List<int>"
  Console.WriteLine(nameof(List<int>.Add)); // 输出 "Add"

  List<int> list = new List<int> { 1, 2, 3, 4 };
  Console.WriteLine(nameof(list)); // 输出 "list"
  Console.WriteLine(nameof(list.Count)); // 输出 "Count"
  Console.WriteLine(nameof(list.Add)); // 输出 "Add"
  ```
- **优点**：避免硬编码字符串，减少因拼写错误导致的运行时问题, 就是当有地方报错的时候可以打印报错的变量的名字 方便查哪里错了。

。





---

# **C# 7 新增功能和语法**

## **C# 7 对应的 Unity 版本**

- **Unity 2018.3**：支持 C# 7  
- **Unity 2019.4**：支持 C# 7.3  
- **7.1、7.2、7.3**：基于 C# 7 的改进版本。

---

## **C# 7 的新增功能和语法**

1. **字面值改进**  
2. **`out` 参数相关和弃元知识点**  
3. **`ref` 返回值**  
4. **本地函数**  
5. **抛出表达式**  
6. **元组**  
	7. **模式匹配**

---

## **字面值改进**

- **基本概念**：在声明数值变量时，可以在数值之间插入`_`作为分隔符，方便阅读。  
- **作用**：提高数值变量的可读性。  
- **示例**：  
  ```csharp
  int i = 9_9123_1239; // 输出 991231239
  int i2 = 0xAB_CD_17; // 输出 181247
  ```

---

## **`out` 参数的快捷使用和弃元**

- **用法**：不再需要在调用带有`out`参数的函数之前声明变量。  
- **作用**：简化代码，提高开发效率。  
- **示例**：  
  ```csharp
  // 以前的写法
  // int a, b;
  // Calc(out a, out b);

  // 现在的写法
  Calc(out int x, out int y);
  print(x); // 输出 10
  print(y); // 输出 20

  // 使用 var 类型更简便（但存在重载时需明确调用）
  Calc(out int a, out var b);
  print(a); // 输出 10
  print(b); // 输出 20

  // 使用 _ 弃元符号省略不想使用的参数
  Calc(out int c, out _);
  print(c); // 输出 10
  ```

---

## **`ref` 修饰临时变量和返回值**

- **基本概念**：使用`ref`修饰临时变量和函数返回值，可以让赋值变为引用传递。  
- **作用**：用于修改数据对象中的某些值类型变量。  
- **示例**：  
  ```csharp
  // 修饰值类型临时变量
  int testI = 100;
  ref int testI2 = ref testI;
  testI2 = 900;
  print(testI); // 输出 900

  TestRef r = new TestRef(5, 5);
  ref TestRef r2 = ref r;
  r2.atk = 10;
  print(r.atk); // 输出 10

  // 获取对象中的参数
  ref int atk = ref r.atk;
  atk = 99;
  print(r.atk); // 输出 99

  // 函数返回值
  int[] numbers = new int[] { 1, 2, 3, 45, 5, 65, 4532, 12 };
  ref int number = ref FindNumber(numbers, 5);
  number = 98765;
  print(numbers[4]); // 输出 98765
  
   public ref int FindNumber(int[] numbers, int number)
  {
      for (int i = 0; i < numbers.Length; i++)
      {
          if (numbers[i] == number)
              return ref numbers[i];
      }
      return ref numbers[0];
  }
  ```

---

## **本地函数**

- **基本概念**：在函数内部声明一个临时函数。  
- **注意**：  
  - 本地函数只能在声明该函数的函数内部使用。  
  - 本地函数可以使用声明自己的函数中的变量。  
- **作用**：方便逻辑的封装。  
- **建议**：将本地函数写在主要逻辑的后面，方便代码的查看。  
- **示例**：  
  ```csharp
  public int TestTst(int i)
  {
      bool b = false;
      i += 10;
      Calc();
      print(b); // 输出 true
      return i;

      void Calc()
      {
          i += 10;
          b = true;
      }
  }
  ```





## 抛出表达式

- **基本概念**：在表达式中直接抛出异常，而不是通过单独的`throw`语句。  
- **作用**：简化代码，减少冗余的`if`或`else`语句。  
- **常见用法**：  
  1. **空合并操作符后用`throw`**：  
     ```csharp
     private void InitInfo(string str) => jsonStr = str ?? throw new ArgumentNullException(nameof(str));
     ```
     如果`str`为`null`，直接抛出`ArgumentNullException`。

  2. **三目运算符后面用`throw`**：  
     ```csharp
     private string GetInfo(string str, int index)
     {
         string[] strs = str.Split(',');
         return strs.Length > index ? strs[index] : throw new IndexOutOfRangeException();
     }
     ```
     如果`index`超出范围，直接抛出`IndexOutOfRangeException`。

  3. **`=>`符号后面直接`throw`**：  
     ```csharp
     Action action = () => throw new Exception("错了，不准用这个委托");
     action();
     ```
     在委托中直接抛出异常。

- **好处**：减少代码量，使逻辑更清晰。

---





## 元组

- **基本概念**：元组是一种快速构建数据结构的方式，可以将多个值组合在一起。  
- **主要作用**：方便处理多返回值，提升开发效率。  
- **常见用法**：  
  1. **无变量名元组**：  
     ```csharp
     (int, float, bool, string) yz = (1, 5.5f, true, "123");
     print(yz.Item1); // 输出 1
     print(yz.Item2); // 输出 5.5
     print(yz.Item3); // 输出 true
     print(yz.Item4); // 输出 "123"
     ```
     使用`Item1`、`Item2`等访问元组中的值。

  2. **有变量名元组**：  
     ```csharp
     (int i, float f, bool b, string str) yz2 = (1, 5.5f, true, "123");
     print(yz2.i);   // 输出 1
     print(yz2.f);   // 输出 5.5
     print(yz2.b);   // 输出 true
     print(yz2.str); // 输出 "123"
     ```
     使用自定义变量名访问元组中的值。

  3. **元组的比较**：  
     ```csharp
     if (yz == yz2)
         print("相等");
     else
         print("不相等");
     ```
     元组的比较需要类型和值都相等。

  4. **元组作为函数返回值**：  
     ```csharp
     private (string str, int i, float f) GetInfo()
     {
         return ("123", 2, 5.5f);
     }
     ```
     使用元组返回多个值。

  5. **元组的解构赋值**：  
     ```csharp
     (string myStr, int myInt, float myFloat) = GetInfo();
     print(myStr);   // 输出 "123"
     print(myInt);   // 输出 2
     print(myFloat); // 输出 5.5
     ```
     将元组中的值解构到多个变量中。

  6. **丢弃参数**：  
     ```csharp
     (string ss, _, _) = GetInfo();
     print(ss); // 输出 "123"
     ```
     使用`_`丢弃不需要的值。

  7. **元组作为字典的键**：  
     ```csharp
     Dictionary<(int i, float f), string> dic = new Dictionary<(int i, float f), string>();
     dic.Add((1, 2.5f), "123");
     if (dic.ContainsKey((1, 2.5f)))
     {
         print("存在相同的键");
         print(dic[(1, 2.5f)]); // 输出 "123"
     }
     ```
     使用元组作为字典的键。

---

## 模式匹配

- **基本概念**：模式匹配是一种语法元素，可以测试一个值是否满足某种条件，并从值中提取信息。  
- **主要作用**：简化代码，提高编程效率。  
- **常见用法**：  
  1. **常量模式**：  
     ```csharp
     object o = 1.5f;
     if (o is 1)
     {
         print("o是1");
     }
     if (o is null)
     {
         print("o是null");
     }
     ```
     判断变量是否等于某个常量值。

  2. **类型模式**：  
     ```csharp
     if (o is int i)
     {
         print(i); // 输出变量的值
     }
     ```
     判断变量是否为某种类型，并提取值。

  3. **`switch`语句中的模式匹配**：  
     ```csharp
     switch (o)
     {
         case int value:
             print("int:" + value);
             break;
         case float value:
             print("float:" + value);
             break;
         case null:
             print("null");
             break;
         default:
             break;
     }
     ```
     在`switch`语句中使用模式匹配。

  4. **`var`模式**：  
     ```csharp
     if (o is var v)
     {
         print(v); // 输出变量的值
     }
     ```
     将变量赋值给一个新变量。

---









---

# **C# 8 新增功能和语法**

## C# 8 对应的 Unity 版本

- **Unity 2020.3**：支持 C# 8  
- **注意**：部分 C# 8 的新特性在 Unity 2020.3 中可能不完全支持。  

---

## C# 8 的新增功能和语法

1. **`using` 声明**  
2. **静态本地函数**  
3. **空合并赋值（`??=`）**  
4. **解构函数（`Deconstruct`）**  
5. **模式匹配增强功能**  

---



## 静态本地函数

- **回顾 C# 7 本地函数**：  
  
  - 在函数内部声明的临时函数，只能在声明它的函数中使用。  
  - 可以访问上层函数中的变量。  
  - 示例：  
    ```csharp
    public int CalcInfo(int i)
    {
        bool b = false;
        i += 10;
        Calc(ref i, ref b);
      return i;
  
        void Calc(ref int i, ref bool b)
        {
            i += 10;
            b = true;
        }
    }
  ```
  
- **C# 8 静态本地函数**：  
  
  - 在本地函数前加上`static`关键字。  
  - 静态本地函数不能访问上层函数中的变量，只能处理逻辑。  
  - **作用**：避免通过直接改变上层变量来处理逻辑，防止逻辑混乱。  
  - 示例：  
    ```csharp
    public int CalcInfo(int i)
    {
        bool b = false;
        i += 10;
        Calc(ref i, ref b);
      return i;
  
        static void Calc(ref int i, ref bool b)	//不传参你就用不了
        {
            i += 10;
            b = true;
        }
    }
    ```

---

## `using` 声明

- **回顾 `using` 语句**：  
  - 用于确保对象在语句块结束后被释放，调用`Dispose`方法。  
  - 示例：  
    ```csharp
    using (StreamWriter stream = new StreamWriter("文件路径"))
    {
        stream.Write(true);
        stream.Write(1.2f);
        stream.Flush();
        stream.Close();
    } // 语句块结束时调用 Dispose 方法
    ```

- **C# 8 `using` 声明**：  
  
  - 对`using`语句的简化写法。  
  - 声明的对象在当前作用域结束时自动调用`Dispose`方法。  
  - 示例：  
    ```csharp
    using StreamWriter s2 = new StreamWriter("文件路径");
    s2.Write(5);
    s2.Flush();
    s2.Close();
    // 作用域结束时调用 Dispose 方法
  ```
  
- **注意**：  
  - 使用`using`声明的对象必须实现`IDisposable`接口。  
  - 示例：  
    ```csharp
    using TestUsing t = new TestUsing(); // TestUsing 实现了 IDisposable
    ```

---

## 空合并赋值（`??=`）

- **回顾空合并操作符（`??`）**：  
  - 左边值为`null`时返回右边值，否则返回左边值。  
  - 示例：  
    ```csharp
    string str = null;
    string str2 = str ?? "234"; // str2 = "234"
    ```

- **C# 8 空合并赋值（`??=`）**：  
  - 如果左边值为`null`，则将右边值赋给左边变量；否则不改变左边变量。  
  - 示例：  
    ```csharp
    string str = null;
    str ??= "4565"; // str = "4565"
    str ??= "1111"; // str 仍然是 "4565"，不会改变
    ```

---

## 解构函数（`Deconstruct`）

- **回顾元组解构**：  
  - 可以将元组的值解构到多个变量中。  
  - 示例：  
    ```csharp
    int i;
    float f;
    string s;
    (i, f, _, s) = GetInfo(); // 解构元组
    ```

- **C# 8 解构函数**：  
  - 在类中定义`Deconstruct`方法，允许将对象的成员变量解构到多个变量中。  
  - 示例：  
    ```csharp
    public class Person
    {
        public string name;
        public bool sex;
        public string number;
        public string email;

        public void Deconstruct(out string n, out bool sex) => (n, sex) = (this.name, this.sex);
        public void Deconstruct(out string n, out bool sex, out string number) => (n, sex, number) = (this.name, this.sex, this.number);
        public void Deconstruct(out string n, out bool sex, out string number, out string email)
        {
            n = name;
            sex = this.sex;
            number = this.number;
            email = this.email;
        }
    }

    Person p = new Person();
    p.name = "唐老狮";
    p.sex = false;
    p.email = "tpandme@163.com";
    p.number = "123123123123";

    (string name, bool sex) = p; // 解构部分成员
    print(name); // 输出 "唐老狮"
    print(sex);  // 输出 "False"

    (_, _, string number) = p; // 解构部分成员
    print(number); // 输出 "123123123123"
    ```

- **特点**：  
  - 一个类可以有多个`Deconstruct`方法，但参数数量必须不同。  
  - 解构函数允许将对象的成员变量解构到多个变量中，类似于元组的解构。







## 模式匹模式匹配增强功能

#### `switch`表达式
`switch`表达式是对有返回值的`switch`语句的缩写，使用`=>`表达式符号代替`case:`组合，用`_`弃元符号代替`default`。主要用于`switch`语句中只有一句代码返回值时使用。

```csharp
public Vector2 GetPos(PosType type) => type switch
{
    PosType.Top_Left => new Vector2(0, 0),
    PosType.Top_Right => new Vector2(1, 0),
    PosType.Bottom_Left => new Vector2(0, 1),
    PosType.Bottom_Right => new Vector2(1, 1),
    _ => new Vector2(0, 0)
};
```

### 属性模式

属性模式允许在常量模式的基础上判断对象的属性。使用`is {属性:值}`的语法。

```csharp
DiscountInfo info = new DiscountInfo("5折", true);
if (info is { discount: "6折", isDiscount: true })
{
    print("信息相同");
}
```

结合`switch`表达式使用：

```csharp
public float GetMoney(DiscountInfo info, float money) => info switch
{
    { discount: "5折", isDiscount: true } => money * .5f,
    { discount: "6折", isDiscount: true } => money * .6f,
    { discount: "7折", isDiscount: true } => money * .7f,
    _ => money
};
```

### 元组模式

元组模式允许直接利用元组进行条件判断，而无需声明数据结构类。

```csharp
int ii = 10;
bool bb = true;
if ((ii, bb) is (11, true))
{
    print("元组的值相同");
}
```

结合`switch`表达式使用：

```csharp
public float GetMoney(string discount, bool isDiscount, float money) => (discount, isDiscount) switch
{
    ("5折", true) => money * .5f,
    ("6折", true) => money * .6f,
    ("7折", true) => money * .7f,
    _ => money
};
```

### 位置模式

如果自定义类中实现了`Deconstruct`方法，可以直接用类对象与元组进行`is`判断。

```csharp
DiscountInfo info = new DiscountInfo("5折", true);
if (info is ("5折", true))
{
    print("位置模式 满足条件");
}

public class DiscountInfo
{
    public string discount;
    public bool isDiscount;

    public DiscountInfo(string discount, bool isDiscount)
    {
        this.discount = discount;
        this.isDiscount = isDiscount;
    }

    public void Deconstruct(out string dis, out bool isDis)
    {
        dis = this.discount;
        isDis = this.isDiscount;
    }
}
```

结合`switch`表达式使用：

```csharp
public float GetMoney2(DiscountInfo info, float money) => info switch
{
    ("5折", true) when money > 100 => money * .5f,
    ("6折", true) => money * .6f,
    ("7折", true) => money * .7f,
    _ => money
};
```

---









# 日期和时间

---

## 时间相关的内容

### 目前学习过的时间内容

目前我们只在 Unity 当中学习过 `Time` 类，可以通过它获取当前游戏相关的时间，例如帧间隔时间、游戏运行的时间和帧数等内容。然而，我们并没有学习过与真实世界时间相关的内容，例如如何获取当前时间的年、月、日、时、分、秒等。这节课我们将学习真实时间相关的内容。

---

## 时间在游戏开发中的作用

在游戏开发中，时间相关的功能非常常见，例如每日签到、活动倒计时、建造时间、激活时间等。要实现这些功能，仅靠 Unity 提供的 `Time` 类是远远不够的。因此，我们需要学习专门处理日期和时间的知识，以便实现这些功能需求。C# 提供了以下两个与时间相关的结构体：
1. **`DateTime`**：用于处理日期和时间的结构体。
2. **`TimeSpan`**：用于表示时间跨度的结构体。

---

## 时间相关名词说明

### 时间单位

- 1 秒（s）= 1000 毫秒（ms）  
- 1 毫秒（ms）= 1000 微秒（μs）  
- 1 微秒（μs）= 1000 纳秒（ns）

### 格里高利历

- 格里高利历通常指公元纪年法，目前我们所说的公历就是格里高利历。例如，2022 年是从公元元年开始算起的第二千零二十二年。

### 格林尼治时间（GMT）

- 格林尼治标准时间是位于英国伦敦郊区的皇家格林尼治天文台的标准时间。由于地球自转的不规则性和逐渐减速，格林尼治时间已经不再被作为标准时间使用。现在的标准时间是协调世界时（UTC）。

### 协调世界时（UTC）

- 协调世界时是基于国际原子时间，通过不规则地加入闰秒来抵消地球自转变慢的影响。它是世界上调节时钟和时间的主要时间标准。

### 时间戳

- 时间戳是从 1970 年 1 月 1 日（UNIX 时间戳的起点时间）到现在的时间，单位通常是秒。计算机时间和众多编程语言的时间都是从 1970 年 1 月 1 日开始算起，因为很多编程语言起源于 UNIX 系统，而 UNIX 系统认为 1970 年 1 月 1 日 0 点是时间纪元。

---

## `DateTime` 结构体

`DateTime` 是 C# 提供给我们处理日期和时间的结构体，位于 `System` 命名空间中。它的默认值和最小值是 0001 年 1 月 1 日 00:00:00（午夜），最大值是 9999 年 12 月 31 日晚上 11:59:59。

### 初始化 `DateTime`

```csharp
DateTime dt = new DateTime(2022, 12, 1, 13, 30, 45, 500); // 年、月、日、时、分、秒、毫秒
print(dt.Year + "-" + dt.Month + "-" + dt.Day + "-" + dt.Hour + "-" + dt.Minute + "-" + dt.Second + "-" + dt.Millisecond);
print(dt.Ticks); // 以格里高利历 00:00:00.000 年 1 月 1 日以来的 100 纳秒间隔数
print(dt.DayOfYear); // 一年的第几天
print(dt.DayOfWeek); // 星期几
```

### 获取当前时间

```csharp
DateTime nowTime = DateTime.Now; // 当前日期和时间
print(nowTime.Minute);

DateTime nowTime2 = DateTime.Today; // 当前日期（午夜）
print(nowTime2.Year + "-" + nowTime2.Month + "-" + nowTime2.Day);

DateTime nowTimeUTC = DateTime.UtcNow; // 当前 UTC 日期和时间
```

### 计算时间

```csharp
DateTime nowTime3 = nowTime.AddDays(-1); // 减去一天
print(nowTime3.Day);
```

### 字符串输出

```csharp
print(nowTime.ToString()); // 默认格式
print(nowTime.ToShortTimeString()); // 短时间格式
print(nowTime.ToShortDateString()); // 短日期格式
print(nowTime.ToLongTimeString()); // 长时间格式
print(nowTime.ToLongDateString()); // 长日期格式

print(nowTime.ToString("D")); // 长日期格式
print(nowTime.ToString("yyyy-MM-dd-ddd/HH-mm-ss")); // 自定义格式
```

### 字符串转 `DateTime`

```csharp
string str = "1988/5/4 18:00:08";
DateTime dt3;
if (DateTime.TryParse(str, out dt3))
{
    print(dt3);
}
else
{
    print("转换失败");
}
```

### 存储时间

存储时间的方式有很多：
1. 直接存储字符串。
2. 存储 `Ticks`。
3. 存储时间戳信息。存储时间戳的形式更加节约。

---

## `TimeSpan` 结构体

`TimeSpan` 是 C# 提供给我们的时间跨度结构体，位于 `System` 命名空间中。它通常用于表示两个 `DateTime` 对象之间的时间差。

### 初始化 `TimeSpan`

```csharp
TimeSpan ts = DateTime.Now - new DateTime(1970, 1, 1); // 从 1970 年 1 月 1 日到当前时间的时间跨度
print(ts.TotalMinutes); // 总分钟数
print(ts.TotalSeconds); // 总秒数
print(ts.TotalDays); // 总天数
print(ts.TotalHours); // 总小时数
print(ts.Ticks); // 100 纳秒间隔数

print(ts.Days + "-" + ts.Hours + "-" + ts.Minutes + "-" + ts.Seconds + "-" + ts.Milliseconds);
```

### 用 `TimeSpan` 计算时间

```csharp
TimeSpan ts2 = new TimeSpan(1, 0, 0, 0); // 1 天的时间跨度
DateTime timeNow = DateTime.Now + ts2; // 当前时间加上 1 天
```

### `TimeSpan` 的常量

```csharp
TimeSpan ts3 = new TimeSpan(0, 1, 1, 1); // 1 天 1 小时 1 分钟 1 秒
TimeSpan ts4 = ts2 + ts3; // 时间跨度相加
print(ts4.Days + "-" + ts4.Hours); // 输出结果

print(ts4.Ticks / TimeSpan.TicksPerSecond); // 使用常量进行计算
```





