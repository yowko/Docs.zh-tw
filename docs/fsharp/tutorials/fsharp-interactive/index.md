---
title: F# Interactive (fsi.exe) 參考
description: '了解如何 F # Interactive (fsi.exe) 用來以互動方式在主控台執行 F # 程式碼或執行 F # 指令碼。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36af8d1b-dc08-4a37-9497-d23c0a0ac11c
ms.openlocfilehash: a18f339d898374a59858cd774154b3846594d183
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="db447-104">F# 互動式程式設計</span><span class="sxs-lookup"><span data-stu-id="db447-104">Interactive Programming with F#</span></span> #

> [!NOTE]
<span data-ttu-id="db447-105">本文目前僅描述 Windows 的體驗。</span><span class="sxs-lookup"><span data-stu-id="db447-105">This article currently describes the experience for Windows only.</span></span>  <span data-ttu-id="db447-106">將會加以重新撰寫。</span><span class="sxs-lookup"><span data-stu-id="db447-106">It will be rewritten.</span></span>

> [!NOTE]
<span data-ttu-id="db447-107">API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="db447-107">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="db447-108">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="db447-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="db447-109">F# Interactive (fsi.exe) 在主控台中，以互動方式用於執行 F# 程式碼，或執行 F# 指令碼。</span><span class="sxs-lookup"><span data-stu-id="db447-109">F# Interactive (fsi.exe) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="db447-110">換句話說，F# Interactive 會執行 F# 語言的 REPL (讀取、評估、列印迴圈)。</span><span class="sxs-lookup"><span data-stu-id="db447-110">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="db447-111">若要從主控台執行 F# Interactive，請執行 fsi.exe。</span><span class="sxs-lookup"><span data-stu-id="db447-111">To run F# Interactive from the console, run fsi.exe.</span></span>  <span data-ttu-id="db447-112">您可以獲悉 fsi.exe 在"c:\Program 檔案 (x86) \Microsoft SDKs\F#\<版本 > \Framework\<版本 >\"。</span><span class="sxs-lookup"><span data-stu-id="db447-112">You will find fsi.exe in "c:\Program Files (x86)\Microsoft SDKs\F#\<version>\Framework\<version>\".</span></span> <span data-ttu-id="db447-113">如需可用命令列選項的資訊，請參閱 [F# Interactive 選項](../../language-reference/fsharp-interactive-options.md)。</span><span class="sxs-lookup"><span data-stu-id="db447-113">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="db447-114">若要透過 Visual Studio 執行 F# Interactive，您可以按一下標示為 **F# Interactive** 的合適工具列按鈕，或使用按鍵 **Ctrl+Alt+F**。</span><span class="sxs-lookup"><span data-stu-id="db447-114">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="db447-115">如此會開啟互動式視窗，也就是執行 F# Interactive 工作階段的工具視窗。</span><span class="sxs-lookup"><span data-stu-id="db447-115">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="db447-116">您也可以選取要在互動式視窗中執行的部分程式碼，然後點擊按鍵組合 **ALT+ENTER**。</span><span class="sxs-lookup"><span data-stu-id="db447-116">You can also select some code that you want to run in the interactive window and hit the key combination **ALT+ENTER**.</span></span> <span data-ttu-id="db447-117">F# Interactive 會隨即在標示為 **F# Interactive** 的工具視窗中啟動。</span><span class="sxs-lookup"><span data-stu-id="db447-117">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="db447-118">當您使用這個按鍵組合時，請確定編輯器視窗具有焦點。</span><span class="sxs-lookup"><span data-stu-id="db447-118">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="db447-119">不論是使用主控台還是否 Visual Studio，命令提示字元都會出現，表示解譯器在等待您輸入。</span><span class="sxs-lookup"><span data-stu-id="db447-119">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="db447-120">您可以如同在程式碼檔案中一樣輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="db447-120">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="db447-121">若要編譯並執行程式碼，請輸入兩個分號 (**;;**) 以終止一或數行的輸入。</span><span class="sxs-lookup"><span data-stu-id="db447-121">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="db447-122">F# Interactive 會嘗試編譯程式碼，如果成功的話，它會執行程式碼，並列印它所編譯的類型與值的簽章。</span><span class="sxs-lookup"><span data-stu-id="db447-122">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="db447-123">如果發生錯誤，解譯器就會列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="db447-123">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="db447-124">在同一個工作階段中輸入的程式碼，可以存取先前輸入的所有建構，因此您可以建置程式。</span><span class="sxs-lookup"><span data-stu-id="db447-124">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="db447-125">若有需要，可利用 [工具] 視窗中的延伸緩衝區，視需要將程式碼複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="db447-125">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="db447-126">在 Visual Studio 中執行 F# Interactive 時，會與專案分開執行，因此，舉例來說，除非您將函式的程式碼複製到 [互動] 視窗，否則無法使用在 F# Interactive 中專案內所定義的建構。</span><span class="sxs-lookup"><span data-stu-id="db447-126">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="db447-127">若您開啟了參考某些程式庫的專案，則可以透過方案總管參考 F# Interactive 中的這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="db447-127">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="db447-128">若要參考 F# Interactive 中的程式庫，請展開 [參考] 節點，開啟程式庫的捷徑功能表，然後選擇 [傳送至 F# Interactive]。</span><span class="sxs-lookup"><span data-stu-id="db447-128">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="db447-129">您可以調整設定來控制 F# Interactive 命令列引數 (選項)。</span><span class="sxs-lookup"><span data-stu-id="db447-129">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="db447-130">在 [工具] 功能表上，選取 [選項...]，然後展開 [F# 工具]。</span><span class="sxs-lookup"><span data-stu-id="db447-130">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="db447-131">您只能變更 F# Interactive 選項和 [64 位元 F# Interactive] 這兩項設定，而且只有在 64 位元電腦上執行 F# Interactive 時才相關。</span><span class="sxs-lookup"><span data-stu-id="db447-131">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="db447-132">這項設定會判斷您要執行專用的 64 位元版 fsi.exe 或 fsianycpu.exe，它會使用電腦架構判斷要以 32 位元或 64 位元處理序執行。</span><span class="sxs-lookup"><span data-stu-id="db447-132">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>


