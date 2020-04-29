---
title: C# 與 Visual Studio Code 使用者入門
description: 了解如何在 C# 中使用 Visual Studio Code 建立並偵錯您的第一個 .NET Core 應用程式。
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506874"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="42b2e-103">C# 與 Visual Studio Code 使用者入門</span><span class="sxs-lookup"><span data-stu-id="42b2e-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="42b2e-104">.NET Core 提供快速且模組化的平台，可建立在 Windows、Linux 和 macOS 上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="42b2e-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="42b2e-105">搭配使用 Visual Studio Code 與 C# 擴充功能，以取得具備 C# IntelliSense (智慧型程式碼完成) 與偵錯完整支援的強大編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="42b2e-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="42b2e-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="42b2e-106">Prerequisites</span></span>

1. <span data-ttu-id="42b2e-107">安裝 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="42b2e-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="42b2e-108">安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="42b2e-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="42b2e-109">安裝適用於 Visual Studio Code 的 [C# 擴充功能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="42b2e-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="42b2e-110">如需如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能市集](https://code.visualstudio.com/docs/editor/extension-gallery) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="42b2e-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="42b2e-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="42b2e-111">Hello World</span></span>

<span data-ttu-id="42b2e-112">開始使用 .NET Core 上的簡單 "Hello World" 程式：</span><span class="sxs-lookup"><span data-stu-id="42b2e-112">Get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="42b2e-113">開啟專案：</span><span class="sxs-lookup"><span data-stu-id="42b2e-113">Open a project:</span></span>

    - <span data-ttu-id="42b2e-114">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="42b2e-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="42b2e-115">從主**功能表選取 [** 檔案] [**開啟資料夾**]。 > </span><span class="sxs-lookup"><span data-stu-id="42b2e-115">Select **File** > **Open Folder** from the main menu.</span></span>
    - <span data-ttu-id="42b2e-116">建立名為*HelloWorld*的資料夾，然後按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="42b2e-116">Create a folder named *HelloWorld*, and click **Select Folder**.</span></span> <span data-ttu-id="42b2e-117">資料夾名稱預設會成為專案名稱和命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="42b2e-117">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="42b2e-118">您稍後會在本教學課程中新增程式碼，假設專案`HelloWorld`命名空間為。</span><span class="sxs-lookup"><span data-stu-id="42b2e-118">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="42b2e-119">初始化 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="42b2e-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="42b2e-120">從主功能表選取 [**查看** > **終端**機]，從 Visual Studio Code 開啟終端機。</span><span class="sxs-lookup"><span data-stu-id="42b2e-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="42b2e-121">在終端機視窗中， `dotnet new console`輸入。</span><span class="sxs-lookup"><span data-stu-id="42b2e-121">In the terminal window, enter `dotnet new console`.</span></span>

      <span data-ttu-id="42b2e-122">此命令會在您的資料夾中建立*Program.cs*檔案，其中已撰寫簡單的 "Hello World" 程式，以及名為*HelloWorld*的 c # 專案檔。</span><span class="sxs-lookup"><span data-stu-id="42b2e-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![DotNet 新增命令](media/with-visual-studio-code/dotnet-new-command.png)

1. <span data-ttu-id="42b2e-124">執行 "Hello World" 程式︰</span><span class="sxs-lookup"><span data-stu-id="42b2e-124">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="42b2e-125">在終端機視窗中， `dotnet run`輸入。</span><span class="sxs-lookup"><span data-stu-id="42b2e-125">In the terminal window, enter `dotnet run`.</span></span>

      ![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a><span data-ttu-id="42b2e-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="42b2e-127">Debug</span></span>

1. <span data-ttu-id="42b2e-128">按一下 *Program.cs* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="42b2e-128">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="42b2e-129">在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="42b2e-129">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="42b2e-131">Visual Studio Code 會提示您新增遺失的資產，以建立及偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="42b2e-131">Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="42b2e-132">選取 [是]  。</span><span class="sxs-lookup"><span data-stu-id="42b2e-132">Select **Yes**.</span></span>

    ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="42b2e-134">若要開啟 [偵錯] 檢視，請按一下左側功能表上的 [偵錯] 圖示。</span><span class="sxs-lookup"><span data-stu-id="42b2e-134">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![在 Visual Studio Code 中開啟 [偵錯] 索引標籤](media/with-visual-studio-code/open-debug-tab.png)

1. <span data-ttu-id="42b2e-136">尋找窗格頂端的綠色箭頭。</span><span class="sxs-lookup"><span data-stu-id="42b2e-136">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="42b2e-137">請確定其旁邊的下拉式選已選取 [ **.Net Core 啟動] （主控台）** 。</span><span class="sxs-lookup"><span data-stu-id="42b2e-137">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![在 Visual Studio Code 中選取 .NET Core](media/with-visual-studio-code/select-net-core.png)

1. <span data-ttu-id="42b2e-139">按一下第 9 行旁邊的 [編輯器邊界]\*\*\*\* (編輯器中行號左側空白處)，將中斷點新增至您的專案，或將文字游標移至編輯器中的第 9 行，然後按 <kbd>F9</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="42b2e-139">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![設定中斷點](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. <span data-ttu-id="42b2e-141">若要開始進行調試，請按<kbd>F5</kbd>或選取綠色箭號。</span><span class="sxs-lookup"><span data-stu-id="42b2e-141">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="42b2e-142">當偵錯程式到達您在上一個步驟中設定的中斷點時，它會停止您程式的執行。</span><span class="sxs-lookup"><span data-stu-id="42b2e-142">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="42b2e-143">在偵錯工具中，您可以在左上方窗格中，或使用 debug 主控台來查看您的本機變數。</span><span class="sxs-lookup"><span data-stu-id="42b2e-143">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

1. <span data-ttu-id="42b2e-144">選取頂端的藍色箭頭以繼續偵錯，或選取頂端的紅色正方形以停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="42b2e-144">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![在 Visual Studio Code 中執行和偵錯](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="42b2e-146">如需在 Visual Studio Code 中使用 OmniSharp 進行 .NET Core 偵錯的詳細資訊與疑難排解祕訣，請參閱 [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md) (設定 .NET Core 偵錯工具的指示)。</span><span class="sxs-lookup"><span data-stu-id="42b2e-146">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="42b2e-147">新增類別</span><span class="sxs-lookup"><span data-stu-id="42b2e-147">Add a class</span></span>

1. <span data-ttu-id="42b2e-148">若要加入新的類別，請以滑鼠右鍵按一下*Program.cs*下方的 VSCode Explorer，然後選取 [**新增**檔案]。</span><span class="sxs-lookup"><span data-stu-id="42b2e-148">To add a new class, right-click in the VSCode Explorer below *Program.cs* and select **New File**.</span></span> <span data-ttu-id="42b2e-149">這會在您於 VSCode 中開啟的資料夾內新增檔案。</span><span class="sxs-lookup"><span data-stu-id="42b2e-149">This adds a new file to the folder you have open in VSCode.</span></span>
1. <span data-ttu-id="42b2e-150">將檔案命名為*MyClass.cs*。</span><span class="sxs-lookup"><span data-stu-id="42b2e-150">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="42b2e-151">您必須在結尾加上 `.cs` 副檔名來儲存它，系統才能將它辨識為 csharp 檔案。</span><span class="sxs-lookup"><span data-stu-id="42b2e-151">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
1. <span data-ttu-id="42b2e-152">新增下列程式碼，以建立您的第一個類別。</span><span class="sxs-lookup"><span data-stu-id="42b2e-152">Add the following code to create your first class.</span></span>

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

1. <span data-ttu-id="42b2e-153">將 Program.cs 中的程式碼`Main`取代為下列程式碼， *Program.cs*以從您的方法呼叫新的類別：</span><span class="sxs-lookup"><span data-stu-id="42b2e-153">Call your new class from your `Main` method by replacing the code in *Program.cs* with the following code:</span></span>

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

1. <span data-ttu-id="42b2e-154">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="42b2e-154">Save your changes.</span></span>

1. <span data-ttu-id="42b2e-155">再次執行程式。</span><span class="sxs-lookup"><span data-stu-id="42b2e-155">Run the program again.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="42b2e-156">新訊息隨即出現，並附上附加的字串。</span><span class="sxs-lookup"><span data-stu-id="42b2e-156">The new message appears with the appended string.</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="42b2e-157">常見問題集</span><span class="sxs-lookup"><span data-stu-id="42b2e-157">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="42b2e-158">我缺少在 Visual Studio Code 中建置及偵錯 C# 所需的資產。</span><span class="sxs-lookup"><span data-stu-id="42b2e-158">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="42b2e-159">我的偵錯工具顯示「沒有組態」。</span><span class="sxs-lookup"><span data-stu-id="42b2e-159">My debugger says "No Configuration."</span></span>

<span data-ttu-id="42b2e-160">Visual Studio Code C# 延伸模組可為您產生用於建置和偵錯的資產。</span><span class="sxs-lookup"><span data-stu-id="42b2e-160">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="42b2e-161">Visual Studio Code 會在您第一次開啟 C# 專案時，提示您產生這些資產。</span><span class="sxs-lookup"><span data-stu-id="42b2e-161">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="42b2e-162">如果您當時未產生資產，仍可以透過開啟 [命令選擇區] ([檢視] > [命令選擇區]\*\*\*\*)，然後鍵入 ">.NET: Generate Assets for Build and Debug" 來執行此命令。</span><span class="sxs-lookup"><span data-stu-id="42b2e-162">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="42b2e-163">選取此程式會產生*vscode*、*啟動 json*和您需要的*json*設定檔案。</span><span class="sxs-lookup"><span data-stu-id="42b2e-163">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="42b2e-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="42b2e-164">See also</span></span>

- [<span data-ttu-id="42b2e-165">設定 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="42b2e-165">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="42b2e-166">在 Visual Studio Code 中偵錯</span><span class="sxs-lookup"><span data-stu-id="42b2e-166">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
