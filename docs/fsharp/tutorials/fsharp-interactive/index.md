---
title: F# 互動 (dotnet) 參考
description: '瞭解如何使用 F# 互動 (dotnet fsi) ，以互動方式在主控台執行 F # 程式碼，或執行 F # 腳本。'
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: b1020d8ab8f2282c792fb5d00656b6d43c2c6610
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064115"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="e83e6-103">使用 F 的互動式程式設計\#</span><span class="sxs-lookup"><span data-stu-id="e83e6-103">Interactive programming with F\#</span></span>

<span data-ttu-id="e83e6-104">F# 互動 (dotnet fsi) 用來以互動方式在主控台執行 F # 程式碼，或執行 F # 腳本。</span><span class="sxs-lookup"><span data-stu-id="e83e6-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="e83e6-105">換句話說，F# Interactive 會執行 F# 語言的 REPL (讀取、評估、列印迴圈)。</span><span class="sxs-lookup"><span data-stu-id="e83e6-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="e83e6-106">若要從主控台執行 F# 互動，請執行 `dotnet fsi` 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="e83e6-107">您將可以 `dotnet fsi` 在任何 .NET SDK 中找到。</span><span class="sxs-lookup"><span data-stu-id="e83e6-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="e83e6-108">如需可用命令列選項的資訊，請參閱 [F# Interactive 選項](../../language-reference/fsharp-interactive-options.md)。</span><span class="sxs-lookup"><span data-stu-id="e83e6-108">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="e83e6-109">若要透過 Visual Studio 執行 F# Interactive，您可以按一下標示為 **F# Interactive** 的合適工具列按鈕，或使用按鍵 **Ctrl+Alt+F** 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-109">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive** , or use the keys **Ctrl+Alt+F** .</span></span> <span data-ttu-id="e83e6-110">如此會開啟互動式視窗，也就是執行 F# Interactive 工作階段的工具視窗。</span><span class="sxs-lookup"><span data-stu-id="e83e6-110">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="e83e6-111">您也可以選取要在互動式視窗中執行的一些程式碼，然後按按鍵組合 **Alt + Enter** 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-111">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter** .</span></span> <span data-ttu-id="e83e6-112">F# Interactive 會隨即在標示為 **F# Interactive** 的工具視窗中啟動。</span><span class="sxs-lookup"><span data-stu-id="e83e6-112">F# Interactive starts in a tool window labeled **F# Interactive** .</span></span> <span data-ttu-id="e83e6-113">當您使用這個按鍵組合時，請確定編輯器視窗具有焦點。</span><span class="sxs-lookup"><span data-stu-id="e83e6-113">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="e83e6-114">不論是使用主控台還是否 Visual Studio，命令提示字元都會出現，表示解譯器在等待您輸入。</span><span class="sxs-lookup"><span data-stu-id="e83e6-114">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="e83e6-115">您可以如同在程式碼檔案中一樣輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="e83e6-115">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="e83e6-116">若要編譯並執行程式碼，請輸入兩個分號 ( **;;** ) 以終止一或數行的輸入。</span><span class="sxs-lookup"><span data-stu-id="e83e6-116">To compile and execute the code, enter two semicolons ( **;;** ) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="e83e6-117">F# Interactive 會嘗試編譯程式碼，如果成功的話，它會執行程式碼，並列印它所編譯的類型與值的簽章。</span><span class="sxs-lookup"><span data-stu-id="e83e6-117">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="e83e6-118">如果發生錯誤，解譯器就會列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e83e6-118">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="e83e6-119">在同一個工作階段中輸入的程式碼，可以存取先前輸入的所有建構，因此您可以建置程式。</span><span class="sxs-lookup"><span data-stu-id="e83e6-119">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="e83e6-120">若有需要，可利用 [工具] 視窗中的延伸緩衝區，視需要將程式碼複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="e83e6-120">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="e83e6-121">在 Visual Studio 中執行 F# Interactive 時，會與專案分開執行，因此，舉例來說，除非您將函式的程式碼複製到 [互動] 視窗，否則無法使用在 F# Interactive 中專案內所定義的建構。</span><span class="sxs-lookup"><span data-stu-id="e83e6-121">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="e83e6-122">若您開啟了參考某些程式庫的專案，則可以透過方案總管  參考 F# Interactive 中的這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="e83e6-122">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer** .</span></span> <span data-ttu-id="e83e6-123">若要參考 F# Interactive 中的程式庫，請展開 [參考]  節點，開啟程式庫的捷徑功能表，然後選擇 [傳送至 F# Interactive]  。</span><span class="sxs-lookup"><span data-stu-id="e83e6-123">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive** .</span></span>

