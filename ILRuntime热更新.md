# ILRuntime 环境搭建与使用指南



## 1. ILRuntime 环境搭建

为了在 Unity 项目中使用 ILRuntime，需要进行以下配置和安装步骤：

- **添加 Scoped Registries：**

	- 方法一：手动修改项目文件夹下的 `Packages/manifest.json` 文件。在 `dependencies` 字段前添加以下内容:

		```json
		"scopedRegistries": [
		    {
		        "name": "ILRuntime",
		        "url": "https://registry.npmjs.org",
		        "scopes": [
		            "com.ourpalm"
		        ]
		    }
		],
		```

	- 方法二：在 Unity 的 `Project Settings` 中，选择 `Package Manager`，然后添加对应的 Registry 信息：

		- `Name`: ILRuntime
		- `Url`: `https://registry.npmjs.org`
		- `Scopes`: `com.ourpalm`

- **通过 Package Manager 安装 ILRuntime：**

	- 打开 Unity 工具栏中的 `Window` -> `Package Manager`。
	- 在左上角的 `Packages` 下拉菜单中选择 `My Registries` 选项。
	- 找到并选择 `ILRuntime` 进行安装。
	- 安装完成后，可以导入其示例工程。

- **启用 Unsafe Code：**

	- 由于 ILRuntime 会用到 C# 的 `unsafe` 关键字，因此需要启用该功能。
	- 在 Unity 工具栏的 `Edit` -> `Project Settings` 中。
	- 在 `Other Settings` 中勾选 `Allow 'unsafe' Code` 选项。

- 完成上述操作后，即可在 Unity 工具栏中看到 `ILRuntime` 选项。



## 2. ILRuntime 的开发方式



ILRuntime 的开发模式将项目分为两个部分：

- **Unity 工程 (主工程)：** 进行非热更新部分的开发，与常规 C# 开发方式相同。
- **热更工程 (HotFix_Project)：** 专门用于开发需要热更新的代码部分，同样使用 C# 语言编写。
	- 该工程位于 Unity 项目目录下的 `Samples\ILRuntime\2.1.0\Demo\HotFix_Project` 文件夹中，在 Unity 编辑器中不可见，需要在文件浏览器中查看。
- 在开发过程中，需要在两个工程之间切换进行开发。
- 两个工程之间可以相互访问和调用，实现了**跨域访问**。



## 3. ILRuntime 中的跨域访问



跨域访问是指**原始的 Unity 工程与热更工程之间能够相互调用对方声明的内容**。

- 例如：
	- Unity 工程可以使用热更工程中声明的类、委托或函数。
	- 热更工程也可以使用 Unity 工程中声明的类、委托或函数。



## 4. ILRuntime 的基本原理



ILRuntime 的核心原理是利用 **Mono.Cecil 库**。

- **Mono.Cecil 库：** 这是一个专门用于读取 C# 编译的 DLL 文件的开源第三方库。它提供了以下功能：
	- 获取 DLL 中的类型和方法元信息。
	- 读取方法体的 IL（Intermediate Language）汇编指令。
	- 读取 PDB 调试符号表文件。
	- 可以修改 DLL 中的元信息和方法体内容，并写回 DLL。
- **ILRuntime 的执行方式：** ILRuntime 在运行时通过读取和解释 DLL 文件中的内容来执行热更新代码。



## 5. 执行第一个 ILRuntime 热更程序示例



要运行您的第一个 ILRuntime 热更新程序：

1. 通过文件浏览器打开 `HotFix_Project` 工程（如果报错，请根据提示修改工程的目标框架）。 右键属性 在应用程序那块将目标框架改为.NET Framework 4.8
2. 成功生成 `HotFix_Project` 后，可以在 Unity 工程的 `StreamingAssets` 文件夹中看到生成的 `.dll` 文件和对应的 `.pdb` 调试符号文件。
3. 打开示例工程 `HelloWorld`，运行游戏。如果一切顺利，您将在 `Console` 窗口看到打印信息。



## 6. 总结使用 ILRuntime 的注意事项



为了正常使用 ILRuntime，需要注意以下关键点：

1. 正确修改 `manifest.json` 文件中的配置，或通过 `Package Manager` 添加 Registry。
2. 在 `Project Settings` 中勾选 `Allow 'unsafe' Code` 选项。
3. 通过 `HotFix_Project` 工程生成用于热更的 `.dll` 和 `.pdb` 文件。
4. ILRuntime 的基本原理是利用 Mono.Cecil 库来解释执行热更工程中 DLL 文件的代码。

------







# ILRuntime启动的基本流程



## ILRuntime 关键类：AppDomain

**`AppDomain`** 是 ILRuntime 框架中用于**解释和执行热更代码**的核心类，其作用类似于 xLua 中的 `LuaEnv`。

