---
title: "使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core"
description: "使用 .NET Core 命令列介面 (CLI) 在 Windows、Linux 或 macOS 上開始使用 .NET Core"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: be988f09-7349-43b0-97fb-3a703d4587ce
translationtype: Human Translation
ms.sourcegitcommit: aeb199a9aeb1584570ad2a2942e2f22c75a59616
ms.openlocfilehash: aafa0c110dc3a2820f7e050d70b9450af1db35d8

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core

此指南說明如何使用 .NET Core CLI 工具，來建置跨平台的主控台應用程式。  它會從最基本的主控台應用程式開始，最終會跨越多個專案，包括測試。 您將逐步新增這些功能，這些功能會建置在您已熟悉並建置的項目之上。

如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../sdk.md)。

## <a name="prerequisites"></a>必要條件

在開始之前，請確定您有[最新的 .NET Core CLI 工具](https://www.microsoft.com/net/core)。  您也需要文字編輯器。

## <a name="hello-console-app"></a>嗨，主控台應用程式！

首先，瀏覽至或用您喜歡的名稱建立新的資料夾。  "Hello" 是針對範例程式碼選擇的名稱，您可以在[這裡](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Hello)找到。

開啟命令提示字元並輸入下列命令：

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

讓我們快速逐步解說︰

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的 NuGet 相依性建立最新的 `project.json` 檔案。  它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。
   
   `project.json`:
   ```json
   {
        "version": "1.0.0-*",
        "buildOptions": {
            "emitEntryPoint": true
        },
        "dependencies": {
            "Microsoft.NETCore.App": {
                "type": "platform",
                "version": "1.0.0"
            }
        },   
       "frameworks": {
            "netcoreapp1.0": {
                "imports": "dnxcore50"
            }
        }
   }
   ```
   `Program.cs`:
   ```csharp
   using System;

   namespace ConsoleApplication
   {
       public class Program
       {
           public static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) 呼叫 NuGet 以還原相依性樹狀結構。 NuGet 會分析 `project.json` 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 `project.lock.json` 檔案。  必須要有 `project.lock.json` 檔案才能夠編譯並執行。
   
   `project.lock.json` 檔案是一組持續性且完整的 NuGet 相依性圖形，也包含了描述應用程式的其他資訊。  其他工具，例如 `dotnet build` 和 `dotnet run`，會讀取這個檔案，以便它們能用正確的 NuGet 相依性集合與繫結解析，處理原始程式碼。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) 呼叫 `dotnet build` 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。
   
```
$ dotnet run
Hello, World!
```

您也可以執行 [`dotnet build`](../tools/dotnet-build.md) 來編譯程式碼，而不執行建置主控台應用程式。

### <a name="building-a-selfcontained-application"></a>建置獨立的應用程式

讓我們來試試編譯獨立的應用程式，而不是可攜式應用程式。 您可以深入閱讀 [.NET Core 中的可攜性類型](../deploying/index.md)，來了解不同的應用程式類型，及其部署方式。

您需要為您的 `project.json` 檔案進行一些變更，指引工具建立獨立的應用程式。 您可以在範例目錄中的 [HelloNative](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloNative) 專案看到這些。

第一項變更是從所有相依性移除 `"type": "platform"` 元素。 這個專案到目前為止的唯一相依性是 `"Microsoft.NETCore.App"`。 `dependencies` 區段應該像這樣：

```json
"dependencies": {
    "Microsoft.NETCore.App": {
        "version": "1.0.0"
    }
},
```

接下來，您必須新增 `runtimes` 節點以指定所有目標執行環境。 例如，下列 `runtimes` 節點會指示建置系統建立 64 位元版本 Windows 10 及 64 位元版本 Mac OS X 10.11 版的可執行檔。
建置系統會產生目前環境的原生可執行檔。 如果您在 Windows 電腦上依照下列步驟執行，則會建置 Windows 可執行檔。 如果您在 Mac 上依照下列步驟執行，則會建置 OS X 可執行檔。

```json 
"runtimes": {
  "win10-x64": {},
  "osx.10.11-x64": {}
}
```

請參閱 [RID 目錄](../rid-catalog.md)中的支援執行階段完整清單。 
 
進行這兩項變更之後，請執行 `dotnet restore`，後面接著 `dotnet build`，建立原生的可執行檔。 然後，您可以執行產生的原生可執行檔。 

下列範例顯示適用於 Windows 的命令。 此範例會顯示產生原生可執行檔的位置，並假設專案目錄名為 HelloNative。

```
$ dotnet restore 
$ dotnet build 
$ .\bin\Debug\netcoreapp1.0\win10-x64\HelloNative.exe
Hello World!
```

您可能會注意到，原生應用程式需要稍微較長的時間來建置，但執行速度稍微較快。 這種行為會隨著應用程式成長而更明顯。

在您的 `project.json` 建立原生組建時，建置程序會產生數個額外檔案。 這些檔案建立於 `bin\Debug\netcoreapp1.0\<platform>`，其中 `<platform>` 是選擇的 RID。 除了專案的 `HelloNative.dll` 之外，還有 `HelloNative.exe`，它會載入執行階段，並啟動應用程式。
請注意，產生的應用程式名稱已變更，因為專案目錄的名稱已變更。  

若要在不包含 .NET 執行階段的電腦上執行此應用程式，請封裝此應用程式。
您可以使用 `dotnet publish` 命令來完成。 `dotnet publish` 命令會在 `./bin/Debug/netcoreapp1.0/<platform>` 目錄下建立新的子目錄，名為 `publish`。 它會將可執行檔、所有相依的 DLL，以及架構都複製到這個子目錄。 您可以封裝該目錄到另一部電腦 (或容器)，然後在該處執行應用程式。 

讓我們比較第一個 Hello World 範例中的 `dotnet publish` 行為。 該應用程式是「可攜式應用程式」，這是 .NET Core 應用程式的預設類型。 可攜式應用程式需要在目標電腦上安裝 .NET Core。 可攜式應用程式可在一部電腦上建置，然後在任何位置執行。 原生應用程式則必須個別針對每一部目標電腦而建置。 `dotnet publish`建立一個目錄，其中具有應用程式的 DLL，以及不屬於平台安裝一部分的任何相依 dll。

### <a name="augmenting-the-program"></a>擴充程式

讓我們稍微變更檔案。  Fibonacci 數字很有趣，因此讓我們來試試 (使用原生的版本)︰

`Program.cs`:

```csharp
using static System.Console;

namespace ConsoleApplication
{
    public class Program
    {
        public static int FibonacciNumber(int n)
        {
            int a = 0;
            int b = 1;
            int tmp;
            
            for (int i = 0; i < n; i++)
            {
                tmp = a;
                a = b;
                b += tmp;
            }
            
            return a;   
        }
        
        public static void Main(string[] args)
        {
            WriteLine("Hello World!");
            WriteLine("Fibonacci Numbers 1-15:");
            
            for (int i = 0; i < 15; i++)
            {
                WriteLine($"{i+1}: {FibonacciNumber(i)}");
            }
        }
    }
}
```

並執行程式 (假設您是在 Windows 上，並且已將專案目錄名稱變更為 Fibonacci)︰

```
$ dotnet build
$ .\bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
1: 0
2: 1
3: 1
4: 2
5: 3
6: 5
7: 8
8: 13
9: 21
10: 34
11: 55
12: 89
13: 144
14: 233
15: 377
```

就是這麼容易！  您可以隨意擴充 `Program.cs`。

## <a name="adding-some-new-files"></a>新增一些新的檔案

單一檔案很適合用於簡單的一次性程式，但有可能您會想要分成多個檔案，如果您在建置具有多個元件的任何項目的話。  多個檔案是這麼做的一個方法。

建立新的檔案，並給它唯一的命名空間︰

```csharp
using System;

namespace NumberFun
{
    // code can go here
} 
```

接下來，將它包含在您的 `Program.cs` 檔案︰

```csharp
using static System.Console;
using NumberFun;
```

最後，可以建置它︰

`$ dotnet build`

再來是有趣的部分︰讓新的檔案執行某些動作！

### <a name="example-a-fibonacci-sequence-generator"></a>範例︰Fibonacci 序列產生器

假設您想要藉由快取某些 Fibonacci 值，再新增一些遞迴效果，從先前的 [Fibonacci 範例](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Fibonacci) 開始建置。  您的[更好的 Fibonacci 範例](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetter)的程式碼看起來可能像這樣︰

```csharp
using System;
using System.Collections.Generic;

namespace NumberFun
{
    public class FibonacciGenerator
    {
        private Dictionary<int, int> _cache = new Dictionary<int, int>();
        
        private int Fib(int n) => n < 2 ? n : FibValue(n - 1) + FibValue(n - 2);
        
        private int FibValue(int n)
        {
            if (!_cache.ContainsKey(n))
            {
                _cache.Add(n, Fib(n));
            }
            
            return _cache[n];
        }
        
        public IEnumerable<int> Generate(int n)
        {
            for (int i = 0; i < n; i++)
            {
                yield return FibValue(i);
            }
        }
    }
}
```

請注意，使用 `Dictionary<int, int>` 和 `IEnumerable<int>` 表示會併入 `System.Collections` 命名空間。
`Microsoft.NetCore.App` 套件是「中繼套件」，其中包含許多來自 .NET Framework 的核心組件。 藉由包含這個中繼套件，您便已經將 `System.Collections.dll` 組件包含為專案的一部分。 您可以執行 `dotnet publish` 並檢查屬於所安裝套件一部分的檔案，確認這點。 您會在清單中看到 `System.Collections.dll`。 

```json
{ 
  "version": "1.0.0-*", 
  "buildOptions": { 
    "debugType": "portable", 
    "emitEntryPoint": true 
  }, 
  "dependencies": {}, 
  "frameworks": { 
    "netcoreapp1.0": { 
      "dependencies": { 
        "Microsoft.NETCore.App": { 
          "version": "1.0.0" 
        } 
      }, 
      "imports": "dnxcore50" 
    } 
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.11-x64": {}
  }
}
```

現在，請如下所示調整 `Program.cs` 檔案中的 `Main()` 方法。 這個範例假設 `Program.cs` 有 `using System;` 陳述式。 如果您有 `using static System.Console;` 陳述式，請從 `Console.WriteLine` 移除 `Console.`。  

```csharp
public static void Main(string[] args)
{
    var generator = new FibonacciGenerator();
    foreach (var digit in generator.Generate(15))
    {
        WriteLine(digit);
    }
}
```

最後，執行應用程式！

```
$ dotnet run
0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

就是這麼容易！

## <a name="using-folders-to-organize-code"></a>使用資料夾來組織程式碼

假設您想要引進一些新的類型來使用。  您可以藉由新增更多檔案，並確定給予它們可包含在您 `Program.cs` 檔案中的命名空間，來達到此目的。

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__project.json
```

這很適合您的專案相當小的時候。  不過，如果您有較大的應用程式，並且使用許多不同的資料類型，且可能有多個層時，您可能會想以邏輯方式來組織項目。  這就是資料夾派上用場的時刻。  您可以遵照本指南介紹的 [NewTypes 範例專案](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes)，或建立自己的檔案和資料夾。

若要開始，請在專案的根目錄下建立新的資料夾。  `/Model`在這裡選擇。

```
/NewTypes
|__/Model
|__Program.cs
|__project.json
```

現在，請新增一些新的類型到資料夾中︰

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__project.json
```

現在，就彷彿它們是相同目錄中的檔案，請給予它們相同的命名空間，然後您就可以將其包含在您的 `Program.cs`。

### <a name="example-pet-types"></a>範例︰寵物類型

這個範例會建立兩個新的類型：`Dog` 和 `Cat`，並且實作介面 `IPet`。

資料夾結構：

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__project.json
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`project.json`:
```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "emitEntryPoint": true
  },
  "dependencies": {
    "Microsoft.NETCore.App": {
      "type": "platform",
      "version": "1.0.0"
    }
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": "dnxcore50"
    }
  }
}
```

而且，如果您執行它︰

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

可以新增新的寵物類型 (例如 `Bird`)，擴充此專案。

## <a name="testing-your-console-app"></a>測試主控台應用程式

您可能會想要在某個時間點測試您的專案。  以下是很好的作法︰

1. 將現有專案的任何來源移至新的 `src` 資料夾。

   ```
   /Project
   |__/src
   ```

2. 建立 `/test` 目錄。

   ```
   /Project
   |__/src
   |__/test
   ```

3. 建立新的 `global.json` 檔案：

   ```
   /Project
   |__/src
   |__/test
   |__global.json
   ```

   `global.json`:
   ```json
   {
      "projects": [
         "src", "test"
      ]
   }
   ```

   這個檔案會告訴建置系統，這是多專案的系統，如此可讓它到它處尋找相依性，而不只是在剛好執行所在的目前資料夾。  這很重要，因為它可讓您將對測試中之程式碼的相依性，放在您的測試專案中。
   
### <a name="example-extending-the-newtypes-project"></a>範例︰擴充 NewTypes 專案

現在，專案系統已就緒，您可以建立測試專案，並開始撰寫測試！  從現在開始，本指南會使用和擴充[範例 Types 專案](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes)。  此外，它會使用 [Xunit](https://xunit.github.io/) 測試架構。  請放心地依照指示進行，或建立自己的多專案系統與測試。


整個專案結構看起來應該像這樣︰

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__project.json
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__project.json
|__global.json
```

您的測試專案中需要確定有兩樣新的項目︰

1. 正確的 `project.json`，並具有下列各項︰

   * 參考`xunit`
   * 參考`dotnet-test-xunit`
   * 對應至測試中程式碼的命名空間參考

2. Xunit 測試類別。

`NewTypesTests/project.json`:
```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",

  "dependencies": {
    "Microsoft.NETCore.App": {
      "type":"platform",
      "version": "1.0.0"
    },
    "xunit":"2.2.0-beta2-build3300",
    "dotnet-test-xunit": "2.2.0-preview2-build1029",
    "NewTypes": "1.0.0"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "portable-net45+win8" 
      ]
    }
  }
}
```

`PetTests.cs`: 
```csharp
using System;
using Xunit;
using Pets;
public class PetTests
{
    [Fact]
    public void DogTalkToOwnerTest()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerTest()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
}
```
   
現在您可以執行測試了！  [`dotnet test`](../tools/dotnet-test.md) 命令會執行您的專案中所指定的測試執行器。 請確定您在最上層目錄啟動。
 
```
$ dotnet restore
$ cd test/NewTypesTests
$ dotnet test
```
 
輸出應該看起來像這樣︰
 
```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```
 
## <a name="conclusion"></a>結論
 
希望本指南已協助您了解如何建立 .NET Core 主控台應用程式，從基礎一直到具有單元測試的多專案系統。  下一個步驟是建立您自己的出色主控台應用程式！
 
如果您對更進階的主控台應用程式範例感興趣，請參閱下一個教學課程︰[使用 CLI 工具來撰寫主控台應用程式︰進階的逐步指南](cli-console-app-tutorial-advanced.md)。



<!--HONumber=Nov16_HO1-->


