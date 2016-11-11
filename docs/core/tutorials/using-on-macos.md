---
title: "在 macOS 上開始使用 .NET Core"
description: "在 macOS 上開始使用 .NET Core, 使用 Visual Studio Code"
keywords: .NET, .NET Core
author: bleroy
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
translationtype: Human Translation
ms.sourcegitcommit: 2339be6aef7e2ff942f1f1999a12f48ee4a77ee8
ms.openlocfilehash: 12b7bed380db53aad04f0615c6efa6152b3035b7

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-code"></a>在 macOS 上開始使用 .NET Core, 使用 Visual Studio Code

[Bertrand Le Roy](https://github.com/bleroy)、[Phillip Carter](https://github.com/cartermp)、[Bill Wagner](https://github.com/billwagner) 撰

由 [Toni Solarin Sodara](https://github.com/tsolarin) 貢獻

本文件提供使用 [Visual Studio Code](http://code.visualstudio.com) 建立 .NET Core 方案的步驟與工作流程導覽。
您將了解如何建立專案、建立單元測試、使用偵錯工具，以及透過 [NuGet](http://nuget.org) 納入協力廠商程式庫。

這篇文章會在 Mac OS 上使用 Visual Studio Code。 有差異之處，會指出 Windows 平台的差異。

## <a name="prerequisites"></a>必要條件

開始之前，您必須安裝 [.NET Core SDK](https://www.microsoft.com/net/core)，這目前在預覽版本。 .NET Core SDK 包含 .NET Core 架構和執行階段的最新版本。

您也需要安裝 [Visual Studio Code](http://code.visualstudio.com)。
在這篇文章的過程中，您也將安裝延伸模組，改善 .NET Core 開發經驗。

您可以在 [.NET 首頁](http://dot.net)找到以上所有鏈結。

## <a name="getting-started"></a>快速入門

本教學課程中的來源位於 [GitHub](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden)。

啟動 Visual Studio Code。 按 Ctrl + '\`' (後引號字元)，在 VS Code 中開啟內嵌的終端機。 (或者，您想要的話，可以使用不同的終端機視窗。)

在我們完成時，您將建立三個專案︰程式庫專案、該程式庫專案的測試，以及利用程式庫的主控台應用程式。 您將針對這三個專案遵循標準資料夾結構。 遵循此標準的資料夾結構，表示 .NET Core SDK 工具了解您的實際執行程式碼專案與測試程式碼專案之間的關係。 這可讓您的開發經驗更具生產力。

現在就開始建立這些資料夾。 在終端機中，建立 'golden' 目錄。 在該目錄下建立 `src` 和 `test` 目錄。 在 `src` 下建立 `app` 和 `library` 目錄。 在 `test` 中建立 `test-library` 目錄。 您可以在 VS Code 中使用終端機，或在 VS Code 中的父資料夾上按一下並選取 [新資料夾] 圖示，來完成此動作。

在 VS Code 中，開啟 'golden' 目錄。 這個目錄是您方案的根目錄。

接下來，在方案的根目錄中建立 `global.json` 檔案。
`global.json` 的內容為：

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

此時，您的目錄樹狀結構看起來如下所示︰


```
/golden
|__global.json
|__/src
   |__/app
   |__/library
|__/test
   |__/test-library
```

### <a name="writing-the-library"></a>撰寫程式庫

您的下一個工作是建立程式庫。 在終端機視窗 (VS Code 中的內嵌終端機，或另一個終端機) 中，切換至 `golden/src/library`，然後輸入命令 `dotnet new -t lib`。
這會建立含有兩個檔案的程式庫專案︰`project.json` 和 `Library.cs`。

`project.json`包含下列資訊：

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {},
  "frameworks": {
    "netstandard1.6": {
      "dependencies": {
        "NETStandard.Library": "1.6.0"
      }
    }
  }
}
```


此程式庫專案將會利用物件的 JSON 表示法，因此請新增 `Newtonsoft.Json` NuGet 套件的參考。 在 `project.json` 中新增最新的套件發行前版本作為相依性︰

```json
"dependencies": {
    "Newtonsoft.Json": "9.0.1-beta1"
},
```

完成新增這些相依性之後，您需要將這些套件安裝到工作區。 執行 `dotnet restore` 命令來更新所有相依性，並在專案目錄中寫入 `project.lock.json` 檔案。 這個檔案包含專案中所有相依性的完整相依性樹狀結構。 您不需要讀取這個檔案，它是由 .NET Core SDK 中的工具所使用。

現在，讓我們更新 C# 程式碼。 讓我們建立 `Thing` 類別，其中包含一個公用的方法。 這個方法會傳回兩個數字的總和，但其作法是將該數字轉換成 JSON 字串，然後再還原序列化。 將檔案 `Library.cs` 重新命名為 `Thing.cs`。 然後，使用下列內容取代現有的程式碼 (適用於範本產生的類別 1)：

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

這會利用許多現代 C# 功能，例如靜態 using、運算式主體成員和插補字串，您可以在[了解 C#](../../csharp/index.md) 一節中了解這些。

既然您已更新程式碼，便可以使用 `dotnet build` 建置程式庫。

您現在在 `golden/src/library/bin/Debug/netstandard1.6` 下有已建置的 `library.dll` 檔案。

### <a name="writing-the-test-project"></a>撰寫測試專案

我們將為您已建置的這個程式庫建置測試專案。 切換至 `test/test-library` 目錄。 執行 `dotnet new -t xunittest` 建立新的測試專案。 

您必須為上述步驟中所撰寫的程式庫新增相依性節點。 開啟 `project.json` 並更新相依性區段如下 (包括 `library` 節點，也就是底下的最後一個節點)：

```json
"dependencies": {
  "System.Runtime.Serialization.Primitives": "4.1.1",
  "xunit": "2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "library": {
    "target": "project"
  }
}
```

`library` 節點指定此相依性應該解析為目前工作區中的專案。 如果未明確指定，有可能測試專案會針對具有相同名稱的 NuGet 套件建置。

既然已正確設定相依性，就讓我們建立您的程式庫的測試。 開啟 `Tests.cs` 並將其內容取代為下列程式碼：

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

現在，執行 `dotnet restore`、`dotnet build` 和 `dotnet test`。
xUnit 主控台測試執行器會執行一項測試，並回報它通過。 

### <a name="writing-the-console-app"></a>撰寫主控台應用程式

在終端機中，切換至 `golden/src/app` 目錄。 執行 `dotnet new` 以建立新的主控台應用程式。

您的主控台應用程式會依賴您在先前步驟中建置和測試的程式庫。 您需要藉由編輯 `project.json` 新增此相依性來表示這點。  在 `dependencies` 節點中，新增 `library` 節點，如下所示︰

```json
"dependencies": {
  "library": {
    "target": "project"
  }
}
```

`project` 節點在這裡很重要，因為它過去在測試程式庫中。 它表示這是目前方案中的專案，而不是 NuGet 套件。

執行 `dotnet restore` 還原所有相依性。 開啟 `program.cs` 並將 `Main` 方法的內容取代為這一行︰

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

您必須將兩個 `using` 指示詞新增到檔案的頂端︰

```csharp
using static System.Console;
using Library;
```

然後，執行 `dotnet build`。 如此會建立組件，而您可以輸入 `dotnet run` 來執行可執行檔。

### <a name="debugging-your-application"></a>偵錯應用程式

您可以在 VS Code 中使用 C# 延伸模組偵錯您的程式碼。
按下 `F1` 開啟 VS Code 調色盤以安裝此延伸模組。 輸入 `ext install` 查看延伸模組的清單。 選取 C# 延伸模組。 (更多詳細資料位於 [Visual Studio Code C# 延伸模組文件](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) 頁面。)

安裝延伸模組之後，VS Code 將要求您重新啟動應用程式以載入新的延伸模組。 安裝延伸模組之後，您可以開啟 [偵錯工具] 索引標籤 (請參閱圖)。

![VS Code 偵錯工具](./media/using-on-macos/vscodedebugger.png)


當您啟動偵錯工具時，VS Code 會指示您設定偵錯工具。 當您這樣做時，它會建立 `.vscode` 目錄，其中含有兩個檔案︰`tasks.json` 和 `launch.json`。 這兩個檔案會控制偵錯工具組態。 在大部分的專案中，此目錄不會納入原始檔控制。
它包含在與本逐步解說相關聯的範例中，因此您可以看到需要進行的編輯。

您的方案包含多個專案，因此請修改這些每個檔案，以執行正確的命令。 首先，開啟 `tasks.json`。 預設建置工作會在工作區的來源目錄執行 `dotnet build`。 相反地，在您想要在 `src/app` 目錄中執行它。 您需要新增 `options` 節點以將目前工作目錄設定為它︰

```json
"options": {
    "cwd": "${workspaceRoot}/src/app"
}
```

接下來，您必須開啟 `launch.json` 並更新程式路徑。 您會看到在 "configurations" 下有一個說明程式的節點。 您會看到︰

```json
"program": "${workspaceRoot}/bin/Debug/<target-framework>/<project-name.dll>",
```

您會將它變更為︰

```json
"program": "${workspaceRoot}/src/app/bin/Debug/netcoreapp1.0/app.dll",
```

如果您在 Windows 上執行，則需要更新應用程式的 `project.json` (在 `src/app` 目錄)，以產生可移植的 PDB 檔案 (這在 Mac OSX 和 Linux 上會預設發生)。
在 `buildOptions` 內新增 `debugType` 節點 。 您必須針對 `src/app` 和 `src/library` 資料夾，在 `project.json` 中新增 `debugType` 節點。

```json
  "buildOptions": {
    "debugType": "portable"
  },
```

在 `Main` 中的 `WriteLine` 陳述式設定中斷點。 您可以按 `F9` 鍵，或在您要設定中斷點的該行左邊界按一下滑鼠按鈕。 在 VS Code 畫面左邊按 [偵錯] 圖示，開啟偵錯工具 (請參閱圖)。 然後，按下 [播放] 按鈕在偵錯工具中啟動應用程式。

您應該會遇到中斷點。 逐步執行 `Get` 方法，並確定您已傳入正確的引數。 確定實際答案為 42。



<!--HONumber=Nov16_HO1-->