- **热更代码的产物：** ILRuntime 热更工程中的 C# 代码最终会被编译成 **`dll` 文件** 和 **`pdb` 文件**。这些文件包含了热更代码的所有信息。
- **`AppDomain` 的职责：** `AppDomain` 类就是 ILRuntime 提供的**解释器**，它能够加载并执行这些 `dll` 和 `pdb` 文件中的代码。

------



## Unity 中启动 ILRuntime 的步骤

在 Unity 中启动 ILRuntime 并执行热更代码需要以下几个步骤：

1. **声明 `AppDomain` 对象**：首先，创建一个 `ILRuntime.Runtime.Enviorment` 命名空间下的 `AppDomain` 实例。一个项目通常只需要一个 `AppDomain` 对象。
2. **加载热更文件**：通过本地或网络下载的方式，加载热更工程生成的 `dll` 和 `pdb` 文件。
3. **加载到 `AppDomain`**：将加载好的 `dll` 和 `pdb` 文件以**流（Stream）**的形式（如 `FileStream` 或 `MemoryStream`）传递给 `AppDomain` 对象的 `LoadAssembly` 方法。
4. **初始化信息**：根据需要初始化 ILRuntime 的相关信息，例如设置主线程 ID，以便在 Unity 的 Profiler 中进行性能分析。
5. **执行热更代码**：通过 `AppDomain` 对象调用热更工程中的逻辑。

------



## 总结

ILRuntime 热更新的核心就是**`dll` 和 `pdb` 文件**。这两个文件包含了所有的热更 C# 代码。因此，未来如果需要实现远程热更新，只需将这两个文件打包进 **AssetBundle**，然后通过网络下载即可。



### ILRuntime管理类

阅读顺序 StartILRuntime() -> LoadHotUpdateInfo(再看里面逻辑执行了哪些函数) -> StopILRuntime()

```c#
using ILRuntime.Mono.Cecil.Pdb;
using ILRuntime.Runtime.Enviorment;
using System.Collections;
using System.Collections.Generic;
using System.IO;
using System.Threading;
using UnityEngine;
using UnityEngine.Events;
using UnityEngine.Networking;

public class ILRuntimeMgr : MonoBehaviour
{
    private static ILRuntimeMgr instance;

    public AppDomain appDomain;
    //用于存储加载出来的 两个文件的内存流对象
    private MemoryStream dllStream;
    private MemoryStream pdbStream;

    private bool isStart = false;

    public static ILRuntimeMgr Instance
    {
        get
        {
            if(instance == null)
            {
                GameObject obj = new GameObject("ILRuntimeMgr");
                instance = obj.AddComponent<ILRuntimeMgr>();
                DontDestroyOnLoad(obj);
            }

            return instance;
        }
    }

    /// <summary>
    /// 用于启动ILRuntime初始化方法
    /// </summary>
    public void StartILRuntime( UnityAction callBack = null )
    {
        if(!isStart)
        {
            isStart = true;
            appDomain = new AppDomain();
            StartCoroutine(LoadHotUpdateInfo(callBack));
        }
    }

    public void StopILRuntime()
    {
        //1.释放流
        if (dllStream != null)
            dllStream.Close();
        if (pdbStream != null)
            pdbStream.Close();
        dllStream = null;
        pdbStream = null;
        //2.清空appDomain
        appDomain = null;

        isStart = false;
    }

    /// <summary>
    /// 初始化ILRuntime相关的内容
    /// </summary>
    private void InitILRuntime()
    {
        //其他初始化

        //初始化ILRuntime相关信息（目前只需要告诉ILRuntime主线程的线程ID，主要目的是能够在Unity的Profiler剖析器窗口中分析问题）
        appDomain.UnityMainThreadID = Thread.CurrentThread.ManagedThreadId;
    }

    /// <summary>
    /// 启动完毕并且初始化完毕后 想要执行的热更新的逻辑
    /// </summary>
    private void ILRuntimeLoadOverDoSomething()
    {

    }

    /// <summary>
    /// 去异步加载我们的热更相关的dll和pdb文件
    /// </summary>
    /// <returns></returns>
    IEnumerator LoadHotUpdateInfo(UnityAction callBack)
    {
        //这部分知识点在 Unity网络开发基础当中有讲解
        //加载本地的DLL文件
#if UNITY_ANDROID
        UnityWebRequest reqDll = UnityWebRequest.Get(Application.streamingAssetsPath + "/HotFix_Project.dll");
#else
        UnityWebRequest reqDll = UnityWebRequest.Get("file:///" + Application.streamingAssetsPath + "/HotFix_Project.dll");
#endif
        yield return reqDll.SendWebRequest();
        //如果失败了
        if (reqDll.result != UnityWebRequest.Result.Success)
            print("加载DLL文件失败" + reqDll.responseCode + reqDll.result);
        //读取加载的DLL数据
        byte[] dll = reqDll.downloadHandler.data;
        reqDll.Dispose();

#if UNITY_ANDROID
        UnityWebRequest reqPdb = UnityWebRequest.Get(Application.streamingAssetsPath + "/HotFix_Project.pdb");
#else
        UnityWebRequest reqPdb = UnityWebRequest.Get("file:///" + Application.streamingAssetsPath + "/HotFix_Project.pdb");
#endif
        yield return reqPdb.SendWebRequest();
        //如果失败了
        if (reqPdb.result != UnityWebRequest.Result.Success)
            print("加载Pdb文件失败" + reqPdb.responseCode + reqPdb.result);
        //读取加载的DLL数据
        byte[] pdb = reqPdb.downloadHandler.data;
        reqPdb.Dispose();

        //3.将加载的数据以流的形式(文件流或者内存流对象)传递给AppDomain对象中的LoadAssembly方法
        //注意 这里使用流 不要用完就关 一定要等到热更相关内容不使用了 再关闭
        dllStream = new MemoryStream(dll);
        pdbStream = new MemoryStream(pdb);
        //将我们两个文件的内存流用于初始化 appDomain 我们之后就可以通过该对象来执行我们对应的热更代码了
        appDomain.LoadAssembly(dllStream, pdbStream, new PdbReaderProvider());

        InitILRuntime();

        ILRuntimeLoadOverDoSomething();

        //当ILRuntime启动完毕 想要在外部执行的内容
        callBack?.Invoke();
    }
}

```



