---
title: F# Interactive (fsi.exe) 參考
description: '瞭解 F # Interactive ( # A0) 如何用來在主控台以互動方式執行 F # 程式碼，或執行 F # 腳本。'
ms.date: 05/16/2016
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 8bb1563ad34e65101fb9f09d6e347278e4b0de78
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854941"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="b1528-103">使用 F 進行互動式程式設計\#</span><span class="sxs-lookup"><span data-stu-id="b1528-103">Interactive programming with F\#</span></span>

> [!NOTE]
> <span data-ttu-id="b1528-104">本文目前僅描述 Windows 的體驗。</span><span class="sxs-lookup"><span data-stu-id="b1528-104">This article currently describes the experience for Windows only.</span></span>

<span data-ttu-id="b1528-105">F# Interactive (fsi.exe) 在主控台中，以互動方式用於執行 F# 程式碼，或執行 F# 指令碼。</span><span class="sxs-lookup"><span data-stu-id="b1528-105">F# Interactive (fsi.exe) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="b1528-106">換句話說，F# Interactive 會執行 F# 語言的 REPL (讀取、評估、列印迴圈)。</span><span class="sxs-lookup"><span data-stu-id="b1528-106">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="b1528-107">若要從主控台執行 F# Interactive，請執行 fsi.exe。</span><span class="sxs-lookup"><span data-stu-id="b1528-107">To run F# Interactive from the console, run fsi.exe.</span></span> <span data-ttu-id="b1528-108">您會在中找到 fsi.exe：</span><span class="sxs-lookup"><span data-stu-id="b1528-108">You will find fsi.exe in:</span></span>

