---
title: 開始在 macOS 上使用 .NET Core
description: 本文件提供使用 Visual Studio Code 建立 .NET Core 方案的步驟及工作流程。
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: f1cb9b45c0ed1b4315361846fc065209088b57f8
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373792"
---
# <a name="get-started-with-net-core-on-macos"></a>開始在 macOS 上使用 .NET Core

本文件提供建立適用於 macOS 之 .NET Core 方案的步驟及工作流程。 了解如何建立專案、建立單元測試、使用偵錯工具，以及透過 [NuGet](https://www.nuget.org/) 納入協力廠商程式庫。

> [!NOTE]
> 這篇文章會在 macOS 上使用 [Visual Studio Code](https://code.visualstudio.com)。

## <a name="prerequisites"></a>必要條件

安裝 [.NET Core SDK (英文)](https://www.microsoft.com/net/core)。 .NET Core SDK 包含 .NET Core 架構和執行階段的最新版本。

安裝 [Visual Studio Code (英文)](https://code.visualstudio.com)。 在這篇文章的過程中，您也將安裝能改善 .NET Core 開發體驗的 Visual Studio Code 延伸模組。

請開啟 Visual Studio Code，並按下 <kbd>F1</kbd> 來開啟 Visual Studio Code 調色盤，以安裝 Visual Studio Code C# 延伸模組。 鍵入 **ext install** 來查看延伸模組的清單。 選取 C# 延伸模組。 重新啟動 Visual Studio Code 以啟動延伸模組。 如需詳細資訊，請參閱 [Visual Studio Code C# 延伸模組文件](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)。

## <a name="get-started"></a>開始使用

在本教學課程中，您會建立三個專案︰程式庫專案、該程式庫專案的測試，以及利用程式庫的主控台應用程式。 您可以在 GitHub 的 dotnet/samples 存放庫[檢視或下載來源](https://github.com/dotnet/samples/tree/master/core/getting-started/golden)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

啟動 Visual Studio Code。 按下 <kbd>Ctrl</kbd>+<kbd>\`</kbd> (倒引號字元)，或從功能表中選取 [檢視] > [整合式終端機]，以使用 Visual Studio Code 開啟內嵌終端機。 如果您想要在 Visual Studio Code 外部工作，則仍然可以使用總管 [在命令提示字元中開啟] 命令 (Mac 或 Linux 上的 [在終端機中開啟]) 來開啟外部殼層。

請從建立方案檔開始，而方案檔是作為一或多個 .NET Core 專案的容器。 在終端機中，建立 *golden* 資料夾，然後開啟該資料夾。 這個資料夾是您方案的根資料夾。 執行 [`dotnet new`](../tools/dotnet-new.md) 命令，建立新方案 *golden.sln*：

```console
dotnet new sln
```

從 *golden* 資料夾中，執行下列命令來建立程式庫專案，這樣會在 *library* 資料夾中產生 library.csproj 及 Class1.cs 這兩個檔案：

```console
dotnet new classlib -o library
```

執行 [`dotnet sln`](../tools/dotnet-sln.md) 命令，將新建立的 *library.csproj* 專案新增至方案：

```console
dotnet sln add library/library.csproj
```

*library.csproj* 檔案包含下列資訊：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

我們的程式庫方法會序列化及還原序列化 JSON 格式的物件。 若要支援 JSON 序列化及還原序列化，請新增 `Newtonsoft.Json` NuGet 套件的參考。 `dotnet add` 命令會新增項目至專案。 若要新增 NuGet 套件的參考，請使用 [`dotnet add package`](../tools/dotnet-add-package.md) 命令，並指定套件的名稱：

```console
dotnet add library package Newtonsoft.Json
```

這會將 `Newtonsoft.Json` 及其相依性新增至程式庫專案。 或者，手動編輯 *library.csproj* 檔案，並新增下列節點：

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

執行 [`dotnet restore`](../tools/dotnet-restore.md) ([請參閱注意事項](#dotnet-restore-note))，以還原相依性，並在其中有三個檔案的 *library* 內建立 *obj* 資料夾，包含 *project.assets.json* 檔案：

```console
dotnet restore
```

在 *library* 資料夾中，將檔案 *Class1.cs* 重新命名為 *Thing.cs*。 使用下列內容取代程式碼：

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

`Thing` 類別包含一個公用方法 `Get`，這個公用方法會傳回兩個數字的總和，而做法是將總和轉換成字串，然後將它還原序列化為整數。 這會利用一些現代 C# 功能，例如 [`using static`指示詞](../../csharp/language-reference/keywords/using-static.md)、[運算式主體成員](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)及[字串內插補點](../../csharp/language-reference/tokens/interpolated.md)。

使用 [`dotnet build`](../tools/dotnet-build.md) 命令建置程式庫。 這會在 *golden/library/bin/Debug/netstandard1.4* 底下產生 *library.dll* 檔案：

```console
dotnet build
```

## <a name="create-the-test-project"></a>建立測試專案

建置程式庫的測試專案。 從 *golden* 資料夾中，建立新的測試專案︰

```console
dotnet new xunit -o test-library
```

將測試專案新增至方案：

```console
dotnet sln add test-library/test-library.csproj
```

新增上一節中所建立之程式碼的專案參考，讓編譯器可以尋找及使用程式庫專案。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

或者，手動編輯 *test-library.csproj* 檔案，並新增下列節點：

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

既然已正確設定相依性，請建立您程式庫的測試。 開啟 *UnitTest1.cs* 並將其內容取代為下列程式碼：

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

請注意，當您第一次建立單元測試時，確認值 42 不等於 19+23 (或 42) (`Assert.NotEqual`)，而這項建立作業會失敗。 建置單元測試的重要步驟是建立測試，以確認其邏輯在第一次時失敗一次。

從 *golden* 資料夾中，執行下列命令：

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

這些命令會以遞迴方式尋找所有專案來還原相依性、建置相依性，並啟動 xUnit 測試執行器來執行測試。 如您所預期，單一測試失敗。

編輯 *UnitTest1.cs* 檔案，並將判斷提示從 `Assert.NotEqual` 變更為 `Assert.Equal`。 從 *golden* 資料夾中執行下列命令，以重新執行測試，而這次測試會通過：

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>建立主控台應用程式

您透過下列步驟所建立的主控台應用程式依存於您先前建立的程式庫專案，並在它執行時呼叫它的程式庫方法。 使用這種模式的開發，您會看到如何建立多個專案的可重複使用程式庫。

從 *golden* 資料夾中，建立新的主控台應用程式︰

```console
dotnet new console -o app
```

將主控台應用程式專案新增至方案：

```console
dotnet sln add app/app.csproj
```

執行 `dotnet add reference` 命令，建立與程式庫的相依性︰

```console
dotnet add app/app.csproj reference library/library.csproj
```

執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note))，還原方案中三個專案的相依性。 開啟 *Program.cs*，並將 `Main` 方法的內容取代為下行：

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

將兩個 `using` 指示詞新增至 *Program.cs* 檔案的頂端：

```csharp
using static System.Console;
using Library;
```

執行下列 `dotnet run` 命令來執行可執行檔，而 `dotnet run` 的 `-p` 選項指定主要應用程式的專案。 應用程式會產生 "The answer is 42" 字串。

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>進行應用程式偵錯

在 `Main` 方法中的 `WriteLine` 陳述式設定中斷點。 做法是在游標位於 `WriteLine` 行上方時按下 <kbd>F9</kbd> 鍵，或在您要設定中斷點之行的左邊界按一下滑鼠。 紅色圓圈會出現在程式碼行旁邊的邊界。 到達中斷點時，會在執行中斷點行「之前」停止執行程式碼。

開啟偵錯工具索引標籤，方法是選取 Visual Studio Code 工具列中的偵錯圖示、選取功能表列中的 [檢視] > [偵錯]，或使用鍵盤快速鍵 <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>：

![Visual Studio Code 偵錯工具](./media/using-on-macos/visual-studio-code-debugger.png)

按下 [播放] 按鈕，在偵錯工具中啟動應用程式。 應用程式會開始執行，並執行至中斷點，然後停止。 逐步執行 `Get` 方法，並確定您已傳入正確的引數。 確認答案是 42。

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