<span data-ttu-id="e83e6-124">您可以調整設定來控制 F# Interactive 命令列引數 (選項)。</span><span class="sxs-lookup"><span data-stu-id="e83e6-124">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="e83e6-125">在 [工具]  功能表上，選取 [選項...]  ，然後展開 [F# 工具]  。</span><span class="sxs-lookup"><span data-stu-id="e83e6-125">On the **Tools** menu, select **Options...** , and then expand **F# Tools** .</span></span> <span data-ttu-id="e83e6-126">您只能變更 F# Interactive 選項和 [64 位元 F# Interactive]  這兩項設定，而且只有在 64 位元電腦上執行 F# Interactive 時才相關。</span><span class="sxs-lookup"><span data-stu-id="e83e6-126">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="e83e6-127">這項設定會判斷您要執行專用的 64 位元版 fsi.exe 或 fsianycpu.exe，它會使用電腦架構判斷要以 32 位元或 64 位元處理序執行。</span><span class="sxs-lookup"><span data-stu-id="e83e6-127">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="e83e6-128">使用 F 編寫腳本\#</span><span class="sxs-lookup"><span data-stu-id="e83e6-128">Scripting with F\#</span></span>

<span data-ttu-id="e83e6-129">指令碼使用副檔名 **.fsx** 或 **.fsscript** 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-129">Scripts use the file extension **.fsx** or **.fsscript** .</span></span> <span data-ttu-id="e83e6-130">您可以直接執行 **dotnet fsi** 並指定 f # 原始程式碼的指令檔名，而 f # interactive 會即時讀取程式碼並執行它，而不是編譯原始程式碼，然後稍後再執行已編譯的元件。</span><span class="sxs-lookup"><span data-stu-id="e83e6-130">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="e83e6-131">互動式、腳本和編譯環境之間的差異</span><span class="sxs-lookup"><span data-stu-id="e83e6-131">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="e83e6-132">當您編譯 F# Interactive 中的程式碼時，無論是以互動方式執行或是執行指令碼，都會定義符號 **INTERACTIVE** 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-132">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="e83e6-133">當您在編譯器中編譯程式碼時，會定義符號 **COMPILED** 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-133">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="e83e6-134">因此，如果已編譯模式和互動式模式中的程式碼必須不同，可以使用條件式編譯的前置處理器指示詞，決定要使用哪一種模式。</span><span class="sxs-lookup"><span data-stu-id="e83e6-134">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="e83e6-135">當您要在 F# Interactive 中執行在執行編譯器時無法使用的指令碼時，有一些指示詞可用。</span><span class="sxs-lookup"><span data-stu-id="e83e6-135">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="e83e6-136">下表摘要說明使用 F# Interactive 時可用的指示詞。</span><span class="sxs-lookup"><span data-stu-id="e83e6-136">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="e83e6-137">指示詞</span><span class="sxs-lookup"><span data-stu-id="e83e6-137">Directive</span></span>|<span data-ttu-id="e83e6-138">描述</span><span class="sxs-lookup"><span data-stu-id="e83e6-138">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="e83e6-139">**#help**</span><span class="sxs-lookup"><span data-stu-id="e83e6-139">**#help**</span></span>|<span data-ttu-id="e83e6-140">顯示可用指示詞的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e83e6-140">Displays information about available directives.</span></span>|
|<span data-ttu-id="e83e6-141">**#I**</span><span class="sxs-lookup"><span data-stu-id="e83e6-141">**#I**</span></span>|<span data-ttu-id="e83e6-142">指定加上引號的組件搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="e83e6-142">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="e83e6-143">**#load**</span><span class="sxs-lookup"><span data-stu-id="e83e6-143">**#load**</span></span>|<span data-ttu-id="e83e6-144">讀取原始程式檔、進行編譯，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="e83e6-144">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="e83e6-145">**#quit**</span><span class="sxs-lookup"><span data-stu-id="e83e6-145">**#quit**</span></span>|<span data-ttu-id="e83e6-146">終止 F# Interactive 工作階段。</span><span class="sxs-lookup"><span data-stu-id="e83e6-146">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="e83e6-147">**#r**</span><span class="sxs-lookup"><span data-stu-id="e83e6-147">**#r**</span></span>|<span data-ttu-id="e83e6-148">參考組件。</span><span class="sxs-lookup"><span data-stu-id="e83e6-148">References an assembly.</span></span>|
|<span data-ttu-id="e83e6-149">**#time ["on"&#124;"off"]**</span><span class="sxs-lookup"><span data-stu-id="e83e6-149">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="e83e6-150">**#time** 會自行切換是否顯示效能資訊。</span><span class="sxs-lookup"><span data-stu-id="e83e6-150">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="e83e6-151">當它啟用時，F# Interactive 會測量所解譯及執行的每個程式碼區段之即時、CPU 時間及記憶體回收資訊。</span><span class="sxs-lookup"><span data-stu-id="e83e6-151">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="e83e6-152">當您在 F# Interactive 中指定檔案或路徑時，應該要有一個字串常值。</span><span class="sxs-lookup"><span data-stu-id="e83e6-152">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="e83e6-153">因此，檔案和路徑必須以引號括住，並遵循一般的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="e83e6-153">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="e83e6-154">此外，您可以使用 @ 字元，讓 F# Interactive 能將包含路徑的字串，解譯為逐字字串。</span><span class="sxs-lookup"><span data-stu-id="e83e6-154">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="e83e6-155">這會導致 F# Interactive 會忽略所有逸出字元。</span><span class="sxs-lookup"><span data-stu-id="e83e6-155">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="e83e6-156">已編譯模式和互動式模式之間，其中一項差異是存取命令列引數的方式。</span><span class="sxs-lookup"><span data-stu-id="e83e6-156">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="e83e6-157">在編譯模式中是使用 **System.Environment.GetCommandLineArgs** 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-157">In compiled mode, use **System.Environment.GetCommandLineArgs** .</span></span> <span data-ttu-id="e83e6-158">而在指令碼中則是使用 **fsi.CommandLineArgs** 。</span><span class="sxs-lookup"><span data-stu-id="e83e6-158">In scripts, use **fsi.CommandLineArgs** .</span></span>