```console
C:\Program Files (x86)\Microsoft Visual Studio\2019\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

<span data-ttu-id="b1528-109">其中 `sku` 可以是 `Community` 、 `Professional` 或 `Enterprise` 。</span><span class="sxs-lookup"><span data-stu-id="b1528-109">where `sku` is either `Community`, `Professional`, or `Enterprise`.</span></span>

<span data-ttu-id="b1528-110">如需可用命令列選項的資訊，請參閱 [F# Interactive 選項](../../language-reference/fsharp-interactive-options.md)。</span><span class="sxs-lookup"><span data-stu-id="b1528-110">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="b1528-111">若要透過 Visual Studio 執行 F# Interactive，您可以按一下標示為 **F# Interactive** 的合適工具列按鈕，或使用按鍵 **Ctrl+Alt+F**。</span><span class="sxs-lookup"><span data-stu-id="b1528-111">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="b1528-112">如此會開啟互動式視窗，也就是執行 F# Interactive 工作階段的工具視窗。</span><span class="sxs-lookup"><span data-stu-id="b1528-112">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="b1528-113">您也可以在互動式視窗中選取您想要執行的一些程式碼，然後按按鍵組合**Alt + Enter**。</span><span class="sxs-lookup"><span data-stu-id="b1528-113">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="b1528-114">F# Interactive 會隨即在標示為 **F# Interactive** 的工具視窗中啟動。</span><span class="sxs-lookup"><span data-stu-id="b1528-114">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="b1528-115">當您使用這個按鍵組合時，請確定編輯器視窗具有焦點。</span><span class="sxs-lookup"><span data-stu-id="b1528-115">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="b1528-116">不論是使用主控台還是否 Visual Studio，命令提示字元都會出現，表示解譯器在等待您輸入。</span><span class="sxs-lookup"><span data-stu-id="b1528-116">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="b1528-117">您可以如同在程式碼檔案中一樣輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1528-117">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="b1528-118">若要編譯並執行程式碼，請輸入兩個分號 (**;;**) 以終止一或數行的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1528-118">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="b1528-119">F# Interactive 會嘗試編譯程式碼，如果成功的話，它會執行程式碼，並列印它所編譯的類型與值的簽章。</span><span class="sxs-lookup"><span data-stu-id="b1528-119">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="b1528-120">如果發生錯誤，解譯器就會列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="b1528-120">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="b1528-121">在同一個工作階段中輸入的程式碼，可以存取先前輸入的所有建構，因此您可以建置程式。</span><span class="sxs-lookup"><span data-stu-id="b1528-121">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="b1528-122">若有需要，可利用 [工具] 視窗中的延伸緩衝區，視需要將程式碼複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="b1528-122">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="b1528-123">在 Visual Studio 中執行 F# Interactive 時，會與專案分開執行，因此，舉例來說，除非您將函式的程式碼複製到 [互動] 視窗，否則無法使用在 F# Interactive 中專案內所定義的建構。</span><span class="sxs-lookup"><span data-stu-id="b1528-123">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="b1528-124">若您開啟了參考某些程式庫的專案，則可以透過方案總管\*\*\*\* 參考 F# Interactive 中的這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="b1528-124">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="b1528-125">若要參考 F# Interactive 中的程式庫，請展開 [參考] \*\*\*\* 節點，開啟程式庫的捷徑功能表，然後選擇 [傳送至 F# Interactive]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1528-125">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="b1528-126">您可以調整設定來控制 F# Interactive 命令列引數 (選項)。</span><span class="sxs-lookup"><span data-stu-id="b1528-126">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="b1528-127">在 [工具]\*\*\*\* 功能表上，選取 [選項...]\*\*\*\*，然後展開 [F# 工具]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1528-127">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="b1528-128">您只能變更 F# Interactive 選項和 [64 位元 F# Interactive] \*\*\*\* 這兩項設定，而且只有在 64 位元電腦上執行 F# Interactive 時才相關。</span><span class="sxs-lookup"><span data-stu-id="b1528-128">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="b1528-129">這項設定會判斷您要執行專用的 64 位元版 fsi.exe 或 fsianycpu.exe，它會使用電腦架構判斷要以 32 位元或 64 位元處理序執行。</span><span class="sxs-lookup"><span data-stu-id="b1528-129">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="b1528-130">使用 F 撰寫腳本\#</span><span class="sxs-lookup"><span data-stu-id="b1528-130">Scripting with F\#</span></span>

<span data-ttu-id="b1528-131">指令碼使用副檔名 **.fsx** 或 **.fsscript**。</span><span class="sxs-lookup"><span data-stu-id="b1528-131">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="b1528-132">您只要執行 **fsi.exe**，並指定 F# 原始程式碼的指令碼檔名，F# Interactive 就會即時讀取程式碼並執行程式碼，而不是編譯原始程式碼，然後稍後再執行已編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="b1528-132">Instead of compiling source code and then later running the compiled assembly, you can just run **fsi.exe** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="b1528-133">互動式、腳本和編譯環境之間的差異</span><span class="sxs-lookup"><span data-stu-id="b1528-133">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="b1528-134">當您編譯 F# Interactive 中的程式碼時，無論是以互動方式執行或是執行指令碼，都會定義符號 **INTERACTIVE**。</span><span class="sxs-lookup"><span data-stu-id="b1528-134">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="b1528-135">當您在編譯器中編譯程式碼時，會定義符號 **COMPILED**。</span><span class="sxs-lookup"><span data-stu-id="b1528-135">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="b1528-136">因此，如果已編譯模式和互動式模式中的程式碼必須不同，可以使用條件式編譯的前置處理器指示詞，決定要使用哪一種模式。</span><span class="sxs-lookup"><span data-stu-id="b1528-136">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="b1528-137">當您要在 F# Interactive 中執行在執行編譯器時無法使用的指令碼時，有一些指示詞可用。</span><span class="sxs-lookup"><span data-stu-id="b1528-137">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="b1528-138">下表摘要說明使用 F# Interactive 時可用的指示詞。</span><span class="sxs-lookup"><span data-stu-id="b1528-138">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="b1528-139">指示詞</span><span class="sxs-lookup"><span data-stu-id="b1528-139">Directive</span></span>|<span data-ttu-id="b1528-140">描述</span><span class="sxs-lookup"><span data-stu-id="b1528-140">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="b1528-141">**#help**</span><span class="sxs-lookup"><span data-stu-id="b1528-141">**#help**</span></span>|<span data-ttu-id="b1528-142">顯示可用指示詞的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b1528-142">Displays information about available directives.</span></span>|
|<span data-ttu-id="b1528-143">**#I**</span><span class="sxs-lookup"><span data-stu-id="b1528-143">**#I**</span></span>|<span data-ttu-id="b1528-144">指定加上引號的組件搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="b1528-144">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="b1528-145">**#load**</span><span class="sxs-lookup"><span data-stu-id="b1528-145">**#load**</span></span>|<span data-ttu-id="b1528-146">讀取原始程式檔、進行編譯，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="b1528-146">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="b1528-147">**#quit**</span><span class="sxs-lookup"><span data-stu-id="b1528-147">**#quit**</span></span>|<span data-ttu-id="b1528-148">終止 F# Interactive 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b1528-148">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="b1528-149">**#r**</span><span class="sxs-lookup"><span data-stu-id="b1528-149">**#r**</span></span>|<span data-ttu-id="b1528-150">參考組件。</span><span class="sxs-lookup"><span data-stu-id="b1528-150">References an assembly.</span></span>|
|<span data-ttu-id="b1528-151">**#time ["on"&#124;"off"]**</span><span class="sxs-lookup"><span data-stu-id="b1528-151">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="b1528-152">**#time** 會自行切換是否顯示效能資訊。</span><span class="sxs-lookup"><span data-stu-id="b1528-152">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="b1528-153">當它啟用時，F# Interactive 會測量所解譯及執行的每個程式碼區段之即時、CPU 時間及記憶體回收資訊。</span><span class="sxs-lookup"><span data-stu-id="b1528-153">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="b1528-154">當您在 F# Interactive 中指定檔案或路徑時，應該要有一個字串常值。</span><span class="sxs-lookup"><span data-stu-id="b1528-154">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="b1528-155">因此，檔案和路徑必須以引號括住，並遵循一般的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="b1528-155">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="b1528-156">此外，您可以使用 @ 字元，讓 F# Interactive 能將包含路徑的字串，解譯為逐字字串。</span><span class="sxs-lookup"><span data-stu-id="b1528-156">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="b1528-157">這會導致 F# Interactive 會忽略所有逸出字元。</span><span class="sxs-lookup"><span data-stu-id="b1528-157">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="b1528-158">已編譯模式和互動式模式之間，其中一項差異是存取命令列引數的方式。</span><span class="sxs-lookup"><span data-stu-id="b1528-158">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="b1528-159">在編譯模式中是使用 **System.Environment.GetCommandLineArgs**。</span><span class="sxs-lookup"><span data-stu-id="b1528-159">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="b1528-160">而在指令碼中則是使用 **fsi.CommandLineArgs**。</span><span class="sxs-lookup"><span data-stu-id="b1528-160">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="b1528-161">下列程式碼說明如何建立可讀取指令碼中命令列引數的函式，同時也會示範如何從指令碼參考另一個組件。</span><span class="sxs-lookup"><span data-stu-id="b1528-161">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="b1528-162">第一個程式碼檔案 **MyAssembly.fs** 是要參考之組件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1528-162">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="b1528-163">請使用命令列 **fsc -a MyAssembly.fs** 編譯這個檔案，然後使用下列命令列以指令碼形式執行第二個檔案：**fsi --exec file1.fsx** test</span><span class="sxs-lookup"><span data-stu-id="b1528-163">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="b1528-164">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="b1528-164">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="related-articles"></a><span data-ttu-id="b1528-165">相關文章</span><span class="sxs-lookup"><span data-stu-id="b1528-165">Related articles</span></span>

|<span data-ttu-id="b1528-166">Title</span><span class="sxs-lookup"><span data-stu-id="b1528-166">Title</span></span>|<span data-ttu-id="b1528-167">描述</span><span class="sxs-lookup"><span data-stu-id="b1528-167">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="b1528-168">F# Interactive 選項</span><span class="sxs-lookup"><span data-stu-id="b1528-168">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="b1528-169">描述 F # Interactive、fsi.exe 的命令列語法和選項。</span><span class="sxs-lookup"><span data-stu-id="b1528-169">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
|[<span data-ttu-id="b1528-170">F# Interactive 程式庫參考</span><span class="sxs-lookup"><span data-stu-id="b1528-170">F# Interactive Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|<span data-ttu-id="b1528-171">說明在 F# Interactive 中執行程式碼時，所提供的程式庫功能。</span><span class="sxs-lookup"><span data-stu-id="b1528-171">Describes library functionality available when executing code in F# interactive.</span></span>|