## <a name="scripting-with-f"></a><span data-ttu-id="db447-133">F# 指令碼作業</span><span class="sxs-lookup"><span data-stu-id="db447-133">Scripting with F#</span></span> #
<span data-ttu-id="db447-134">指令碼使用副檔名 **.fsx** 或 **.fsscript**。</span><span class="sxs-lookup"><span data-stu-id="db447-134">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="db447-135">您只要執行 **fsi.exe**，並指定 F# 原始程式碼的指令碼檔名，F# Interactive 就會即時讀取程式碼並執行程式碼，而不是編譯原始程式碼，然後稍後再執行已編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="db447-135">Instead of compiling source code and then later running the compiled assembly, you can just run **fsi.exe** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="db447-136">Interactive、指令碼與編譯環境之間的差異</span><span class="sxs-lookup"><span data-stu-id="db447-136">Differences Between the Interactive, Scripting and Compiled Environments</span></span>
<span data-ttu-id="db447-137">當您編譯 F# Interactive 中的程式碼時，無論是以互動方式執行或是執行指令碼，都會定義符號 **INTERACTIVE**。</span><span class="sxs-lookup"><span data-stu-id="db447-137">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="db447-138">當您在編譯器中編譯程式碼時，會定義符號 **COMPILED**。</span><span class="sxs-lookup"><span data-stu-id="db447-138">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="db447-139">因此，如果已編譯模式和互動式模式中的程式碼必須不同，可以使用條件式編譯的前置處理器指示詞，決定要使用哪一種模式。</span><span class="sxs-lookup"><span data-stu-id="db447-139">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="db447-140">當您要在 F# Interactive 中執行在執行編譯器時無法使用的指令碼時，有一些指示詞可用。</span><span class="sxs-lookup"><span data-stu-id="db447-140">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="db447-141">下表摘要說明使用 F# Interactive 時可用的指示詞。</span><span class="sxs-lookup"><span data-stu-id="db447-141">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="db447-142">指示詞</span><span class="sxs-lookup"><span data-stu-id="db447-142">Directive</span></span>|<span data-ttu-id="db447-143">描述</span><span class="sxs-lookup"><span data-stu-id="db447-143">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="db447-144">**#help**</span><span class="sxs-lookup"><span data-stu-id="db447-144">**#help**</span></span>|<span data-ttu-id="db447-145">顯示可用指示詞的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="db447-145">Displays information about available directives.</span></span>|
|<span data-ttu-id="db447-146">**#I**</span><span class="sxs-lookup"><span data-stu-id="db447-146">**#I**</span></span>|<span data-ttu-id="db447-147">指定加上引號的組件搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="db447-147">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="db447-148">**#load**</span><span class="sxs-lookup"><span data-stu-id="db447-148">**#load**</span></span>|<span data-ttu-id="db447-149">讀取原始程式檔、進行編譯，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="db447-149">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="db447-150">**#quit**</span><span class="sxs-lookup"><span data-stu-id="db447-150">**#quit**</span></span>|<span data-ttu-id="db447-151">終止 F# Interactive 工作階段。</span><span class="sxs-lookup"><span data-stu-id="db447-151">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="db447-152">**#r**</span><span class="sxs-lookup"><span data-stu-id="db447-152">**#r**</span></span>|<span data-ttu-id="db447-153">參考組件。</span><span class="sxs-lookup"><span data-stu-id="db447-153">References an assembly.</span></span>|
|<span data-ttu-id="db447-154">**#time ["on"&#124;"off"]**</span><span class="sxs-lookup"><span data-stu-id="db447-154">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="db447-155">**#time** 會自行切換是否顯示效能資訊。</span><span class="sxs-lookup"><span data-stu-id="db447-155">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="db447-156">當它啟用時，F# Interactive 會測量所解譯及執行的每個程式碼區段之即時、CPU 時間及記憶體回收資訊。</span><span class="sxs-lookup"><span data-stu-id="db447-156">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="db447-157">當您在 F# Interactive 中指定檔案或路徑時，應該要有一個字串常值。</span><span class="sxs-lookup"><span data-stu-id="db447-157">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="db447-158">因此，檔案和路徑必須以引號括住，並遵循一般的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="db447-158">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="db447-159">此外，您可以使用 @ 字元，讓 F# Interactive 能將包含路徑的字串，解譯為逐字字串。</span><span class="sxs-lookup"><span data-stu-id="db447-159">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="db447-160">這會導致 F# Interactive 會忽略所有逸出字元。</span><span class="sxs-lookup"><span data-stu-id="db447-160">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="db447-161">已編譯模式和互動式模式之間，其中一項差異是存取命令列引數的方式。</span><span class="sxs-lookup"><span data-stu-id="db447-161">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="db447-162">在編譯模式中是使用 **System.Environment.GetCommandLineArgs**。</span><span class="sxs-lookup"><span data-stu-id="db447-162">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="db447-163">而在指令碼中則是使用 **fsi.CommandLineArgs**。</span><span class="sxs-lookup"><span data-stu-id="db447-163">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="db447-164">下列程式碼說明如何建立可讀取指令碼中命令列引數的函式，同時也會示範如何從指令碼參考另一個組件。</span><span class="sxs-lookup"><span data-stu-id="db447-164">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="db447-165">第一個程式碼檔案 **MyAssembly.fs** 是要參考之組件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db447-165">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="db447-166">請使用命令列 **fsc -a MyAssembly.fs** 編譯這個檔案，然後使用下列命令列以指令碼形式執行第二個檔案：**fsi --exec file1.fsx** test</span><span class="sxs-lookup"><span data-stu-id="db447-166">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

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

<span data-ttu-id="db447-167">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="db447-167">The output is as follows:</span></span>

```
Command line arguments: 
file1.fsx
test
60
```

## <a name="related-topics"></a><span data-ttu-id="db447-168">相關主題</span><span class="sxs-lookup"><span data-stu-id="db447-168">Related Topics</span></span>

|<span data-ttu-id="db447-169">標題</span><span class="sxs-lookup"><span data-stu-id="db447-169">Title</span></span>|<span data-ttu-id="db447-170">描述</span><span class="sxs-lookup"><span data-stu-id="db447-170">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="db447-171">F# Interactive 選項</span><span class="sxs-lookup"><span data-stu-id="db447-171">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="db447-172">描述命令列語法和選項 F # Interactive fsi.exe。</span><span class="sxs-lookup"><span data-stu-id="db447-172">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
|[<span data-ttu-id="db447-173">F# Interactive 程式庫參考</span><span class="sxs-lookup"><span data-stu-id="db447-173">F# Interactive Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|<span data-ttu-id="db447-174">說明在 F# Interactive 中執行程式碼時，所提供的程式庫功能。</span><span class="sxs-lookup"><span data-stu-id="db447-174">Describes library functionality available when executing code in F# interactive.</span></span>|
