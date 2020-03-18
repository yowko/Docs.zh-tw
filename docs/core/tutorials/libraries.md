---
title: 使用 .NET 核心 CLI 開發庫
description: 瞭解如何使用 .NET 核心 CLI 創建 .NET 核心庫。 您將建立支援多個架構的程式庫。
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503503"
---
# <a name="develop-libraries-with-the-net-core-cli"></a>使用 .NET 核心 CLI 開發庫

本文介紹如何使用 .NET 核心 CLI 為 .NET 編寫庫。 CLI 提供可在所有支援的作業系統上運作的有效率且低階體驗。 您仍然可以使用 Visual Studio 來建置程式庫，而且，如果那是您偏好的體驗，[請參閱 Visual Studio 指南](library-with-visual-studio.md)。

## <a name="prerequisites"></a>必要條件

您需要在電腦上安裝 [.NET Core SDK 和 CLI](https://dotnet.microsoft.com/download)。

針對這份文件中處理 .NET Framework 版本的一節，您需要在 Windows 電腦上安裝 [.NET Framework](https://dotnet.microsoft.com)。

此外，如果您希望支援較舊的 .NET 框架目標，則需要從[.NET 下載存檔頁](https://dotnet.microsoft.com/download/archives)安裝目標包或開發人員包。 請參閱這張表格︰

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

如果您不熟悉 .NET 標準，請參閱[.NET 標準](../../standard/net-standard.md)以瞭解更多資訊。

在該文章中，有一個表將 .NET 標準版本映射到各種實現：

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

以下是這個資料表在建立程式庫時的意義︰

您選擇的 .NET 標準版本將是訪問最新 API 和定位更多 .NET 實現和 .NET 標準版本的能力之間的權衡。 通過選擇`netstandardX.X`版本號（其中`X.X`版本號）並將其添加到專案檔案（`.csproj`或`.fsproj`）的版本，可以控制目標平臺和版本的範圍。

根據您的需求，在定位 .NET 標準時，您有三個主要選項。

1. 您可以使用範本提供的 .NET 標準的預設版本 ，`netstandard1.4`它允許您訪問 .NET 標準上的大多數 API，同時仍與 UWP、.NET 框架 4.6.1 和 .NET 標準 2.0 相容。

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. 您可以通過修改專案檔案`TargetFramework`節點中的值來使用較低版本或更高版本的 .NET 標準。

    .NET Standard 版本具備回溯相容。 這表示 `netstandard1.0` 程式庫是在 `netstandard1.1` 平台和更高版本上執行。 但是，沒有正向相容性。 下部 .NET 標準平臺不能引用較高的平臺。 這表示 `netstandard1.0` 程式庫無法參考目標設為 `netstandard1.1` 或更高版本的程式庫。 針對您的需求，選取正確混合使用 API 與平台支援的標準版本。 現在建議使用 `netstandard1.4`。

3. 如果要以 .NET 框架版本 4.0 或以下為目標，或者希望使用 .NET 框架中可用的 API，但不希望在 .NET`System.Drawing`標準（例如），請閱讀以下各節並瞭解如何多目標。

## <a name="how-to-target-net-framework"></a>如何定位 .NET 框架

> [!NOTE]
> 這些說明假定您的電腦上安裝了 .NET 框架。 請參閱安裝相依性的[必要條件](#prerequisites)。

請記住，此處使用的一些 .NET 框架版本不再受支援。 如需不支援的版本，請參閱 [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) (.NET Framework 支援週期原則 FAQ)。

如果要達到開發人員和專案的最大數量，請使用 .NET 框架 4.0 作為基準目標。 要定位 .NET 框架，首先使用與您希望支援 .NET 框架版本對應的正確目標框架 Moniker （TFM）。

| .NET Framework 版本 | TFM      |
| ---------------------- | -------- |
| .NET Framework 2.0     | `net20`  |
| .NET Framework 3.0     | `net30`  |
| .NET Framework 3.5     | `net35`  |
| .NET Framework 4.0     | `net40`  |
| .NET Framework 4.5     | `net45`  |
| .NET Framework 4.5.1   | `net451` |
| .NET Framework 4.5.2   | `net452` |
| .NET Framework 4.6     | `net46`  |
| .NET Framework 4.6.1   | `net461` |
| .NET Framework 4.6.2   | `net462` |
| .NET Framework 4.7     | `net47`  |
| .NET Framework 4.8     | `net48`  |

您接著將這個 TFM 插入專案檔的 `TargetFramework` 區段。 例如，下面介紹如何編寫以 .NET 框架 4.0 為目標的庫：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

就這麼簡單！ 儘管此僅為 .NET 框架 4 編譯，但您可以在較新版本的 .NET Framework 上使用庫。

## <a name="how-to-multitarget"></a>如何多目標

> [!NOTE]
> 下列指示假設您已在電腦上安裝 .NET Framework。 請參閱[必要條件](#prerequisites)小節，了解您需要安裝的相依性以及其下載位置。

當您的專案同時支援 .NET Framework 和 .NET Core 時，可能需要將目標設為舊版 .NET Framework。 在這個案例中，如果您想要為較新的目標使用較新的 API 和語言建構，請在程式碼中使用 `#if` 指示詞。 您也可能需要針對設為目標的每個平台新增不同的套件和相依性，以包含每個案例所需的不同 API。

例如，假設您的程式庫透過 HTTP 執行網路作業。 針對 .NET Standard 和 .NET Framework 4.5 版或更高版本，您可以使用 `System.Net.Http` 命名空間中的 `HttpClient` 類別。 不過，舊版 .NET Framework 沒有 `HttpClient` 類別，因此您可以改用這些項目之 `System.Net` 命名空間中的 `WebClient` 類別。

專案檔如下所示：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

您可在這裡發現三個主要變更︰

1. `TargetFramework` 節點已取代為 `TargetFrameworks`，而且其內表示三個 TFM。
1. 提取至一個 .NET Framework 參考的 `net40` 目標有一個 `<ItemGroup>` 節點。
1. 提取至兩個 .NET Framework 參考的 `net45` 目標有一個 `<ItemGroup>` 節點。

建置系統會得知 `#if` 指示詞中所使用的下列前置處理器符號︰

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

以下是利用個別目標之條件式編譯的範例︰

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
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
            string url = "https://www.dotnetfoundation.org/";

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
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

如果您使用 `dotnet build` 建置此專案，則會在 `bin/` 資料夾下方發現三個目錄：

```
net40/
net45/
netstandard1.4/
```

所有這些都包含每個目標的 `.dll` 檔案。

## <a name="how-to-test-libraries-on-net-core"></a>如何測試 .NET Core 上的程式庫

重要的是一定要可以跨平台進行測試。 您可以使用現成的 [xUnit](https://xunit.github.io/) 或 MSTest。 兩者都完全適用於在 .NET Core 上對程式庫進行單元測試。 如何設定具有測試專案的方案，將取決於[方案結構](#structuring-a-solution)。 下列範例假設測試及來源目錄位於相同的最上層目錄中。

> [!NOTE]
> 這使用一些[.NET 核心 CLI](../tools/index.md)命令。 如需詳細資訊，請參閱 [dotnet new](../tools/dotnet-new.md) 及 [dotnet sln](../tools/dotnet-sln.md)。

1. 設定方案。 您可以使用下列命令：

   ```dotnetcli
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

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. 還原套件並建置專案︰

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. 執行 `dotnet test` 命令，確認已執行 xUnit。 如果您選擇使用 MSTest，則應該會改為執行 MSTest 主控台執行器。

就這麼簡單！ 現在，您可以使用命令列工具跨所有平臺測試庫。 若要在設定好所有項目之後立即繼續測試，測試程式庫就會非常簡單︰

1. 對程式庫進行變更。
1. 在測試目錄中，從命令列中使用 `dotnet test` 命令來執行測試。

當您叫用 `dotnet test` 命令時，將會自動重建程式碼。

## <a name="how-to-use-multiple-projects"></a>如何使用多個專案

較大程式庫的常見需求是將功能放在不同的專案中。

假設您要構建一個可以在慣用 C# 和 F# 中使用的庫。 這意味著庫的消費者會以 C# 或 F# 自然的方式使用它。 例如，在 C# 中，您可能會如下使用程式庫︰

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

* **真棒庫.Core** - 包含庫所有邏輯的核心專案
* **真棒庫.CSharp** - 一個公共 API 的專案，旨在用於 C 中使用#
* **真棒庫.FSharp** - 一個公共 API 的專案，用於在 F 中使用#

您可以在終端機中執行下列命令，以產生與本指南相同的結構︰

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

這將添加上述三個專案以及一個將它們連結在一起的解決方案檔。 創建解決方案檔和連結專案將允許您從頂層還原和生成專案。

### <a name="project-to-project-referencing"></a>專案對專案參考

參考專案的最佳方式是使用 .NET Core CLI 來新增專案參考。 從 **AwesomeLibrary.CSharp** 及 **AwesomeLibrary.FSharp** 專案目錄中，您可以執行下列命令︰

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

**AwesomeLibrary.CSharp** 及 **AwesomeLibrary.FSharp** 的專案檔現在參考 **AwesomeLibrary.Core** 作為 `ProjectReference` 目標。  檢查專案檔並查看其中的下列內容，即可確認這項作業︰

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

如果您不想要使用 .NET Core CLI，則可以手動將這個區段新增至每個專案檔。

### <a name="structuring-a-solution"></a>建構方案

多專案方案的另一個重要部分是建立不錯的整體專案結構。 不過，您可以視需要組織程式碼，而且只要您使用 `dotnet sln add` 將每個專案連結至方案檔，就可以在方案層級執行 `dotnet restore` 及 `dotnet build`。
