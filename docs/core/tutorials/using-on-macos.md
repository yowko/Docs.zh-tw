---
title: "在 macOS 上開始使用 .NET Core"
description: "在 macOS 上開始使用 .NET Core, 使用 Visual Studio Code"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: c4d1b7690ca87f2a1a9ced4d82e47aee2f7ecc9f
ms.lasthandoff: 03/07/2017

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-code"></a>在 macOS 上開始使用 .NET Core, 使用 Visual Studio Code

本文件提供使用 [Visual Studio Code](http://code.visualstudio.com) 建立 .NET Core 方案的步驟與工作流程導覽。
您將了解如何建立專案、建立單元測試、使用偵錯工具，以及透過 [NuGet](http://nuget.org) 納入協力廠商程式庫。

這篇文章會在 Mac OS 上使用 Visual Studio Code。 有差異之處，會指出 Windows 平台的差異。

## <a name="prerequisites"></a>必要條件

開始之前，您必須安裝 [.NET Core SDK](https://www.microsoft.com/net/core)。 .NET Core SDK 包含 .NET Core 架構和執行階段的最新版本。

您也需要安裝 [Visual Studio Code](http://code.visualstudio.com)。
在這篇文章的過程中，您也將安裝延伸模組，改善 .NET Core 開發經驗。

## <a name="getting-started"></a>快速入門

本教學課程中的原始碼來源位於 [GitHub](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden)。

啟動 Visual Studio Code。 按 Ctrl + '\`' (後引號字元)，在 VS Code 中開啟內嵌的終端機。 (或者，您想要的話，可以使用不同的終端機視窗。)

在我們完成時，您將建立三個專案︰程式庫專案、該程式庫專案的測試，以及利用程式庫的主控台應用程式。 

現在就開始建立這些資料夾。 在終端機中，建立 'golden' 目錄。 在 VS Code 中，開啟 *golden* 目錄。 這個目錄是您方案的根目錄。 執行 [`dotnet new`](../tools/dotnet-new.md) 命令，建立新的方案：

```
dotnet new sln
```

此命令會建立整個方案的 *golden.sln* 檔案。

您的下一個工作是建立程式庫。 在終端機視窗 (VS Code 中的內嵌終端機，或另一部終端機) 中，切換至 *golden/*，然後輸入命令：

```
dotnet new classlib -o library
```

這會在 *library* 目錄中建立一個程式庫專案，其中包含兩個檔案︰*library.csproj* 和 *Class1.cs*。 您想要在方案中包含該程式庫專案。 執行 [`dotnet sln`](../tools/dotnet-sln.md) 命令，將新建立的 *library.csproj* 專案新增至方案：

```
dotnet sln add library/library.csproj
```

讓我們來看您所建立的專案。 *library.csproj* 檔案包含下列資訊：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

此程式庫專案將會利用 JSON 的物件表示法，因此請新增 `Newtonsoft.Json` NuGet 套件的參考。 `dotnet add` 命令會新增項目至專案。 若要將參考新增至 NuGet 套件，您可以使用 `package` 命令並指定套件的名稱。 

```
dotnet add library package Newtonsoft.Json
```

這會將 `Newtonsoft.Json` 及其相依性新增至程式庫專案。 或者，您可以手動編輯 *library.csproj* 檔案並新增下列節點：

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>10.0.1</Version>
  </PackageReference>
</ItemGroup>
```

完成新增這些相依性之後，您需要將這些套件安裝到工作區。 執行 `dotnet restore` 命令來更新所有相依性，並在專案目錄下撰寫 *obj/project.assets.json* 檔案。 這個檔案包含專案中所有相依性的完整相依性樹狀結構。 您不需要讀取這個檔案，它是由 .NET Core SDK 中的工具所使用。

現在，讓我們更新 C# 程式碼。 讓我們建立 `Thing` 類別，其中包含一個公用的方法。 這個方法會傳回兩個數字的總和，但其作法是將該數字轉換成 JSON 字串，然後再還原序列化。 將檔案 *Class1.cs* 重新命名為 *Thing.cs*。 然後，使用下列內容取代現有的程式碼 (適用於範本產生的類別)：

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

這會利用一些現代 C# 功能，例如靜態 using、運算式主體成員和插補字串，您可以在[了解 C#](../../csharp/index.md) 一節中了解這些功能。

既然您已更新程式碼，便可以使用 `dotnet build` 建置程式庫。

您現在於 *golden/library/bin/Debug/netstandard1.4* 下有內建 *library.dll* 檔案。

### <a name="writing-the-test-project"></a>撰寫測試專案

我們將為您已建置的這個程式庫建置測試專案。 變更為 *golden* 目錄。 執行 `dotnet new xunit -o test-library` 建立新的測試專案。 您也需要藉由執行 `dotnet sln add test-library/test-library.csproj` 將此專案新增至方案。

您必須為上述步驟中所撰寫的程式庫新增相依性節點。 `dotnet add reference` 命令可達成目的：

```
dotnet add test-library/test-library.csproj reference library/library.csproj
```

或者，您可以手動編輯 *test-library.csproj* 檔案並新增下列節點：

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

`library` 節點指定此相依性應該解析為目前工作區中的專案。 如果未明確指定，有可能測試專案會針對具有相同名稱的 NuGet 套件建置。

既然已正確設定相依性，就讓我們建立您的程式庫的測試。 開啟 *UnitTest1.cs* 並將其內容取代為下列程式碼：

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.Equal(42, new Thing().Get(19, 23));
        }
    }
}
```

現在，執行 `dotnet restore` 和 `dotnet build`。 這些命令會以遞迴方式尋找所有要還原及建置相依性的專案。
最後，執行 `dotnet test test-library/test-library.csproj` 以執行測試。
xUnit 主控台測試執行器會執行一項測試，並回報它通過。 

### <a name="writing-the-console-app"></a>撰寫主控台應用程式

在終端機中，執行 `dotnet new console -o app` 以建立新的主控台應用程式。 此專案也是方案的一部分，因此請執行 `dotnet sln add app/app.csproj` 將專案新增至方案。

您的主控台應用程式會依賴您在先前步驟中建置和測試的程式庫。 您需要藉由再次執行 `dotnet add reference` 來表示這點：

```
dotnet add app/app.csproj reference library/library.csproj
```

執行 `dotnet restore` 還原所有相依性。 開啟 *program.cs* 並將 `Main` 方法的內容取代為這一行：

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

您必須將兩個 `using` 指示詞新增到檔案的頂端︰

```csharp
using static System.Console;
using Library;
```

然後，執行 `dotnet build`。 如此會建立組件，而您可以輸入 `dotnet run -p app/app.csproj` 來執行可執行檔。
`dotnet run` 的 `-p` 引數會指定主應用程式的專案。

### <a name="debugging-your-application"></a>偵錯應用程式

您可以在 VS Code 中使用 C# 延伸模組偵錯您的程式碼。
按下 `F1` 開啟 VS Code 調色盤以安裝此延伸模組。 輸入 `ext install` 查看延伸模組的清單。 選取 C# 延伸模組。 (更多詳細資料位於 [Visual Studio Code C# 延伸模組文件](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) 頁面。)

安裝延伸模組之後，VS Code 將要求您重新啟動應用程式以載入新的延伸模組。 安裝延伸模組之後，您可以開啟 [偵錯工具] 索引標籤 (請參閱圖)。

![VS Code 偵錯工具](./media/using-on-macos/vscodedebugger.png)

在 `Main` 中的 `WriteLine` 陳述式設定中斷點。 您可以按 `F9` 鍵，或在您要設定中斷點的該行左邊界按一下滑鼠按鈕。 在 VS Code 畫面左邊按 [偵錯] 圖示，開啟偵錯工具 (請參閱圖)。 然後，按下 [播放] 按鈕在偵錯工具中啟動應用程式。

您應該會遇到中斷點。 逐步執行 `Get` 方法，並確定您已傳入正確的引數。 確定實際答案為 42。

