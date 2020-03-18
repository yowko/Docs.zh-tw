---
title: C# 與 Visual Studio Code 使用者入門
description: 了解如何在 C# 中使用 Visual Studio Code 建立並偵錯您的第一個 .NET Core 應用程式。
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 8eaf1ba2314dcab96db615a8691afed82c5011a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398878"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="f67fb-103">C# 與 Visual Studio Code 使用者入門</span><span class="sxs-lookup"><span data-stu-id="f67fb-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="f67fb-104">.NET Core 提供快速且模組化的平台，可建立在 Windows、Linux 和 macOS 上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f67fb-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="f67fb-105">搭配使用 Visual Studio Code 與 C# 擴充功能，以取得具備 C# IntelliSense (智慧型程式碼完成) 與偵錯完整支援的強大編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="f67fb-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f67fb-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="f67fb-106">Prerequisites</span></span>

1. <span data-ttu-id="f67fb-107">安裝[視覺化工作室代碼](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="f67fb-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="f67fb-108">安裝[.NET 核心 SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="f67fb-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="f67fb-109">安裝適用於 Visual Studio Code 的 [C# 擴充功能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f67fb-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="f67fb-110">如需如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能市集](https://code.visualstudio.com/docs/editor/extension-gallery) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f67fb-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="f67fb-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="f67fb-111">Hello World</span></span>

<span data-ttu-id="f67fb-112">讓我們在 .NET Core 上開始進行簡單的 "Hello World" 程式：</span><span class="sxs-lookup"><span data-stu-id="f67fb-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="f67fb-113">開啟專案：</span><span class="sxs-lookup"><span data-stu-id="f67fb-113">Open a project:</span></span>

    - <span data-ttu-id="f67fb-114">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="f67fb-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="f67fb-115">按一下左側功能表上的 [檔案總管] 圖示，然後按一下 [開啟資料夾]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f67fb-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="f67fb-116">從主功能表中選擇 **"檔** > **打開資料夾**"以打開您希望 C# 專案位於的資料夾，然後按一下"**選擇資料夾**"。</span><span class="sxs-lookup"><span data-stu-id="f67fb-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="f67fb-117">針對本範例，我們將為專案建立一個名為 *HelloWorld* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f67fb-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Visual Studio Code 開啟資料夾](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="f67fb-119">初始化 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="f67fb-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="f67fb-120">通過從主功能表中選擇 **"查看** > **集成終端**"，從視覺化工作室代碼打開集成終端。</span><span class="sxs-lookup"><span data-stu-id="f67fb-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="f67fb-121">在終端機視窗中，輸入 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="f67fb-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="f67fb-122">此命令在資料夾中創建一個*Program.cs*檔，其中已編寫了一個簡單的"Hello World"程式，以及名為*HelloWorld.csproj*的 C# 專案檔案。</span><span class="sxs-lookup"><span data-stu-id="f67fb-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![DotNet 新增命令](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="f67fb-124">解析組建資產：</span><span class="sxs-lookup"><span data-stu-id="f67fb-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="f67fb-125">針對 **.NET Core 1.x**，鍵入 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="f67fb-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="f67fb-126">執行 `dotnet restore` 可讓您存取建置專案所需的必要 .NET Core 封裝。</span><span class="sxs-lookup"><span data-stu-id="f67fb-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![DotNet 還原命令](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="f67fb-128">執行 "Hello World" 程式︰</span><span class="sxs-lookup"><span data-stu-id="f67fb-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="f67fb-129">輸入 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="f67fb-129">Type `dotnet run`.</span></span>

      ![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="f67fb-131">您也可以觀看簡短的影片教學課程，以取得 [Windows (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) 或 [Linux (英文)](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) 上的進一步設定說明。</span><span class="sxs-lookup"><span data-stu-id="f67fb-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="f67fb-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="f67fb-132">Debug</span></span>

1. <span data-ttu-id="f67fb-133">按一下 *Program.cs* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="f67fb-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="f67fb-134">在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="f67fb-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="f67fb-136">Visual Studio Code 應該會提示您新增遺失的資產，以建置和偵錯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f67fb-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="f67fb-137">選取 [是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f67fb-137">Select **Yes**.</span></span>

    ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="f67fb-139">若要開啟 [偵錯] 檢視，請按一下左側功能表上的 [偵錯] 圖示。</span><span class="sxs-lookup"><span data-stu-id="f67fb-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![在 Visual Studio Code 中開啟 [偵錯] 索引標籤](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="f67fb-141">尋找窗格頂端的綠色箭頭。</span><span class="sxs-lookup"><span data-stu-id="f67fb-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="f67fb-142">確保其旁邊的下拉清單已選擇 **.NET 核心啟動（主控台）。**</span><span class="sxs-lookup"><span data-stu-id="f67fb-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![在 Visual Studio Code 中選取 .NET Core](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="f67fb-144">按一下第 9 行旁邊的 [編輯器邊界]\*\*\*\* (編輯器中行號左側空白處)，將中斷點新增至您的專案，或將文字游標移至編輯器中的第 9 行，然後按 <kbd>F9</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="f67fb-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![設定中斷點](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="f67fb-146">要開始調試，請按<kbd>F5</kbd>或選擇綠色箭頭。</span><span class="sxs-lookup"><span data-stu-id="f67fb-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="f67fb-147">當偵錯程式到達您在上一個步驟中設定的中斷點時，它會停止您程式的執行。</span><span class="sxs-lookup"><span data-stu-id="f67fb-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="f67fb-148">進行偵錯時，您可以在左上角窗格中檢視您的本機變數或使用偵錯主控台。</span><span class="sxs-lookup"><span data-stu-id="f67fb-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="f67fb-149">選取頂端的藍色箭頭以繼續偵錯，或選取頂端的紅色正方形以停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="f67fb-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![在 Visual Studio Code 中執行和偵錯](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="f67fb-151">如需在 Visual Studio Code 中使用 OmniSharp 進行 .NET Core 偵錯的詳細資訊與疑難排解祕訣，請參閱 [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) (設定 .NET Core 偵錯工具的指示)。</span><span class="sxs-lookup"><span data-stu-id="f67fb-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="f67fb-152">新增類別</span><span class="sxs-lookup"><span data-stu-id="f67fb-152">Add a class</span></span>

1. <span data-ttu-id="f67fb-153">要添加新類，請按右鍵 VSCode 資源管理器並選擇 **"新檔**"。</span><span class="sxs-lookup"><span data-stu-id="f67fb-153">To add a new class, right click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="f67fb-154">這會在您於 VSCode 中開啟的資料夾內新增檔案。</span><span class="sxs-lookup"><span data-stu-id="f67fb-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="f67fb-155">*MyClass.cs*命名檔。</span><span class="sxs-lookup"><span data-stu-id="f67fb-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="f67fb-156">您必須在結尾加上 `.cs` 副檔名來儲存它，系統才能將它辨識為 csharp 檔案。</span><span class="sxs-lookup"><span data-stu-id="f67fb-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="f67fb-157">新增下方程式碼來建立您的第一個類別。</span><span class="sxs-lookup"><span data-stu-id="f67fb-157">Add the code below to create your first class.</span></span> <span data-ttu-id="f67fb-158">請確保包含正確的命名空間，以便可以從*Program.cs*檔中引用它：</span><span class="sxs-lookup"><span data-stu-id="f67fb-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. <span data-ttu-id="f67fb-159">通過添加以下代碼，在*Program.cs*中從主方法調用新類：</span><span class="sxs-lookup"><span data-stu-id="f67fb-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. <span data-ttu-id="f67fb-160">儲存變更，然後重新執行您的程式。</span><span class="sxs-lookup"><span data-stu-id="f67fb-160">Save your changes and run your program again.</span></span> <span data-ttu-id="f67fb-161">應該會顯示含有所附加字串的新訊息。</span><span class="sxs-lookup"><span data-stu-id="f67fb-161">The new message should appear with the appended string.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="f67fb-162">您會獲得下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="f67fb-162">You get the following output:</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="f67fb-163">常見問題集</span><span class="sxs-lookup"><span data-stu-id="f67fb-163">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="f67fb-164">我缺少在 Visual Studio Code 中建置及偵錯 C# 所需的資產。</span><span class="sxs-lookup"><span data-stu-id="f67fb-164">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="f67fb-165">我的偵錯工具顯示「沒有組態」。</span><span class="sxs-lookup"><span data-stu-id="f67fb-165">My debugger says "No Configuration."</span></span>

<span data-ttu-id="f67fb-166">Visual Studio Code C# 延伸模組可為您產生用於建置和偵錯的資產。</span><span class="sxs-lookup"><span data-stu-id="f67fb-166">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="f67fb-167">Visual Studio Code 會在您第一次開啟 C# 專案時，提示您產生這些資產。</span><span class="sxs-lookup"><span data-stu-id="f67fb-167">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="f67fb-168">如果您當時未產生資產，仍可以透過開啟 [命令選擇區] ([檢視] > [命令選擇區]\*\*\*\*)，然後鍵入 ">.NET: Generate Assets for Build and Debug" 來執行此命令。</span><span class="sxs-lookup"><span data-stu-id="f67fb-168">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="f67fb-169">選擇此選項可生成 *.vscode、\*\*啟動.json*和*任務.json*設定檔。這些設定檔是您所需要的。</span><span class="sxs-lookup"><span data-stu-id="f67fb-169">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="f67fb-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f67fb-170">See also</span></span>

- [<span data-ttu-id="f67fb-171">設定 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f67fb-171">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="f67fb-172">在 Visual Studio Code 中偵錯</span><span class="sxs-lookup"><span data-stu-id="f67fb-172">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
