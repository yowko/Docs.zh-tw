---
title: C# 與 Visual Studio Code 使用者入門 - C# 指南
description: 了解如何在 C# 中使用 Visual Studio Code 建立並偵錯您的第一個 .NET Core 應用程式。
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 8958c39ba16cadbfab95e35fa36e8e85ce0a4ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213612"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="fcaab-103">C# 與 Visual Studio Code 使用者入門</span><span class="sxs-lookup"><span data-stu-id="fcaab-103">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="fcaab-104">.NET Core 提供快速且模組化的平台，可建立在 Windows、Linux 和 macOS 上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcaab-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="fcaab-105">搭配使用 Visual Studio Code 與 C# 擴充功能，以取得具備 C# IntelliSense (智慧型程式碼完成) 與偵錯完整支援的強大編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="fcaab-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fcaab-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="fcaab-106">Prerequisites</span></span>

1. <span data-ttu-id="fcaab-107">安裝 [Visual Studio Code (英文)](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="fcaab-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="fcaab-108">安裝 [.NET Core SDK (英文)](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="fcaab-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="fcaab-109">安裝適用於 Visual Studio Code 的 [C# 擴充功能](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="fcaab-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="fcaab-110">如需如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能市集](https://code.visualstudio.com/docs/editor/extension-gallery) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="fcaab-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="fcaab-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="fcaab-111">Hello World</span></span>

<span data-ttu-id="fcaab-112">讓我們在 .NET Core 上開始進行簡單的 "Hello World" 程式：</span><span class="sxs-lookup"><span data-stu-id="fcaab-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="fcaab-113">開啟專案：</span><span class="sxs-lookup"><span data-stu-id="fcaab-113">Open a project:</span></span>

    * <span data-ttu-id="fcaab-114">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="fcaab-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="fcaab-115">按一下左側功能表上的 [檔案總管] 圖示，然後按一下 [開啟資料夾]。</span><span class="sxs-lookup"><span data-stu-id="fcaab-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="fcaab-116">從主要功能表中選取 [檔案] > [開啟資料夾]，以開啟您想要放置 C# 專案的資料夾，然後按一下 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="fcaab-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="fcaab-117">針對本範例，我們將為專案建立一個名為 *HelloWorld* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fcaab-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="fcaab-119">初始化 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="fcaab-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="fcaab-120">從主要功能表中選取 [檢視] > [整合式終端機]，以從 Visual Studio Code 開啟 [整合式終端機]。</span><span class="sxs-lookup"><span data-stu-id="fcaab-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="fcaab-121">在終端機視窗中，輸入 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="fcaab-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="fcaab-122">此命令會在您的資料夾中建立已撰寫簡單 "Hello World" 程式的 `Program.cs` 檔案，以及名為 `HelloWorld.csproj` 的 C# 專案檔。</span><span class="sxs-lookup"><span data-stu-id="fcaab-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![DotNet 新增命令](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="fcaab-124">解析組建資產：</span><span class="sxs-lookup"><span data-stu-id="fcaab-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="fcaab-125">針對 **.NET Core 1.x**，鍵入 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="fcaab-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="fcaab-126">執行 `dotnet restore` 可讓您存取建置專案所需的必要 .NET Core 封裝。</span><span class="sxs-lookup"><span data-stu-id="fcaab-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![DotNet 還原命令](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="fcaab-128">執行 "Hello World" 程式︰</span><span class="sxs-lookup"><span data-stu-id="fcaab-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="fcaab-129">輸入 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="fcaab-129">Type `dotnet run`.</span></span> 

      ![DotNet 執行命令](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="fcaab-131">您也可以觀看簡短的影片教學課程，以取得 [Windows (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) 或 [Linux (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) 上的進一步設定說明。</span><span class="sxs-lookup"><span data-stu-id="fcaab-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="fcaab-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="fcaab-132">Debug</span></span>

1. <span data-ttu-id="fcaab-133">按一下 *Program.cs* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="fcaab-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="fcaab-134">在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](http://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="fcaab-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![開啟 Program.cs 檔案](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="fcaab-136">Visual Studio Code 應該會提示您新增遺失的資產，以建置和偵錯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcaab-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="fcaab-137">選取 [是]。</span><span class="sxs-lookup"><span data-stu-id="fcaab-137">Select **Yes**.</span></span> 

    ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="fcaab-139">若要開啟 [偵錯] 檢視，請按一下左側功能表上的 [偵錯] 圖示。</span><span class="sxs-lookup"><span data-stu-id="fcaab-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![開啟 [偵錯] 索引標籤](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="fcaab-141">尋找窗格頂端的綠色箭頭。</span><span class="sxs-lookup"><span data-stu-id="fcaab-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="fcaab-142">請確定它旁邊的下拉式清單已選取 `.NET Core Launch (console)`。</span><span class="sxs-lookup"><span data-stu-id="fcaab-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![選取 .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="fcaab-144">按一下第 9 行旁邊的「編輯器邊界」(編輯器中行號左側的空白處)，將中斷點新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="fcaab-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9.</span></span>

    ![設定中斷點](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="fcaab-146">若要開始偵錯，請選取 <kbd>F5</kbd> 或綠色箭頭。</span><span class="sxs-lookup"><span data-stu-id="fcaab-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="fcaab-147">當偵錯程式到達您在上一個步驟中設定的中斷點時，它會停止您程式的執行。</span><span class="sxs-lookup"><span data-stu-id="fcaab-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="fcaab-148">進行偵錯時，您可以在左上角窗格中檢視您的本機變數或使用偵錯主控台。</span><span class="sxs-lookup"><span data-stu-id="fcaab-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![執行和偵錯](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="fcaab-150">選取頂端的綠色箭頭以繼續偵錯，或者選取頂端的紅色正方形以停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="fcaab-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="fcaab-151">如需在 Visual Studio Code 中使用 OmniSharp 進行 .NET Core 偵錯的詳細資訊與疑難排解祕訣，請參閱 [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) (設定 .NET Core 偵錯工具的指示)。</span><span class="sxs-lookup"><span data-stu-id="fcaab-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcaab-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcaab-152">See also</span></span>
<span data-ttu-id="fcaab-153">[設定 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="fcaab-153">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="fcaab-154">在 Visual Studio Code 中偵錯 (英文)</span><span class="sxs-lookup"><span data-stu-id="fcaab-154">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
