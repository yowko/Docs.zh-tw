---
title: F# 互動 (dotnet) 參考
description: '瞭解如何使用 F# 互動 (dotnet fsi) ，以互動方式在主控台執行 F # 程式碼，或執行 F # 腳本。'
ms.date: 10/31/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: b535cb03d76909043ca192ed5a9d2078f9343795
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099472"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="987f1-103">使用 F 的互動式程式設計\#</span><span class="sxs-lookup"><span data-stu-id="987f1-103">Interactive programming with F\#</span></span>

<span data-ttu-id="987f1-104">F# 互動 (dotnet fsi) 用來以互動方式在主控台執行 F # 程式碼，或執行 F # 腳本。</span><span class="sxs-lookup"><span data-stu-id="987f1-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="987f1-105">換句話說，F# Interactive 會執行 F# 語言的 REPL (讀取、評估、列印迴圈)。</span><span class="sxs-lookup"><span data-stu-id="987f1-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="987f1-106">若要從主控台執行 F# 互動，請執行 `dotnet fsi` 。</span><span class="sxs-lookup"><span data-stu-id="987f1-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="987f1-107">您將可以 `dotnet fsi` 在任何 .NET SDK 中找到。</span><span class="sxs-lookup"><span data-stu-id="987f1-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="987f1-108">如需可用命令列選項的相關資訊，請參閱 [F# 互動選項](../../language-reference/fsharp-interactive-options.md)。</span><span class="sxs-lookup"><span data-stu-id="987f1-108">For information about available command-line options, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

## <a name="executing-code-directly-in-f-interactive"></a><span data-ttu-id="987f1-109">直接在 F# 互動中執行程式碼</span><span class="sxs-lookup"><span data-stu-id="987f1-109">Executing code directly in F# Interactive</span></span>

<span data-ttu-id="987f1-110">因為 F# 互動是 (讀取-評估-列印迴圈) 的複寫功能，所以您可以在其中以互動方式執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="987f1-110">Because F# Interactive is a REPL (read-eval-print loop), you can execute code interactively in it.</span></span> <span data-ttu-id="987f1-111">以下是從命令列執行之後的互動式會話範例 `dotnet fsi` ：</span><span class="sxs-lookup"><span data-stu-id="987f1-111">Here is an example of an interactive session after executing `dotnet fsi` from the command line:</span></span>

```console
Microsoft (R) F# Interactive version 11.0.0.0 for F# 5.0
Copyright (c) Microsoft Corporation. All Rights Reserved.

For help type #help;;

> let square x = x *  x;;
val square : x:int -> int

> square 12;;
val it : int = 144

> printfn "Hello, FSI!"
- ;;
Hello, FSI!
val it : unit = ()
```

<span data-ttu-id="987f1-112">您會看到兩個主要專案：</span><span class="sxs-lookup"><span data-stu-id="987f1-112">You'll notice two main things:</span></span>

1. <span data-ttu-id="987f1-113">所有程式碼都必須以雙分號結束， (`;;` 要評估) </span><span class="sxs-lookup"><span data-stu-id="987f1-113">All code must be terminated with a double semicolon (`;;`) to be evaluated</span></span>
2. <span data-ttu-id="987f1-114">程式碼會進行評估並儲存在 `it` 值中。</span><span class="sxs-lookup"><span data-stu-id="987f1-114">Code is evaluated and stored in an `it` value.</span></span> <span data-ttu-id="987f1-115">您可以 `it` 互動方式參考。</span><span class="sxs-lookup"><span data-stu-id="987f1-115">You can reference `it` interactively.</span></span>

<span data-ttu-id="987f1-116">F# 互動也支援多行輸入。</span><span class="sxs-lookup"><span data-stu-id="987f1-116">F# Interactive also supports multi-line input.</span></span> <span data-ttu-id="987f1-117">您只需要以雙分號 (的) 來終止提交 `;;` 。</span><span class="sxs-lookup"><span data-stu-id="987f1-117">You just need to terminate your submission with a double semicolon (`;;`).</span></span> <span data-ttu-id="987f1-118">請考慮下列已貼入 F# 互動的程式碼片段，並加以評估：</span><span class="sxs-lookup"><span data-stu-id="987f1-118">Consider the following snippet that has been pasted into and evaluated by F# Interactive:</span></span>

