---
title: "開始使用 C# 和 Visual Studio 程式碼的 C# 手冊"
description: "了解如何在 C# 中使用 Visual Studio Code 建立並偵錯您的第一個 .NET Core 應用程式。"
keywords: "C#, 使用者入門, 取得, 安裝, Visual Studio Code, 跨平台"
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.openlocfilehash: 3a9de689946507e4b6d89f684461d65049b3375a
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# 與 Visual Studio Code 使用者入門

.NET Core 提供快速且模組化的平台，可建立在 Windows、Linux 和 macOS 上執行的應用程式。 搭配使用 Visual Studio Code 與 C# 擴充功能，以取得具備 C# IntelliSense (智慧型程式碼完成) 與偵錯完整支援的強大編輯體驗。

## <a name="prerequisites"></a>必要條件

1. 安裝 [Visual Studio Code (英文)](https://code.visualstudio.com/)。
2. 安裝 [.NET Core SDK (英文)](https://www.microsoft.com/net/download/core)。
3. 從 Visual Studio Code Marketplace 安裝 [C# 擴充功能 (英文)](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)。

## <a name="hello-world"></a>Hello World

讓我們在 .NET Core 上開始進行簡單的 "Hello World" 程式：

1. 開啟專案：

    * 開啟 Visual Studio Code。
    * 按一下左側功能表上的 [檔案總管] 圖示，然後按一下 [開啟資料夾]。
    * 選取**檔案** > **開啟資料夾**從主功能表開啟資料夾中，您要 C# 專案中，按一下**選取資料夾**。 範例中，我們正在建立資料夾，名為受測專案的*HelloWorld*。

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. 初始化 C# 專案：
    * 選取從 Visual Studio 程式碼開啟整合式終端機**檢視** > **整合的終端機**從主功能表。
    * 在終端機視窗中，輸入 `dotnet new console`。
    * 此命令會建立`Program.cs`已經寫入，以及 C# 專案檔名為簡單"Hello World"程式資料夾中的檔案`HelloWorld.csproj`。

      ![DotNet 新增命令](media/with-visual-studio-code/dotnetnew.png)

3. 解析組建資產：

    * 如**.NET Core 1.x**，型別`dotnet restore`。 執行 `dotnet restore` 可讓您存取建置專案所需的必要 .NET Core 封裝。

      ![DotNet 還原命令](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. 執行 "Hello World" 程式︰

    * 輸入 `dotnet run`。 

      ![DotNet 執行命令](media/with-visual-studio-code/dotnetrun.png)

您也可以觀看簡短的影片教學課程，以取得 [Windows (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) 或 [Linux (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) 上的進一步設定說明。

## <a name="debug"></a>偵錯

1. 按一下 *Program.cs* 來開啟它。 您在 Visual Studio 程式碼中，開啟 C# 檔案的第一次[OmniSharp](http://www.omnisharp.net/)在編輯器中載入。

    ![開啟 Program.cs 檔案](media/with-visual-studio-code/opencs.png)

2. Visual Studio 程式碼應該會提示您將加入遺漏的資產建置及偵錯您的應用程式。 選取 [是]。 

    ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

3. 若要開啟 [偵錯] 檢視，請按一下左側功能表上的 [偵錯] 圖示。

    ![開啟 [偵錯] 索引標籤](media/with-visual-studio-code/opendebug.png)

4. 尋找窗格頂端的綠色箭頭。 請確定它旁邊的下拉式清單已選取 `.NET Core Launch (console)`。

    ![選取 .NET Core](media/with-visual-studio-code/selectcore.png)

5. 將中斷點加入至專案，按一下 上**編輯器邊界**，也就是在編輯器中，第 9 行旁邊的行號左邊的空間。

    ![設定中斷點](media/with-visual-studio-code/setbreakpoint.png)

6. 若要啟動偵錯，請選取<kbd>F5</kbd>或綠色箭號。 當偵錯程式到達您在上一個步驟中設定的中斷點時，它會停止您程式的執行。
    * 偵錯時，您可以檢視您的本機變數的最上層的左窗格中，或使用 偵錯主控台。

    ![執行和偵錯](media/with-visual-studio-code/rundebug.png)

7. 選取頂端的綠色箭頭以繼續偵錯，或者選取頂端的紅色正方形以停止偵錯。

> [!TIP] 
> 如需在 Visual Studio Code 中使用 OmniSharp 進行 .NET Core 偵錯的詳細資訊與疑難排解祕訣，請參閱 [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) (設定 .NET Core 偵錯工具的指示)。

## <a name="see-also"></a>請參閱
[設定 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)   
[在 Visual Studio Code 中偵錯 (英文)](https://code.visualstudio.com/Docs/editor/debugging)
