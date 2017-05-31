---
title: "開始使用 Visual Studio Code | C# 指南"
description: "了解如何在 C# 中使用 VS Code 建立您的第一個 .NET Core 應用程式並進行偵錯。"
keywords: "C#, 使用者入門, 取得, 安裝, Visual Studio Code, 跨平台"
author: kendrahavens
ms.author: mairaw
ms.date: 5/02/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.translationtype: Human Translation
ms.sourcegitcommit: d00f2096e0799107a8a2ff1d12274c6026d4c27a
ms.openlocfilehash: a8233995046e6fdf980bf630da18908a02d2bfb0
ms.contentlocale: zh-tw
ms.lasthandoff: 05/14/2017

---

# <a name="get-started-with-visual-studio-code"></a>開始使用 Visual Studio Code

.NET Core 提供您一個快速且模組化的平台，以建立可在 Windows、Linux 和 macOS 上執行的伺服器應用程式。 搭配使用 Visual Studio Code 與 C# 擴充功能，以取得具備 C# IntelliSense (智慧型程式碼完成) 與偵錯完整支援的強大編輯體驗。

## <a name="prerequisites"></a>必要條件

1. 安裝 [Visual Studio Code (英文)](https://code.visualstudio.com/)。
2. 安裝 [.NET Core SDK (英文)](https://www.microsoft.com/net/download/core)。
3. 從 Visual Studio Code Marketplace 安裝 [C# 擴充功能 (英文)](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)。

## <a name="hello-world"></a>Hello World

讓我們在 .NET Core 上開始進行簡單的 "Hello World" 程式：

1. 開啟專案：

    * 開啟 VS Code。
    * 按一下左側功能表上的 [檔案總管] 圖示，然後按一下 [開啟資料夾]。
    * 選取您想要放置 C# 專案的資料夾，然後按一下 [選取資料夾]。 針對本範例，我們將為專案建立一個名為 'HelloWorld' 的資料夾。 

  ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

    * 或者，您可以從主功能表選取 [檔案]  >  [開啟資料夾]，來開啟您的專案資料夾。

2. 初始化 C# 專案：
    * 輸入 <kbd>CTRL</kbd>+<kbd>\`</kbd> (倒引號) 來從 VS Code 開啟 [整合式終端機]。
    * 在終端機視窗中，輸入 `dotnet new console`。
    * 這會在您的資料夾中建立已撰寫簡單 "Hello World" 程式的 `Program.cs` 檔案，以及名稱為 `HelloWorld.csproj` 的 C# 專案檔。

  ![DotNet 新增命令](media/with-visual-studio-code/dotnetnew.png)

3. 解析組建資產：

    * 輸入 `dotnet restore`。 執行 `dotnet restore` 可讓您存取建置專案所需的必要 .NET Core 封裝。

  ![DotNet 還原命令](media/with-visual-studio-code/dotnetrestore.png)

4. 執行 "Hello World" 程式︰

    * 輸入 `dotnet run`。 

  ![DotNet 執行命令](media/with-visual-studio-code/dotnetrun.png)

您也可以觀看簡短的影片教學課程，以取得 [Windows (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) 或 [Linux (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) 上的進一步設定說明。

## <a name="debug"></a>偵錯
1. 按一下 *Program.cs* 來開啟它。 在 VS Code 中首次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp (英文)](http://www.omnisharp.net/)。

  ![開啟 Program.cs 檔案](media/with-visual-studio-code/opencs.png)

2. VS Code 會提示您加入遺失的資產，以針對您的應用程式進行建置及偵錯。 選取 [是]。 

  ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

3. 若要開啟 [偵錯] 檢視，請按一下左側功能表上的 [偵錯] 圖示。

  ![開啟 [偵錯] 索引標籤](media/with-visual-studio-code/opendebug.png)

4. 尋找窗格頂端的綠色箭頭。 請確定它旁邊的下拉式清單已選取 `.NET Core Launch (console)`。

  ![選取 .NET Core](media/with-visual-studio-code/selectcore.png)

5. 按一下第 9 行旁邊的「編輯器邊界」(編輯器中行號左側的空白處)，將中斷點新增至您的專案。

  ![設定中斷點](media/with-visual-studio-code/setbreakpoint.png)

6. 選取 <kbd>F5</kbd> 或綠色箭頭來開始偵錯。 當偵錯程式到達您在上一個步驟中設定的中斷點時，它會停止您程式的執行。
    * 進行偵錯時，您可以在左上角窗格中，或使用偵錯主控台來檢視您的本機變數。

  ![執行和偵錯](media/with-visual-studio-code/rundebug.png)

7. 選取頂端的綠色箭頭以繼續偵錯，或者按下紅色方形以停止偵錯。

> [!TIP] 
> 如需在 VS Code 中使用 OmniSharp 進行 .NET Core 偵錯的詳細資訊與疑難排解秘訣，請參閱[設定 .NET Core 偵錯工具的指示 (英文)](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)。

## <a name="see-also"></a>請參閱
[設定 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)   
[在 Visual Studio Code 中偵錯 (英文)](https://code.visualstudio.com/Docs/editor/debugging)