```console
> let getOddSquares xs =
-     xs
-     |> List.filter (fun x -> x % 2 <> 0)
-     |> List.map (fun x -> x * x)
-
- printfn "%A" (getOddSquares [1..10]);;
[1; 9; 25; 49; 81]
val getOddSquares : xs:int list -> int list
val it : unit = ()

>
```

<span data-ttu-id="987f1-119">程式碼的格式會保留下來，且 (`;;`) 終止輸入的雙重分號。</span><span class="sxs-lookup"><span data-stu-id="987f1-119">The code's formatting is preserved, and there is a double semicolon (`;;`) terminating the input.</span></span> <span data-ttu-id="987f1-120">F# 互動接著評估程式碼並印出結果！</span><span class="sxs-lookup"><span data-stu-id="987f1-120">F# Interactive then evaluated the code and printed the results!</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="987f1-121">使用 F 編寫腳本\#</span><span class="sxs-lookup"><span data-stu-id="987f1-121">Scripting with F\#</span></span>

<span data-ttu-id="987f1-122">在 F# 互動中以互動方式評估程式碼可能是很棒的學習工具，但是您很快就會發現，在一般編輯器中撰寫程式碼並不是那麼有效率。</span><span class="sxs-lookup"><span data-stu-id="987f1-122">Evaluating code interactively in F# Interactive can be a great learning tool, but you'll quickly find that it's not as productive as writing code in a normal editor.</span></span> <span data-ttu-id="987f1-123">若要支援一般程式碼編輯，您可以撰寫 F # 腳本。</span><span class="sxs-lookup"><span data-stu-id="987f1-123">To support normal code editing, you can write F# scripts.</span></span>

<span data-ttu-id="987f1-124">腳本會使用 .fsx 副檔名 **。**</span><span class="sxs-lookup"><span data-stu-id="987f1-124">Scripts use the file extension **.fsx**.</span></span> <span data-ttu-id="987f1-125">您可以直接執行 **dotnet fsi** 並指定 f # 原始程式碼的指令檔名，而 f # interactive 會即時讀取程式碼並執行它，而不是編譯原始程式碼，然後稍後再執行已編譯的元件。</span><span class="sxs-lookup"><span data-stu-id="987f1-125">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span> <span data-ttu-id="987f1-126">例如，請考慮下列稱為的腳本 `Script.fsx` ：</span><span class="sxs-lookup"><span data-stu-id="987f1-126">For example, consider the following script called `Script.fsx`:</span></span>

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

printfn "%A" (getOddSquares [1..10])
```

<span data-ttu-id="987f1-127">當您在電腦上建立這個檔案時，您可以使用來執行它， `dotnet fsi` 並直接在終端機視窗中查看輸出：</span><span class="sxs-lookup"><span data-stu-id="987f1-127">When this file is created in your machine, you can run it with `dotnet fsi` and see the output directly in your terminal window:</span></span>

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

<span data-ttu-id="987f1-128">F # 腳本在 [Visual Studio](../../get-started/get-started-visual-studio.md)、 [Visual Studio Code](../../get-started/get-started-vscode.md)和 [Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md)原生支援。</span><span class="sxs-lookup"><span data-stu-id="987f1-128">F# scripting is natively supported in [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio Code](../../get-started/get-started-vscode.md), and [Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md).</span></span>

## <a name="referencing-packages-in-f-interactive"></a><span data-ttu-id="987f1-129">在 F# 互動中參考封裝</span><span class="sxs-lookup"><span data-stu-id="987f1-129">Referencing packages in F# Interactive</span></span>

<span data-ttu-id="987f1-130">F# 互動支援使用 `#r "nuget:"` 語法和選擇性版本參考 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="987f1-130">F# Interactive supports referencing NuGet packages with the `#r "nuget:"` syntax and an optional version:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