# Unity调用ILRuntime



## Unity跨域实例化ILRuntime中成员属性



### 知识点一：在 ILRuntime 热更工程中新建类

要在 ILRuntime 热更工程中创建一个类，你只需要像平时一样新建一个类文件即可。为了支持多种实例化方式，建议为该类声明多个**构造函数重载**。

------



### 知识点二：在 Unity 中跨域调用 ILRuntime 中的类

为了在 Unity 主工程中实例化并使用热更工程中的类，需要先让 ILRuntime 重新生成最新的 **`dll`** 和 **`pdb`** 文件。加载这些文件后，可以通过以下几种方式在主工程中实例化热更类。

这三种方式都需要在加载完 `dll` 和 `pdb` 后，通过 `ILRuntime.Runtime.Enviorment.AppDomain` 对象来完成：



#### 类声明

记得重新生成

```c#
namespace HotFix_Project
{
    class Lesson3_Test
    {
        public string str;
        public Lesson3_Test()
        {

        }

        public Lesson3_Test(string str)
        {
            this.str = str;
        }
    }
}
```





#### 方式一：使用 `appdomain.Instantiate` 方法

这是最直接、最简单的方式。你只需要提供类的完整命名空间和类名，以及可选的构造函数参数。

```c#
ILRuntimeMgr.Instance.StartILRuntime(() =>
{

// 无参构造
object obj = appDomain.Instantiate("HotFix_Project.Lesson3_Test");
print(obj);

// 带参构造
obj = appDomain.Instantiate("HotFix_Project.Lesson3_Test", new object[] { "123" });
print(obj);
}
```



#### 方式二：通过 `LoadedTypes` 字典获取 `IType` 后实例化

这种方式类似于 C# 的反射机制。你首先通过 `appDomain.LoadedTypes` 字典获取类的 `IType` 对象，然后将其转换为 `ILType` 并调用其 `Instantiate` 方法。

```c#
IType type = appDomain.LoadedTypes["HotFix_Project.Lesson3_Test"];

// 无参构造
object obj = ((ILType)type).Instantiate();
print(obj);

// 带参构造
obj = ((ILType)type).Instantiate(new object[] { "234" });
print(obj);
```

**推荐使用此方式**，因为它获取的 `IType` 对象可以在后续调用该对象的方法和变量时提供便利。



#### 方式三：通过 `IType` 和 `ConstructorInfo` 实例化

这种方式也类似于反射，但更为底层。你先获取类的 `IType` 对象，然后通过 `ReflectionType.GetConstructor` 获取其构造函数信息，最后使用 `Invoke` 来实例化对象。

```c#
IType type = appDomain.LoadedTypes["HotFix_Project.Lesson3_Test"];

// 无参构造
ConstructorInfo info = type.ReflectionType.GetConstructor(new Type[0]);
object obj = info.Invoke(null);
print(obj);

// 带参构造
info = type.ReflectionType.GetConstructor(new Type[] { typeof(string)});
obj = info.Invoke(new object[] { "11111"});
print(obj);
```

------



## 总结

在 Unity 中实例化 ILRuntime 热更工程中的类主要有三种方式。其中，**方式二和方式三更被推荐**，因为它们都首先获取了类的 **`IType`** 类型信息。这个 `IType` 对象非常有用，在后续调用热更对象的成员（方法、字段等）时，可以提供更方便的访问方式。







## Unity跨域调用ILRuntime中成员属性

