---
title: "使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core (SDK Preview 3)"
description: "使用 .NET Core 命令列介面 (CLI) 在 Windows、Linux 或 macOS 上開始使用 .NET Core"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: be988f09-7349-43b0-97fb-3a703d4587ce
translationtype: Human Translation
ms.sourcegitcommit: ab71aab99505f211fe4adc86957eda4707761f1c
ms.openlocfilehash: 01b17021e79bcdb2dc69f97b709f4aa63dbab9aa

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line-sdk-preview-3"></a>使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core (SDK Preview 3)

此指南說明如何使用 .NET Core CLI 工具，來建置跨平台的主控台應用程式。  它會從最基本的主控台應用程式開始，最終會跨越多個專案，包括測試。 您將逐步新增這些功能，這些功能會建置在您已熟悉並建置的項目之上。

如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/dotnet.md)。

## <a name="prerequisites"></a>必要條件

開始之前，請確定您有[最新的 .NET Core CLI 工具 Preview 3 或更新版本](https://github.com/dotnet/core/blob/master/release-notes/preview3-download.md)。  您也需要文字編輯器。

## <a name="hello-console-app"></a>嗨，主控台應用程式！

首先，瀏覽至或用您喜歡的名稱建立新的資料夾。  "Hello" 是針對範例程式碼選擇的名稱，您可以在[這裡](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild)找到。

開啟命令提示字元並輸入下列命令：

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

讓我們快速逐步解說︰

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。  它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。
   
   `Hello.csproj`:
   ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
        <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
        
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>netcoreapp1.0</TargetFramework>
        </PropertyGroup>

        <ItemGroup>
            <Compile Include="**\*.cs" />
            <EmbeddedResource Include="**\*.resx" />
        </ItemGroup>

        <ItemGroup>
            <PackageReference Include="Microsoft.NETCore.App">
                <Version>1.0.1</Version>
            </PackageReference>
            <PackageReference Include="Microsoft.NET.Sdk">
                <Version>1.0.0-alpha-20161104-2</Version>
                <PrivateAssets>All</PrivateAssets>
            </PackageReference>
        </ItemGroup>
        
        <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
   ```

   專案檔會指定還原相依性和建置程式所需的所有內容。

   * `Import` 標記會帶入一些通用於所有 .NET Core 專案的屬性。
   * `OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。
   * `TargetFramework` 標記會指定我們設定為目標的 .NET 執行階段。 在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。 在本教學課程中，我們將著重於僅針對 .NET Core 1.0 來建置。
   * `Compile` 標記會指示編譯器，在目前目錄及其所有子目錄中建置所有副檔名為 `.cs` 的檔案，亦即專案中的所有 C# 檔案。 在進階案例中，可以排除檔案，但在本教學課程及大部分的簡單案例中，這一行可保留不變。
   * `EmbeddedResource` 標籤會指示建置系統，將副檔名為 `.resx` 的當地語系化檔案內嵌至已編譯的可執行檔中。 我們不會在本教學課程中使用該功能。
   * `PackageReference` 標記會指定在建置應用程式時必須還原和包含哪些相依性套件。 每個套件參考都會在 `Include` 屬性下方指定套件名稱及版本號碼。 在大部分的進階案例中，您將新增多個套件參考。 此外，也可以參考磁碟上的其他專案。

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

   程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。 `System` 命名空間會包含像是 `string` 的基本結構或數字類型。

   然後，我們會定義稱為 "ConsoleApplication" 的命名空間。 您可以將其變更為任何所需的位置。 名為 "Program" 的類別是定義於該命名空間內，其中含有可接受字串陣列做為其引數的 `Main` 方法。 這個陣列包含在將呼叫已編譯的程式時傳入的引數清單。 事實上，並未使用這個陣列︰所有程式所做的只是將 "Hello World!" 寫入 到主控台。 我們可以藉由將 `Console.WriteLine` 變更為下列程式碼，讓事情得更有趣。

   ```csharp
   if (args.Length > 0)
   {
       Console.WriteLine($"Hello {args[0]}!");
   }
   else
   {
       Console.WriteLine("Hello World!");
   }
   ```

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) 呼叫 [NuGet](http://nuget.org) (.NET 的套件管理員)，以還原相依性的樹狀結構。 NuGet 會分析 `Hello.csproj` 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 `obj/project.assets.json` 檔案。  必須要有 `project.assets.json` 檔案才能夠編譯並執行。
   
   `project.assets.json` 檔案是一組持續性且完整的 NuGet 相依性圖形，也包含了描述應用程式的其他資訊。  其他工具，例如 `dotnet build` 和 `dotnet run`，會讀取這個檔案，以便它們能用正確的 NuGet 相依性集合與繫結解析，處理原始程式碼。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) 呼叫 `dotnet build` 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。
   
    ```
    $ dotnet run
    Hello World!
    ```

    或者，您也可以執行 [`dotnet build`](../tools/dotnet-build.md) 來編譯程式碼，而不執行建置主控台應用程式。 這會產生 `bin/Debug/netcoreapp1.0/Hello.dll` 編譯的應用程式，您可以在 Windows 中使用 `dotnet bin\Debug\netcoreapp1.0\Hello.dll`，以及在其他系統上使用 `dotnet bin/Debug/netcoreapp1.0/Hello.dll` 來執行此應用程式。 您可以在命令列上指定額外的參數 (假設您位於 Windows 上)：

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll .NET
    Hello .NET!
    ```

    在進階案例中，可以建置應用程式做為一組獨立的平台專屬檔案，您可以將其部署到不需安裝 .NET Core 的電腦上並加以執行。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。

### <a name="augmenting-the-program"></a>擴充程式

讓我們稍微變更檔案。  Fibonacci 數字很有趣，因此讓我們來試試：

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
$ dotnet bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
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
using NumberFun;
```

最後，可以建置它︰

`$ dotnet build`

再來是有趣的部分︰讓新的檔案執行某些動作！

### <a name="example-a-fibonacci-sequence-generator"></a>範例︰Fibonacci 序列產生器

假設您想要藉由快取某些 Fibonacci 值並新增一些遞迴效果，從先前的 Fibonacci 範例開始建置。  為了取得[更好的 Fibonacci 範例](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetterMsBuild)，您的程式碼可能會搭配下列程式碼使用新的 `FibonacciGenerator.cs` 檔案。

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

現在，請如下所示調整 `Program.cs` 檔案中的 `Main()` 方法。

```csharp
using System;
using NumberFun;

class Program
{
    static void Main(string[] args)
    {
        var generator = new FibonacciGenerator();
        foreach (var digit in generator.Generate(15))
        {
            Console.WriteLine(digit);
        }
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

## <a name="conclusion"></a>結論
 
希望本指南已協助您了解如何建立 .NET Core 主控台應用程式，從基礎一直到具有單元測試的多專案系統。  下一個步驟是建立您自己的出色主控台應用程式！
 
如果您有興趣了解主控台應用程式的更進階範例，請參閱下一個教學課程︰[使用 .NET Core 命令列組織和測試專案 (SDK Preview 3)](using-with-xplat-cli-msbuild-folders.md)。



<!--HONumber=Nov16_HO3-->