<span data-ttu-id="987f1-131">如果未指定版本，則會採用最高可用的非預覽套件。</span><span class="sxs-lookup"><span data-stu-id="987f1-131">If a version is not specified, the highest available non-preview package is taken.</span></span> <span data-ttu-id="987f1-132">若要參考特定版本，請透過逗點引入版本。</span><span class="sxs-lookup"><span data-stu-id="987f1-132">To reference a specific version, introduce the version via a comma.</span></span> <span data-ttu-id="987f1-133">在參考套件的預覽版本時，這會很方便。</span><span class="sxs-lookup"><span data-stu-id="987f1-133">This can be handy when referencing a preview version of a package.</span></span> <span data-ttu-id="987f1-134">例如，請考慮使用 [DiffSharp](https://diffsharp.github.io/)預覽版本的這個腳本：</span><span class="sxs-lookup"><span data-stu-id="987f1-134">For example, consider this script using a preview version of [DiffSharp](https://diffsharp.github.io/):</span></span>

```fsharp
#r "nuget: DiffSharp-lite, 1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn "%A" (f (dsharp.tensor 1.2))
```

<span data-ttu-id="987f1-135">您可以在腳本中指定任意數量的封裝參考。</span><span class="sxs-lookup"><span data-stu-id="987f1-135">You can specify as many package references as you like in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="987f1-136"> (使用架構參考的腳本目前有一項限制，例如 `Microsoft.NET.Sdk.Web` 或  `Microsoft.NET.Sdk.WindowsDesktop`) 。</span><span class="sxs-lookup"><span data-stu-id="987f1-136">There's currently a limitation for scripts that use framework references (e.g.`Microsoft.NET.Sdk.Web` or  `Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="987f1-137">無法使用 Saturn、Giraffe、WinForms 等套件。</span><span class="sxs-lookup"><span data-stu-id="987f1-137">Packages like Saturn, Giraffe, WinForms are not available.</span></span> <span data-ttu-id="987f1-138">這是在問題 [#9417](https://github.com/dotnet/fsharp/issues/9417)中追蹤。</span><span class="sxs-lookup"><span data-stu-id="987f1-138">This is being tracked in issue [#9417](https://github.com/dotnet/fsharp/issues/9417).</span></span>

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a><span data-ttu-id="987f1-139">使用 F # interactive 參考磁片上的元件</span><span class="sxs-lookup"><span data-stu-id="987f1-139">Referencing assemblies on disk with F# interactive</span></span>

<span data-ttu-id="987f1-140">或者，如果您在磁片上有一個元件，而且想要在腳本中參考該元件，則可以使用 `#r` 語法來指定元件。</span><span class="sxs-lookup"><span data-stu-id="987f1-140">Alternatively, if you have an assembly on disk and wish to reference that in a script, you can use the `#r` syntax to specify an assembly.</span></span> <span data-ttu-id="987f1-141">在編譯為的專案中，請考慮下列程式碼 `MyAssembly.dll` ：</span><span class="sxs-lookup"><span data-stu-id="987f1-141">Consider the following code in a project compiled into `MyAssembly.dll`:</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

<span data-ttu-id="987f1-142">其中一個已編譯，您可以在名為的檔案中參考它，如下所示 `Script.fsx` ：</span><span class="sxs-lookup"><span data-stu-id="987f1-142">One compiled, you can reference it in a file called `Script.fsx` like so:</span></span>

```fsharp
#r "path/to/MyAssembly.dll"

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="987f1-143">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="987f1-143">The output is as follows:</span></span>

```console
dotnet fsi Script.fsx
90
```

<span data-ttu-id="987f1-144">您可以在腳本中指定任意數量的元件參考。</span><span class="sxs-lookup"><span data-stu-id="987f1-144">You can specify as many assembly references as you like in a script.</span></span>

## <a name="loading-other-scripts"></a><span data-ttu-id="987f1-145">載入其他腳本</span><span class="sxs-lookup"><span data-stu-id="987f1-145">Loading other scripts</span></span>

<span data-ttu-id="987f1-146">編寫腳本時，針對不同工作使用不同的腳本通常會很有説明。</span><span class="sxs-lookup"><span data-stu-id="987f1-146">When scripting, it can often be helpful to use different scripts for different tasks.</span></span> <span data-ttu-id="987f1-147">有時候您可能會想要在另一個腳本中重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="987f1-147">Sometimes you may want to reuse code from on script in another.</span></span> <span data-ttu-id="987f1-148">您可以簡單載入並使用來評估其內容，而不會將其內容複寫到您的檔案中 `#load` 。</span><span class="sxs-lookup"><span data-stu-id="987f1-148">Rather than copy-pasting its contents into your file, you can simple load and evaluate it with `#load`.</span></span>

<span data-ttu-id="987f1-149">請考慮下列 `Script1.fsx` 事項：</span><span class="sxs-lookup"><span data-stu-id="987f1-149">Consider the following `Script1.fsx`:</span></span>

```fsharp
let square x = x * x
```

<span data-ttu-id="987f1-150">以及使用中的檔案 `Script2.fsx` ：</span><span class="sxs-lookup"><span data-stu-id="987f1-150">And the consuming file, `Script2.fsx`:</span></span>

```fsharp
#load "Script1.fsx"
open Script1

printfn "%d" (square 12)
```

<span data-ttu-id="987f1-151">請注意，宣告 `open Script1` 是必要的。</span><span class="sxs-lookup"><span data-stu-id="987f1-151">Note that the `open Script1` declaration is required.</span></span> <span data-ttu-id="987f1-152">這是因為 F # 腳本中的結構會編譯成最上層模組，也就是它所在的指令檔名。</span><span class="sxs-lookup"><span data-stu-id="987f1-152">This is because constructs in an F# script are compiled into a top-level module that is the name of the script file it is in.</span></span>

<span data-ttu-id="987f1-153">您可以評估 `Script2.fsx` 如下：</span><span class="sxs-lookup"><span data-stu-id="987f1-153">You can evaluate `Script2.fsx` like so:</span></span>

```console
dotnet fsi Script2.fsx
144
```

<span data-ttu-id="987f1-154">您可以 `#load` 在腳本中指定所需的指示詞數目。</span><span class="sxs-lookup"><span data-stu-id="987f1-154">You can specify as many `#load` directives as you like in a script.</span></span>

## <a name="using-the-fsi-object-in-f-code"></a><span data-ttu-id="987f1-155">使用 `fsi` F # 程式碼中的物件</span><span class="sxs-lookup"><span data-stu-id="987f1-155">Using the `fsi` object in F# code</span></span>

<span data-ttu-id="987f1-156">F # 腳本可存取 `fsi` 代表 F# 互動會話的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="987f1-156">F# scripts have access to a custom `fsi` object that represents the F# Interactive session.</span></span> <span data-ttu-id="987f1-157">它可讓您自訂輸出格式等專案。</span><span class="sxs-lookup"><span data-stu-id="987f1-157">It allows you to customize things like output formatting.</span></span> <span data-ttu-id="987f1-158">它也是您可以存取命令列引數的方式。</span><span class="sxs-lookup"><span data-stu-id="987f1-158">It is also how you can access command-line arguments.</span></span>

<span data-ttu-id="987f1-159">下列範例顯示如何取得和使用命令列引數：</span><span class="sxs-lookup"><span data-stu-id="987f1-159">The following example shows how to get and use command-line arguments:</span></span>

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn "%s" arg
```

<span data-ttu-id="987f1-160">進行評估時，會列印所有引數。</span><span class="sxs-lookup"><span data-stu-id="987f1-160">When evaluated, it prints all arguments.</span></span> <span data-ttu-id="987f1-161">第一個引數一律是所評估腳本的名稱：</span><span class="sxs-lookup"><span data-stu-id="987f1-161">The first argument is always the name of the script that is evaluated:</span></span>

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

<span data-ttu-id="987f1-162">您也可以使用 `System.Environment.GetCommandLineArgs()` 來存取相同的引數。</span><span class="sxs-lookup"><span data-stu-id="987f1-162">You can also use `System.Environment.GetCommandLineArgs()` to access the same arguments.</span></span>

## <a name="f-interactive-directive-reference"></a><span data-ttu-id="987f1-163">F# 互動指示詞參考</span><span class="sxs-lookup"><span data-stu-id="987f1-163">F# Interactive directive reference</span></span>

<span data-ttu-id="987f1-164">`#r`先前看到的和指示詞 `#load` 只能在 F# 互動中使用。</span><span class="sxs-lookup"><span data-stu-id="987f1-164">The `#r` and `#load` directives seen previously are only available in F# Interactive.</span></span> <span data-ttu-id="987f1-165">只有 F# 互動有幾個指示詞可用：</span><span class="sxs-lookup"><span data-stu-id="987f1-165">There are several directives only available in F# Interactive:</span></span>

|<span data-ttu-id="987f1-166">指示詞</span><span class="sxs-lookup"><span data-stu-id="987f1-166">Directive</span></span>|<span data-ttu-id="987f1-167">Description</span><span class="sxs-lookup"><span data-stu-id="987f1-167">Description</span></span>|
|---------|-----------|
|`#r "nuget:..."`|<span data-ttu-id="987f1-168">從 NuGet 參考封裝</span><span class="sxs-lookup"><span data-stu-id="987f1-168">References a package from NuGet</span></span>|
|`#r "assembly-name.dll"`|<span data-ttu-id="987f1-169">參考磁片上的元件</span><span class="sxs-lookup"><span data-stu-id="987f1-169">References an assembly on disk</span></span>|
|`#load "file-name.fsx"`|<span data-ttu-id="987f1-170">讀取原始程式檔、進行編譯，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="987f1-170">Reads a source file, compiles it, and runs it.</span></span>|
|`#help`|<span data-ttu-id="987f1-171">顯示可用指示詞的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="987f1-171">Displays information about available directives.</span></span>|
|`#I`|<span data-ttu-id="987f1-172">指定加上引號的組件搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="987f1-172">Specifies an assembly search path in quotation marks.</span></span>|
|`#quit`|<span data-ttu-id="987f1-173">終止 F# Interactive 工作階段。</span><span class="sxs-lookup"><span data-stu-id="987f1-173">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="987f1-174">`#time "on"` 或 `#time "off"`</span><span class="sxs-lookup"><span data-stu-id="987f1-174">`#time "on"` or `#time "off"`</span></span>|<span data-ttu-id="987f1-175">它本身會 `#time` 切換是否顯示效能資訊。</span><span class="sxs-lookup"><span data-stu-id="987f1-175">By itself, `#time` toggles whether to display performance information.</span></span> <span data-ttu-id="987f1-176">當它是時 `"on"` ，F# 互動會針對所解釋和執行的每個程式碼區段，測量即時、CPU 時間和垃圾收集資訊。</span><span class="sxs-lookup"><span data-stu-id="987f1-176">When it is `"on"`, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="987f1-177">當您在 F# Interactive 中指定檔案或路徑時，應該要有一個字串常值。</span><span class="sxs-lookup"><span data-stu-id="987f1-177">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="987f1-178">因此，檔案和路徑必須以引號括住，並遵循一般的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="987f1-178">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="987f1-179">您可以使用 `@` 字元來使 F# 互動將包含路徑的字串解讀為逐字字串。</span><span class="sxs-lookup"><span data-stu-id="987f1-179">You can use the `@` character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="987f1-180">這會導致 F# Interactive 會忽略所有逸出字元。</span><span class="sxs-lookup"><span data-stu-id="987f1-180">This causes F# Interactive to ignore any escape characters.</span></span>

## <a name="interactive-and-compiled-preprocessor-directives"></a><span data-ttu-id="987f1-181">互動式和編譯的預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="987f1-181">Interactive and compiled preprocessor directives</span></span>

<span data-ttu-id="987f1-182">當您在 F# 互動中編譯器代碼時，無論是以互動方式執行或是執行腳本，都會定義符號 **Interactive** 。</span><span class="sxs-lookup"><span data-stu-id="987f1-182">When you compile code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="987f1-183">當您在編譯器中編譯器代碼時，會定義已 **編譯** 的符號。</span><span class="sxs-lookup"><span data-stu-id="987f1-183">When you compile code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="987f1-184">因此，如果程式碼在編譯和互動模式中必須不同，您可以使用這些預處理器指示詞進行條件式編譯，以決定要使用的是哪一個。</span><span class="sxs-lookup"><span data-stu-id="987f1-184">Thus, if code needs to be different in compiled and interactive modes, you can use these preprocessor directives for conditional compilation to determine which to use.</span></span> <span data-ttu-id="987f1-185">例如：</span><span class="sxs-lookup"><span data-stu-id="987f1-185">For example:</span></span>

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a><span data-ttu-id="987f1-186">在 Visual Studio 中使用 F# 互動</span><span class="sxs-lookup"><span data-stu-id="987f1-186">Using F# Interactive in Visual Studio</span></span>

<span data-ttu-id="987f1-187">若要透過 Visual Studio 執行 F# Interactive，您可以按一下標示為 **F# Interactive** 的合適工具列按鈕，或使用按鍵 **Ctrl+Alt+F**。</span><span class="sxs-lookup"><span data-stu-id="987f1-187">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="987f1-188">如此會開啟互動式視窗，也就是執行 F# Interactive 工作階段的工具視窗。</span><span class="sxs-lookup"><span data-stu-id="987f1-188">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="987f1-189">您也可以選取要在互動式視窗中執行的一些程式碼，然後按按鍵組合 **Alt + Enter**。</span><span class="sxs-lookup"><span data-stu-id="987f1-189">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="987f1-190">F# Interactive 會隨即在標示為 **F# Interactive** 的工具視窗中啟動。</span><span class="sxs-lookup"><span data-stu-id="987f1-190">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="987f1-191">當您使用這個按鍵組合時，請確定編輯器視窗具有焦點。</span><span class="sxs-lookup"><span data-stu-id="987f1-191">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="987f1-192">不論是使用主控台還是否 Visual Studio，命令提示字元都會出現，表示解譯器在等待您輸入。</span><span class="sxs-lookup"><span data-stu-id="987f1-192">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="987f1-193">您可以如同在程式碼檔案中一樣輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="987f1-193">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="987f1-194">若要編譯並執行程式碼，請輸入兩個分號 (**;;**) 以終止一或數行的輸入。</span><span class="sxs-lookup"><span data-stu-id="987f1-194">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="987f1-195">F# Interactive 會嘗試編譯程式碼，如果成功的話，它會執行程式碼，並列印它所編譯的類型與值的簽章。</span><span class="sxs-lookup"><span data-stu-id="987f1-195">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="987f1-196">如果發生錯誤，解譯器就會列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="987f1-196">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="987f1-197">在同一個工作階段中輸入的程式碼，可以存取先前輸入的所有建構，因此您可以建置程式。</span><span class="sxs-lookup"><span data-stu-id="987f1-197">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="987f1-198">若有需要，可利用 [工具] 視窗中的延伸緩衝區，視需要將程式碼複製到檔案。</span><span class="sxs-lookup"><span data-stu-id="987f1-198">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="987f1-199">在 Visual Studio 中執行 F# Interactive 時，會與專案分開執行，因此，舉例來說，除非您將函式的程式碼複製到 [互動] 視窗，否則無法使用在 F# Interactive 中專案內所定義的建構。</span><span class="sxs-lookup"><span data-stu-id="987f1-199">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="987f1-200">您可以調整設定， (選項) 來控制 F# 互動命令列引數。</span><span class="sxs-lookup"><span data-stu-id="987f1-200">You can control the F# Interactive command-line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="987f1-201">在 [工具] 功能表上，選取 [選項...]，然後展開 [F# 工具]。</span><span class="sxs-lookup"><span data-stu-id="987f1-201">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="987f1-202">您只能變更 F# Interactive 選項和 [64 位元 F# Interactive] 這兩項設定，而且只有在 64 位元電腦上執行 F# Interactive 時才相關。</span><span class="sxs-lookup"><span data-stu-id="987f1-202">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="987f1-203">這項設定會決定您是否要執行專用的64位版本的 **fsi.exe** 或 **fsianycpu.exe**，其使用電腦架構來判斷是否以32位或64位進程的形式執行。</span><span class="sxs-lookup"><span data-stu-id="987f1-203">This setting determines whether you want to run the dedicated 64-bit version of **fsi.exe** or **fsianycpu.exe**, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="related-articles"></a><span data-ttu-id="987f1-204">相關文章</span><span class="sxs-lookup"><span data-stu-id="987f1-204">Related articles</span></span>

|<span data-ttu-id="987f1-205">標題</span><span class="sxs-lookup"><span data-stu-id="987f1-205">Title</span></span>|<span data-ttu-id="987f1-206">說明</span><span class="sxs-lookup"><span data-stu-id="987f1-206">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="987f1-207">F# Interactive 選項</span><span class="sxs-lookup"><span data-stu-id="987f1-207">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="987f1-208">描述 F# 互動、fsi.exe 的命令列語法和選項。</span><span class="sxs-lookup"><span data-stu-id="987f1-208">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
