---
title: "使用跨平台工具開發程式庫"
description: "了解如何使用 .NET Core CLI 工具建立 .NET 程式庫。"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: c0525462ac5efaa8d96ac2bf4c12a823ef40df31
ms.contentlocale: zh-tw
ms.lasthandoff: 09/19/2017

---

# <a name="developing-libraries-with-cross-platform-tools"></a>使用跨平台工具開發程式庫

本文涵蓋如何使用跨平台 CLI 工具撰寫 .NET 的程式庫。 CLI 提供可在所有支援的作業系統上運作的有效率且低階體驗。 您仍然可以使用 Visual Studio 來建置程式庫，而且，如果那是您偏好的體驗，[請參閱 Visual Studio 指南](libraries-with-vs.md)。

## <a name="prerequisites"></a>必要條件

您需要在電腦上安裝 [.NET Core SDK 和 CLI](https://www.microsoft.com/net/core)。

針對這份文件中處理 .NET Framework 版本的一節，您需要在 Windows 電腦上安裝 [.NET Framework](http://getdotnet.azurewebsites.net/)。

此外，如果您想要支援較舊的 .NET Framework 目標，則需要從 [.NET target platforms](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html) 頁面安裝較舊 Framework 版本的目標/開發人員套件。 請參閱這張表格︰

| .NET Framework 版本 | 要下載的項目                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET Framework 4.6.1 目標套件                    |
| 4.6                    | .NET Framework 4.6 目標套件                      |
| 4.5.2                  | .NET Framework 4.5.2 開發人員套件                    |
| 4.5.1                  | .NET Framework 4.5.1 開發人員套件                    |
| 4.5                    | 適用於 Windows 8 的 Windows 軟體開發套件         |
| 4.0                    | 適用於 Windows 7 的 Windows SDK 及 .NET Framework 4         |
| 2.0、3.0 和 3.5      | .NET Framework 3.5 SP1 執行階段 (或 Windows 8+ 版本) |

## <a name="how-to-target-the-net-standard"></a>如何將目標設為 .NET Standard

如果您不是很熟悉 .NET Standard，請參閱 [.NET Standard](../../standard/net-standard.md) 來深入了解。

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

您選擇的 .NET Standard 版本將會在下列兩者間進行取捨：存取最新的 API，以及以多個 .NET 實作和 .NET Standard 版本為目標的能力。 您可以控制可設為目標之平台和版本的範圍，方法是選擇 `netstandardX.X` 版本 (其中 `X.X` 是版本號碼)，並將它新增至專案檔 (`.csproj` 或 `.fsproj`)。

將目標設為 .NET Standard 時，會有三個主要選項 (視需求而定)。

1. 您可以使用最新版本的 .NET Standard (`netstandard1.6`)，這適用於想要存取大部分 API 時，而且較少跨實作時則不用在意。
2. 您可以使用較低版本的 .NET Standard，以將目標設為較舊的 .NET 實作。 這裡的成本不包含存取一些最新的 API。
    
    例如，如果您想要確保與 .NET Framework 4.6 和更新版本相容，請挑選 `netstandard1.3`：

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```
    
    .NET Standard 版本具備回溯相容。 這表示 `netstandard1.0` 程式庫是在 `netstandard1.1` 平台和更高版本上執行。 不過，沒有往後相容性 - 較低的 .NET Standard 平台無法參考較高的平台。 這表示 `netstandard1.0` 程式庫無法參考目標設為 `netstandard1.1` 或更高版本的程式庫。 針對您的需求，選取正確混合使用 API 與平台支援的標準版本。 現在建議使用 `netstandard1.4`。
    
3. 如果您想要將目標設為 .NET Framework 4.0 或以下版本，或者想要使用位在 .NET Framework 中但不在 .NET Standard 中的 API (例如，`System.Drawing`)，請閱讀下列各節，並了解如何使用多目標。

## <a name="how-to-target-the-net-framework"></a>如何將目標設為 .NET Framework

> [!NOTE]
> 這些指示假設您已在電腦上安裝 .NET Framework。 請參閱安裝相依性的[必要條件](#prerequisites)。

請記住，將不再支援這裡使用的一些 .NET Framework 版本。 如需不支援的版本，請參閱 [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) (.NET Framework 支援週期原則 FAQ)。

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
.NET Framework 4.7   --> net47
```

您接著將這個 TFM 插入專案檔的 `TargetFramework` 區段。 例如，以下是如何撰寫目標設為 .NET Framework 4.0 的程式庫：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

就是這麼容易！ 雖然這只是針對 .NET Framework 4 所編譯，但是您可以在較新版的 .NET Framework 上使用程式庫。

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
> 下列指示假設您已在電腦上安裝 .NET Framework。 請參閱[必要條件](#prerequisites)小節，了解您需要安裝的相依性以及其下載位置。

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

1. `TargetFramework` 節點已取代為 `TargetFrameworks`，而且其內表示三個 TFM。
1. 提取至一個 .NET Framework 參考的 `net40 ` 目標有一個 `<ItemGroup>` 節點。
1. 提取至兩個 .NET Framework 參考的 `net45` 目標有一個 `<ItemGroup>` 節點。

建置系統會得知 `#if` 指示詞中所使用的下列前置處理器符號︰

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

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

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
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

重要的是一定要可以跨平台進行測試。 您可以使用現成的 [xUnit](http://xunit.github.io/) 或 MSTest。 兩者都完全適用於在 .NET Core 上對程式庫進行單元測試。 如何設定具有測試專案的方案，將取決於[方案結構](#structuring-a-solution)。 下列範例假設測試及來源目錄位於相同的最上層目錄中。

> [!NOTE]
> 這會使用某些 [.NET Core CLI 命令](../tools/index.md)。 如需詳細資訊，請參閱 [dotnet new](../tools/dotnet-new.md) 及 [dotnet sln](../tools/dotnet-sln.md)。

1. 設定方案。 您可以使用下列命令：

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   這會建立專案，並將它們同時連結在方案中。 您的 `SolutionWithSrcAndTest` 目錄應該如下所示：

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. 巡覽至測試專案的目錄，並將參考從 `MyProject` 新增至 `MyProject.Test`。

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. 還原套件並建置專案︰

   ```bash
   dotnet restore
   dotnet build
   ```

1. 執行 `dotnet test` 命令，確認已執行 xUnit。 如果您選擇使用 MSTest，則應該會改為執行 MSTest 主控台執行器。
    
就是這麼容易！ 您現在可以使用命令列工具跨所有平台來測試程式庫。 若要在設定好所有項目之後立即繼續測試，測試程式庫就會非常簡單︰

1. 對程式庫進行變更。
1. 在測試目錄中，從命令列中使用 `dotnet test` 命令來執行測試。

當您叫用 `dotnet test` 命令時，將會自動重建程式碼。

只要新增相依性，就請記得從命令列執行 `dotnet restore`，這樣您就可以繼續往下進行！

## <a name="how-to-use-multiple-projects"></a>如何使用多個專案

較大程式庫的常見需求是將功能放在不同的專案中。

假設您想要建置可在慣用 C# 和 F# 中使用的程式庫。 這表示您程式庫的消費者透過 C# 或 F# 的原本方式來使用程式庫。 例如，在 C# 中，您可能會如下使用程式庫︰

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

在 F# 中，它可能如下所示：

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
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

這會新增上方的三個專案以及將它們連結在一起的方案檔。 建立方案檔及連結專案可讓您從最上層還原與建置專案。

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

參考專案的最佳方式是使用 .NET Core CLI 來新增專案參考。 從 **AwesomeLibrary.CSharp** 及 **AwesomeLibrary.FSharp** 專案目錄中，您可以執行下列命令︰

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

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

如果您不想要使用 .NET Core CLI，則可以手動將這個區段新增至每個專案檔。

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