<span data-ttu-id="e83e6-159">下列程式碼說明如何建立可讀取指令碼中命令列引數的函式，同時也會示範如何從指令碼參考另一個組件。</span><span class="sxs-lookup"><span data-stu-id="e83e6-159">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="e83e6-160">第一個程式碼檔案 **MyAssembly.fs** 是要參考之組件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e83e6-160">The first code file, **MyAssembly.fs** , is the code for the assembly being referenced.</span></span> <span data-ttu-id="e83e6-161">請使用命令列 **fsc -a MyAssembly.fs** 編譯這個檔案，然後使用下列命令列以指令碼形式執行第二個檔案： **fsi --exec file1.fsx** test</span><span class="sxs-lookup"><span data-stu-id="e83e6-161">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

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

<span data-ttu-id="e83e6-162">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="e83e6-162">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="package-management-in-f-interactive"></a><span data-ttu-id="e83e6-163">F# 互動中的套件管理</span><span class="sxs-lookup"><span data-stu-id="e83e6-163">Package Management in F# Interactive</span></span>

[!NOTE] <span data-ttu-id="e83e6-164">封裝管理可作為的預覽功能 `dotnet fsi` ，隨附于 `3.1.300` 和更高版本的 .net sdk，以及所有 `5.*` 版本的 .net sdk。</span><span class="sxs-lookup"><span data-stu-id="e83e6-164">Package management is available as a preview feature in versions of `dotnet fsi` shipped in the `3.1.300` and greater versions of the .NET SDK, as well as all `5.*` versions of the .NET SDK.</span></span> <span data-ttu-id="e83e6-165">若要在此預覽版本中啟用它，請 `dotnet fsi` 使用 `--langversion:preview` 引數執行。</span><span class="sxs-lookup"><span data-stu-id="e83e6-165">To enable it in this preview release, run `dotnet fsi` with the `--langversion:preview` argument.</span></span>

<span data-ttu-id="e83e6-166">`#r`在 F# 互動中參考 DLL 的語法也可以透過下列語法來參考 nuget 套件：</span><span class="sxs-lookup"><span data-stu-id="e83e6-166">The `#r` syntax for referencing a DLL in F# Interactive can also be used to reference a nuget package via the following syntax:</span></span>

```fsharp
#r "nuget: <package name>"
```

<span data-ttu-id="e83e6-167">例如，若要參考 `FSharp.Data` 封裝，請使用下列 `#r` 參考：</span><span class="sxs-lookup"><span data-stu-id="e83e6-167">For example, to reference the `FSharp.Data` package, use the following `#r` reference:</span></span>

```fsharp
#r "nuget: FSharp.Data"
```

<span data-ttu-id="e83e6-168">執行這一行之後，最新版本的 `FSharp.Data` 套件將會下載至您的 nuget 快取，並在目前的 F# 互動會話中參考。</span><span class="sxs-lookup"><span data-stu-id="e83e6-168">After executing this line, the latest version of the `FSharp.Data` package will be downloaded to your nuget cache and referenced in the current F# Interactive session.</span></span>

<span data-ttu-id="e83e6-169">除了封裝名稱之外，還可以透過簡短的語法參考封裝的特定版本：</span><span class="sxs-lookup"><span data-stu-id="e83e6-169">In addition to the package name, specific versions of a package can be referenced via a short syntax:</span></span>

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

<span data-ttu-id="e83e6-170">或以更明確的方式：</span><span class="sxs-lookup"><span data-stu-id="e83e6-170">or in a more explicit fashion:</span></span>

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a><span data-ttu-id="e83e6-171">相關文章</span><span class="sxs-lookup"><span data-stu-id="e83e6-171">Related articles</span></span>

|<span data-ttu-id="e83e6-172">標題</span><span class="sxs-lookup"><span data-stu-id="e83e6-172">Title</span></span>|<span data-ttu-id="e83e6-173">描述</span><span class="sxs-lookup"><span data-stu-id="e83e6-173">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="e83e6-174">F# Interactive 選項</span><span class="sxs-lookup"><span data-stu-id="e83e6-174">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="e83e6-175">描述 F# 互動、fsi.exe 的命令列語法和選項。</span><span class="sxs-lookup"><span data-stu-id="e83e6-175">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
