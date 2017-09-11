---
title: "C# 與 Visual Studio Code 使用者入門 - C# 指南 | Microsoft Docs"
description: "了解如何在 C# 中使用 Visual Studio Code 建立並偵錯您的第一個 .NET Core 應用程式。"
keywords: "C#, 使用者入門, 取得, 安裝, Visual Studio Code, 跨平台"
author: kendrahavens
ms.author: mairaw
ms.date: 8/01/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.translationtype: HT
ms.sourcegitcommit: 3bd8800e7410ae4a3b89f5962af957789edd48b0
ms.openlocfilehash: a10fda5663f0a49069388ee8ee7a9ebb575cd549
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---

# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="ed09c-104">C# 與 Visual Studio Code 使用者入門</span><span class="sxs-lookup"><span data-stu-id="ed09c-104">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="ed09c-105">.NET Core 提供快速且模組化的平台，可建立在 Windows、Linux 和 macOS 上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed09c-105">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="ed09c-106">搭配使用 Visual Studio Code 與 C# 擴充功能，以取得具備 C# IntelliSense (智慧型程式碼完成) 與偵錯完整支援的強大編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="ed09c-106">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ed09c-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="ed09c-107">Prerequisites</span></span>

1. <span data-ttu-id="ed09c-108">安裝 [Visual Studio Code (英文)](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="ed09c-108">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="ed09c-109">安裝 [.NET Core SDK (英文)](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="ed09c-109">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="ed09c-110">從 Visual Studio Code Marketplace 安裝 [C# 擴充功能 (英文)](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)。</span><span class="sxs-lookup"><span data-stu-id="ed09c-110">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) from the Visual Studio Code Marketplace.</span></span>

## <a name="hello-world"></a><span data-ttu-id="ed09c-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="ed09c-111">Hello World</span></span>

<span data-ttu-id="ed09c-112">讓我們在 .NET Core 上開始進行簡單的 "Hello World" 程式：</span><span class="sxs-lookup"><span data-stu-id="ed09c-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="ed09c-113">開啟專案：</span><span class="sxs-lookup"><span data-stu-id="ed09c-113">Open a project:</span></span>

    * <span data-ttu-id="ed09c-114">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="ed09c-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="ed09c-115">按一下左側功能表上的 [檔案總管] 圖示，然後按一下 [開啟資料夾]。</span><span class="sxs-lookup"><span data-stu-id="ed09c-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="ed09c-116">選取您想要放置 C# 專案的資料夾，然後按一下 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="ed09c-116">Select the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="ed09c-117">針對本範例，我們將為專案建立一個名為 'HelloWorld' 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed09c-117">For our example, we'll create a folder for our project named 'HelloWorld'.</span></span> 

  ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

    * <span data-ttu-id="ed09c-119">或者，您可以從主功能表選取 [檔案]  >  [開啟資料夾]，來開啟您的專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed09c-119">Alternatively, you can select **File** > **Open Folder** from the main menu to open your project folder.</span></span>

2. <span data-ttu-id="ed09c-120">初始化 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="ed09c-120">Initialize a C# project:</span></span>
    * <span data-ttu-id="ed09c-121">鍵入 <kbd>CTRL</kbd>+<kbd>\\`</kbd> (倒引號) 從 Visual Studio Code 開啟整合式終端機。</span><span class="sxs-lookup"><span data-stu-id="ed09c-121">Open the Integrated Terminal from Visual Studio Code by typing <kbd>CTRL</kbd>+<kbd>\\`</kbd> (backtick).</span></span> <span data-ttu-id="ed09c-122">另外，您也可以選取主功能表中的 [檢視] > [整合式終端機]。</span><span class="sxs-lookup"><span data-stu-id="ed09c-122">Alternatively, you can select **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="ed09c-123">在終端機視窗中，輸入 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="ed09c-123">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="ed09c-124">這會在您的資料夾中建立已撰寫簡單 "Hello World" 程式的 `Program.cs` 檔案，以及名稱為 `HelloWorld.csproj` 的 C# 專案檔。</span><span class="sxs-lookup"><span data-stu-id="ed09c-124">This creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

  ![DotNet 新增命令](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="ed09c-126">解析組建資產：</span><span class="sxs-lookup"><span data-stu-id="ed09c-126">Resolve the build assets:</span></span>

    * <span data-ttu-id="ed09c-127">針對 **.NET Core 1.1**，輸入 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="ed09c-127">For **.NET Core 1.1**, type `dotnet restore`.</span></span> <span data-ttu-id="ed09c-128">執行 `dotnet restore` 可讓您存取建置專案所需的必要 .NET Core 封裝。</span><span class="sxs-lookup"><span data-stu-id="ed09c-128">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

   ![DotNet 還原命令](media/with-visual-studio-code/dotnetrestore.png)

    * <span data-ttu-id="ed09c-130">針對 **.NET Core 2.0**，此為選擇性步驟。</span><span class="sxs-lookup"><span data-stu-id="ed09c-130">For **.NET Core 2.0**, this step is optional.</span></span> <span data-ttu-id="ed09c-131">當新專案建立時，`dotnet restore` 命令會自動執行。</span><span class="sxs-lookup"><span data-stu-id="ed09c-131">The `dotnet restore` command executes automatically when a new project is created.</span></span>

4. <span data-ttu-id="ed09c-132">執行 "Hello World" 程式︰</span><span class="sxs-lookup"><span data-stu-id="ed09c-132">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="ed09c-133">輸入 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="ed09c-133">Type `dotnet run`.</span></span> 

  ![DotNet 執行命令](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="ed09c-135">您也可以觀看簡短的影片教學課程，以取得 [Windows (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) 或 [Linux (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) 上的進一步設定說明。</span><span class="sxs-lookup"><span data-stu-id="ed09c-135">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="ed09c-136">偵錯</span><span class="sxs-lookup"><span data-stu-id="ed09c-136">Debug</span></span>
1. <span data-ttu-id="ed09c-137">按一下 *Program.cs* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="ed09c-137">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="ed09c-138">在 Visual Studio Code 中首次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](http://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="ed09c-138">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) will load in the editor.</span></span>

  ![開啟 Program.cs 檔案](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="ed09c-140">Visual Studio Code 會提示您新增遺失的資產，以建置及偵錯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed09c-140">Visual Studio Code will prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="ed09c-141">選取 [是]。</span><span class="sxs-lookup"><span data-stu-id="ed09c-141">Select **Yes**.</span></span> 

  ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="ed09c-143">若要開啟 [偵錯] 檢視，請按一下左側功能表上的 [偵錯] 圖示。</span><span class="sxs-lookup"><span data-stu-id="ed09c-143">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

  ![開啟 [偵錯] 索引標籤](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="ed09c-145">尋找窗格頂端的綠色箭頭。</span><span class="sxs-lookup"><span data-stu-id="ed09c-145">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="ed09c-146">請確定它旁邊的下拉式清單已選取 `.NET Core Launch (console)`。</span><span class="sxs-lookup"><span data-stu-id="ed09c-146">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

  ![選取 .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="ed09c-148">按一下第 9 行旁邊的「編輯器邊界」(編輯器中行號左側的空白處)，將中斷點新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ed09c-148">Add a breakpoint to your project by clicking on the **editor margin** (the space on the left of the line numbers in the editor) next to line 9.</span></span>

  ![設定中斷點](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="ed09c-150">選取 <kbd>F5</kbd> 或綠色箭頭來開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="ed09c-150">Select <kbd>F5</kbd> or the green arrow to start debugging.</span></span> <span data-ttu-id="ed09c-151">當偵錯程式到達您在上一個步驟中設定的中斷點時，它會停止您程式的執行。</span><span class="sxs-lookup"><span data-stu-id="ed09c-151">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="ed09c-152">進行偵錯時，您可以在左上角窗格中，或使用偵錯主控台來檢視您的本機變數。</span><span class="sxs-lookup"><span data-stu-id="ed09c-152">While debugging you can view your local variables in the top left pane or use the debug console.</span></span>

  ![執行和偵錯](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="ed09c-154">選取頂端的綠色箭頭以繼續偵錯，或者選取頂端的紅色正方形以停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="ed09c-154">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="ed09c-155">如需在 Visual Studio Code 中使用 OmniSharp 進行 .NET Core 偵錯的詳細資訊與疑難排解祕訣，請參閱 [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) (設定 .NET Core 偵錯工具的指示)。</span><span class="sxs-lookup"><span data-stu-id="ed09c-155">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed09c-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed09c-156">See also</span></span>
<span data-ttu-id="ed09c-157">[設定 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="ed09c-157">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="ed09c-158">在 Visual Studio Code 中偵錯 (英文)</span><span class="sxs-lookup"><span data-stu-id="ed09c-158">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)

