---
title: "使用跨平台工具開發程式庫"
description: "使用跨平台工具開發程式庫"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 94b6d965c7a39a02723b641f6551e54dd4df1f07
ms.lasthandoff: 03/07/2017

---

# <a name="developing-libraries-with-cross-platform-tools"></a>使用跨平台工具開發程式庫

> [!WARNING]
> 本主題尚未針對最新版工具進行更新。

本文涵蓋如何使用跨平台 CLI 工具撰寫 .NET 的程式庫。  CLI 提供可在所有支援的作業系統上運作的有效率且低階體驗。  您仍然可以使用 Visual Studio 來建置程式庫，而且，如果那是您偏好的體驗，[請參閱 Visual Studio 指南](libraries-with-vs.md)。

## <a name="prerequisites"></a>必要條件

您需要在電腦上安裝 [.NET Core SDK 和 CLI](https://www.microsoft.com/net/core)。

如需這份文件中處理 .NET Framework 版本或可攜式類別庫 (PCL) 的小節，您需要在 Windows 電腦上安裝 [.NET Framework](http://getdotnet.azurewebsites.net/)。  

此外，如果您想要支援較舊的 .NET Framework 目標，則需要從 [.NET target platforms](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html) 頁面安裝較舊 Framework 版本的目標/開發人員套件。  請參閱這張表格︰

| .NET Framework 版本 | 要下載的項目 |
| ---------------------- | ----------------- |
| 4.6.1 | .NET Framework 4.6.1 目標套件 |
| 4.6 | .NET Framework 4.6 目標套件 |
| 4.5.2 | .NET Framework 4.5.2 開發人員套件 |
| 4.5.1 | .NET Framework 4.5.1 開發人員套件 |
| 4.5 | 適用於 Windows 8 的 Windows 軟體開發套件 |
| 4.0 | 適用於 Windows 7 的 Windows SDK 及 .NET Framework 4 |
| 2.0、3.0 和 3.5 | .NET Framework 3.5 SP1 執行階段 (或 Windows 8+ 版本) |

## <a name="how-to-target-the-net-standard"></a>如何將目標設為 .NET Standard

如果您不是很熟悉 .NET Standard，請參閱 [.NET Standard 程式庫](../../standard/library.md)來深入了解。

在該文中，有一張將 .NET Standard 版本對應至各種實作的表格︰

| 平台名稱 | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 |
|.NET 核心|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Mono/Xamarin 平台||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|通用 Windows 平台|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

以下是這個資料表在建立程式庫時的意義︰

您選擇的 .NET Standard 平台版本將會在最新 API 的存取與將目標設為多個 .NET 平台和 Framework 版本的能力之間進行取捨。  您可以控制可設為目標之平台和版本的範圍，方法是選擇 `netstandardX.X` 版本 (其中 `X.X` 是版本號碼)，並將它新增至 `project.json` 檔案。

此外，[要相依的對應 NuGet 套件](https://www.nuget.org/packages/NETStandard.Library/)是 `NETStandard.Library` `1.6.0` 版。  雖然沒有任何事項可以防止您相依於 `Microsoft.NETCore.App` (例如使用主控台應用程式)，但是一般不建議這麼做。  如果您需要 `NETStandard.Library` 中來自未指定套件的 API，則除了 `project.json` 檔案的 `dependencies` 區段中的 `NETStandard.Library` 之外，一律可以指定該套件。

將目標設為 .NET Standard 時，會有三個主要選項 (視需求而定)。

1. 您可以使用最新版本的 .NET Standard (`netstandard1.6`)，這適用於想要存取大部分 API 時，而且較少跨實作時則不用在意。
2. 您可以使用較低版本的 .NET Standard，以將目標設為較舊的 .NET 實作。 這裡的成本不包含存取一些最新的 API。
    
    例如，如果您想要確保與 .NET Framework 4.6 和更新版本相容，請挑選 `netstandard1.3`：

    ```json
    {
        "dependencies":{
            "NETStandard.Library":"1.6.0"
        },
        "frameworks":{
            "netstandard1.3":{}
        }
    }
    ```
    
    .NET Standard 版本具備回溯相容。 這表示 `netstandard1.0` 程式庫是在 `netstandard1.1` 平台和更高版本上執行。  不過，沒有往後相容性 - 較低的 .NET Standard 平台無法參考較高的平台。  這表示 `netstandard1.0` 程式庫無法參考目標設為 `netstandard1.1` 或更高版本的程式庫。  針對您的需求，選取正確混合使用 API 與平台支援的標準版本。
    
3. 如果您想要將目標設為 .NET Framework 4.0 或以下版本，或者想要使用位在 .NET Framework 中但不在 .NET Standard 中的 API (例如，`System.Drawing`)，請閱讀下列各節，並了解如何使用多目標。

## <a name="how-to-target-the-net-framework"></a>如何將目標設為 .NET Framework

> [!NOTE]
> 這些指示假設您已在電腦上安裝 .NET Framework。  請參閱安裝相依性的[必要條件](#prerequisites)。

請記住，將不再支援這裡使用的一些 .NET Framework 版本。  如需不支援的版本，請參閱 [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) (.NET Framework 支援週期原則 FAQ)。

如果您想要達到開發人員和專案數目上限，請使用 .NET Framework 4 作為基準目標。 若要將目標設為 .NET Framework，您需要從使用對應至所要支援之 .NET Framework 版本的正確目標 Framework Moniker (TFM) 開始。

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.6.3 --> net463
```

例如，以下是如何撰寫目標設為 .NET Framework 4 的程式庫：

```json
{
    "frameworks":{
        "net40":{}
    }
}
```

就是這麼容易！  雖然這只是針對 .NET Framework 4 所編譯，但是您可以在較新版的 .NET Framework 上使用程式庫。

## <a name="how-to-target-a-portable-class-library-pcl"></a>如何將目標設為可攜式類別庫 (PCL)

> [!NOTE]
> 這些指示假設您已在電腦上安裝 .NET Framework。  請參閱安裝相依性的[必要條件](#prerequisites)。

將目標設為 PCL 設定檔，比將目標設為 .NET Standard 或 .NET Framework 更難處理。  如果是新手，請[參考這份 PCL 設定檔清單](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview)，以找到對應至設為目標之 PCL 設定檔的 NuGet 目標。

接著，您可能需要執行下列動作：

1. 在 `project.json` 的 `frameworks` 下方建立名為 `.NETPortable,Version=v{version},Profile=Profile{profile}` 的新項目，其中 `{version}` 和 `{profile}` 分別對應至 PCL 版本號碼和設定檔號碼。
2. 在這個新的項目中，列出 `frameworkAssemblies` 項目下方每個用於該目標的單一組件。  這包含 `mscorlib`、`System` 和 `System.Core`。
3. 如果您是使用多目標 (請參閱下一節)，則必須在其目標項目下方明確列出每個目標的相依性。  您將無法再使用全域 `dependencies` 項目。

下列是範例目標 PCL Profile 328。 Profile 328 支援：.NET Standard 1.4、.NET Framework 4、Windows 8、Windows Phone 8.1、Windows Phone Silverlight 8.1 和 Silverlight 5。

```json
{
    "frameworks":{
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":""
            }
        }
    }
}
```

如果您所建置的專案在 *project.json* 檔案中包含 PCL Profile 328 作為架構，則在 */bin/debug* 資料夾中會有這個子資料夾︰

```
portable-net40+sl50+netcore45+wpa81+wp8/
```

這個資料夾包含執行您程式庫所需的 `.dll` 檔案。

## <a name="how-to-multitarget"></a>如何使用多目標

> [!NOTE]
> 下列指示假設您已在電腦上安裝 .NET Framework。  請參閱[必要條件](#prerequisites)小節，了解您需要安裝的相依性以及其下載位置。

當您的專案同時支援 .NET Framework 和 .NET Core 時，可能需要將目標設為舊版 .NET Framework。 在這個案例中，如果您想要為較新的目標使用較新的 API 和語言建構，請在程式碼中使用 `#if` 指示詞。 您也可能需要針對設為目標的每個平台，在 `project.json file` 中新增不同的套件和相依性，以包含每個案例所需的不同 API。

例如，假設您的程式庫透過 HTTP 執行網路作業。 針對 .NET Standard 和 .NET Framework 4.5 版或更高版本，您可以使用 `System.Net.Http` 命名空間中的 `HttpClient` 類別。 不過，舊版 .NET Framework 沒有 `HttpClient` 類別，因此您可以改用這些項目之 `System.Net` 命名空間中的 `WebClient` 類別。

因此，`project.json` 檔案如下所示：

```json
{
    "frameworks":{
        "net40":{
            "frameworkAssemblies": {
                "System.Net":"",
                "System.Text.RegularExpressions":""
            }
        },
        "net452":{
            "frameworkAssemblies":{
                "System.Net":"",
                "System.Net.Http":"",
                "System.Text.RegularExpressions":"",
                "System.Threading.Tasks":""
            }
        },
        "netstandard1.6":{
            "dependencies": {
                "NETStandard.Library":"1.6.0",
            }
        }
    }
}
```

請注意，需要在 `net40` 和 `net452` 目標中明確參考 .NET Framework 組件，並且也在 `netstandard1.6` 目標中明確列出 NuGet 參考。  這在多目標案例中是必要的。

接下來，可以如下調整原始程式檔中的 `using` 陳述式：

```csharp
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
// This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

建置系統會得知 `#if` 指示詞中所使用的下列前置處理器符號︰

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

而且在來源的中間，您可以使用 `#if` 指示詞有條件地使用這些程式庫。 例如: 

```csharp
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "http://www.dotnetfoundation.org/";
          
            var uri = new Uri(url);
            
            string result = "";
            
            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }
            
            int dotNetCount = Regex.Matches(result, ".NET").Count;
            
            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "http://www.dotnetfoundation.org/";
            
            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);
            
            int dotNetCount = Regex.Matches(result, ".NET").Count;
            
            return $"dotnetfoundation.orgmentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
```

如果您所建置的專案在 *project.json* 檔案中包含 `net40`、`net45` 和 `netstandard1.6` 作為架構，則在 */bin/debug* 資料夾中會有這些子資料夾︰

```
net40/
net45/
netstandard1.6/
```

### <a name="but-what-about-multitargeting-with-portable-class-libraries"></a>但是具有可攜式類別庫的多目標怎麼辦？

如果您想要與 PCL 目標交叉編譯，則必須在 PCL 目標中於 `buildOptions` 的 `project.json` 檔案中新增組建定義。  您接著可以在來源中使用將組建定義當成前置處理器符號使用的 `#if` 指示詞。

例如，如果您想要將目標設為 [PCL profile 328](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview) (.NET Framework 4、Windows 8、Windows Phone Silverlight 8、Windows Phone 8.1、Silverlight 5)，則可以在跨編譯時以 "PORTABLE328" 形式參照它。  只要將它當成 `buildOptions` 屬性新增至 `project.json` 檔案︰

```json
{
    "frameworks":{
        "netstandard1.6":{
           "dependencies":{
                "NETStandard.Library":"1.6.0",
            }
        },
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "buildOptions": {
                "define": [ "PORTABLE328" ]
            },
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":"",
                "System.Net"
            }
        }
    }
}

```

現在您可以針對該目標有條件地進行編譯︰

```csharp
#if !PORTABLE328
using System.Net.Http;
using System.Threading.Tasks;
// Potentially other namespaces which aren't compatible with Profile 328
#endif
```

因為編譯器現在可以辨識 `PORTABLE328`，所以編譯器所產生的 PCL Profile 328 程式庫將不會包含 `System.Net.Http` 或 `System.Threading.Tasks`。

如果您所建置的專案在 *project.json* 檔案中包含 PCL Profile 328 和 `netstandard1.6` 作為架構，則在 */bin/debug* 資料夾中會有這些子資料夾︰

```
portable-net40+sl50+netcore45+wpa81+wp8/
netstandard1.6/
```

## <a name="how-to-use-native-dependencies"></a>如何使用原生相依性

您可能想要撰寫與原生 `.dll` 檔案相依的程式庫。  如果您正在撰寫這類程式庫，則會有兩個選項︰

1. 在 `project.json` 中直接參考原生 `.dll`。
2. 將該 `.dll` 封裝到其專屬 NuGet 套件，並與該套件相依。

針對第一個選項，您必須在 `project.json` 檔案中包含下列項目︰

1. 在 `buildOptions` 區段中，將 `allowUnsafe` 設定為 `true`。
2. 在 `runtimes` 區段中指定[執行階段識別項 (RID)](../rid-catalog.md)。
3. 指定所參考之原生 `.dll` 檔案的路徑。

以下是在 Windows 上執行之專案根目錄中原生 `.dll` 檔案的範例 `project.json`：

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "runtimes":{
        "win10-x64":{}
    },
    "packOptions":{
        "files":{
            "mappings":{
                "runtimes/win10-x64/native":{
                    "includeFiles":[ "native-lib.dll"]
                }
            }            
        }
    }
}
```

如果您將程式庫散發為套件，則建議您將 `.dll` 檔案放在專案的根層級。

針對第二個選項，您需要透過 `.dll` 檔案建置 NuGet 套件、將它裝載於 NuGet 或 MyGet 摘要，並且直接與它相依。  您仍然需要在 `project.json` 的 `buildOptions` 區段中，將 `allowUnsafe` 設定為 `true`。  以下是範例 (假設 `MyNativeLib` 是 `1.2.0` 版的 Nuget 套件)：

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "dependencies":{
        "MyNativeLib":"1.2.0"
    }
}
```

若要查看如何封裝跨平台原生二進位檔的範例，請參閱 [ASP.NET Libuv Package](https://github.com/aspnet/libuv-package) 和 [corresponding reference in KestrelHttpServer](https://github.com/aspnet/KestrelHttpServer/blob/1.0.0/src/Microsoft.AspNetCore.Server.Kestrel/project.json#L19)。

## <a name="how-to-test-libraries-on-net-core"></a>如何測試 .NET Core 上的程式庫

重要的是一定要可以跨平台進行測試。  [xUnit](http://xunit.github.io/) 的使用十分簡單，而且它也是 .NET Core 專案所使用的測試工具。  如何設定具有測試專案的方案，將取決於[方案結構](#structuring-a-solution)。  下列範例假設所有來源專案都是位於最上層 `/src` 資料夾下方，而所有測試專案都是位於最上層 `/test` 資料夾下方。

1. 請確定您有方案層級的 `global.json` 檔案，可以了解測試專案所在的位置：
    
    ```json
    {
        "projects":[ "src", "test"]
    }
    ```
    
    然後，您的方案資料夾結構應該如下︰
    
    ```
    /SolutionWithSrcAndTest
    |__global.json
    |__/src
    |__/test
    ```
    
2. 建立新的測試專案，方法是在 `/test` 資料夾下方建立專案資料夾，並在新的專案資料夾中建立 `project.json` 檔案。  若要建立 `project.json` 檔案，您可以執行 `dotnet new` 命令，之後即可修改 `project.json` 檔案。  檔案應該具有下列項目：

   * `netcoreapp1.0`列為 `frameworks` 下方的唯一項目。
   * `Microsoft.NETCore.App` `1.0.0` 版的參考。
   * xUnit `2.2.0-beta2-build3300` 版的參考。
   * `dotnet-test-xunit``2.2.0-preview2-build1029` 版的參考
   * 正在測試之程式庫的專案參考。
   * 項目 `"testRunner":"xunit"`。
   
   以下是範例 (`LibraryUnderTest` `1.0.0` 版是正在測試的程式庫)：
   
   ```json
   {
        "testRunner":"xunit",
        "dependencies":{
            "LibraryUnderTest":{
                "version":"1.0.0",
                "target":"project"
            },
            "Microsoft.NETCore.App":{
                "version":"1.0.0",
                "type":"platform"
            },
            "xunit":"2.2.0-beta2-build3300",
            "dotnet-test-xunit":"2.2.0-preview2-build1029",
        },
        "frameworks":{
            "netcoreapp1.0":{}
        }
   }
   ```
3. 執行 `dotnet restore` 來還原套件。  如果您尚未還原過套件，則應該在方案層級執行這項作業。

4. 瀏覽至測試專案，並使用 `dotnet test` 執行測試：

    ```
    $ cd path-to-your-test-project
    $ dotnet test
    ```

就是這麼容易！  您現在可以使用命令列工具跨所有平台來測試程式庫。  若要在設定好所有項目之後立即繼續測試，測試程式庫就會非常簡單︰

1. 對程式庫進行變更。
2. 在測試目錄中，從命令列中使用 `dotnet test` 命令來執行測試。

當您叫用 `dotnet test` 命令時，將會自動重建程式碼。

只要新增相依性，就請記得從命令列執行 `dotnet restore`，這樣您就可以繼續往下進行！

## <a name="how-to-use-multiple-projects"></a>如何使用多個專案

較大程式庫的常見需求是將功能放在不同的專案中。

假設您想要建置可在慣用 C# 和 F# 中使用的程式庫。  這表示您程式庫的消費者透過 C# 或 F# 的原本方式來使用程式庫。  例如，在 C# 中，您可能會如下使用程式庫︰

```csharp
var convertResult = await AwesomeLibrary.ConvertAsync(data);
var result = AwesomeLibrary.Process(convertResult);
```  

在 F# 中，它可能如下所示：

```fsharp
let result =
    data
    |> AwesomeLibrary.convertAsync 
    |> Async.RunSynchronously 
    |> AwesomeLibrary.process
```

這類使用案例表示針對 C# 和 F#，正在存取的 API 必須具有不同的結構。  完成這項作業的常見方法將程式庫的所有邏輯都納入核心專案，而且 C# 和 F# 專案定義呼叫該核心專案的 API 層。  區段的其餘部分將使用下列名稱︰

* **AwesomeLibrary.Core** - 核心專案，內含程式庫的所有邏輯
* **AwesomeLibrary.CSharp** - 專案，具有公用 API 可供在 C 中使用#
* **AwesomeLibrary.FSharp** - 專案，具有公用 API 可供在 F 中使用#

### <a name="project-to-project-referencing"></a>專案對專案參考

參考專案的最佳方式是執行下列動作︰

1. 請確定您想要參考的專案有磁碟上其內含資料夾的不錯名稱。  這將是用來參考您專案的名稱。
2. 在指定 `"target":"project"` 之使用專案的 `project.json` 檔案中，參考來自 (1) 的名稱。

**AwesomeLibrary.CSharp** 和 **AwesomeLibrary.FSharp** 的 `project.json` 檔案現在需要參考 **AwesomeLibrary.Core** 作為 `project` 目標。  如果您未使用多目標，則可以使用全域 `dependencies` 項目：

```json
{
    "dependencies":{
        "AwesomeLibrary.Core":{
            "target":"project"
        }
    }
}
```

如果您是使用多目標，則可能無法使用全域 `dependencies` 項目，而且可能必須參考目標層級 `dependencies` 項目中的 **AwesomeLibrary.Core**。  例如，如果您將目標設為 `netstandard1.6`，則可以執行下列這類作業：

```json
{
    "frameworks":{
        "netstandard1.6":{
            "dependencies":{
                "AwesomeLibrary.Core":{
                    "target":"project"
                }
            }
        }
    }
}
```

### <a name="structuring-a-solution"></a>建構方案

多專案方案的另一個重要部分是建立不錯的整體專案結構。 若要建構多專案程式庫，您必須使用最上層 `/src` 和 `/test` 資料夾︰

```
/AwesomeLibrary
|__global.json
|__/src
   |__/AwesomeLibrary.Core
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.CSharp
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.FSharp
      |__Source Files
      |__project.json
|__/test
   |__/AwesomeLibrary.Core.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.CSharp.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.FSharp.Tests
      |__Test Files
      |__project.json
```

這個方案的 `global.json` 檔案如下所示：

```json
{
    "projects":["src", "test"]
}
```

這種方式遵循專案範本在 `dotnet new` 命令建立中所建立的相同模式，其中所有專案都是放在 `/src` 目錄下方，而且所有測試都是放在 `/test` 目錄下方。

以下是如何還原套件、建置和測試整個專案︰

```
$ dotnet restore
$ cd src/AwesomeLibrary.FSharp
$ dotnet build
$ cd ../AwesomeLibrary.CSharp
$ dotnet build
$ cd ../../test/AwesomeLibrary.Core.Tests
$ dotnet test
$ cd ../AwesomeLibrary.CSharp.Tests
$ dotnet test
$ cd ../AwesomeLibrary.FSharp.Tests
$ dotnet test
```

就是這麼容易！

