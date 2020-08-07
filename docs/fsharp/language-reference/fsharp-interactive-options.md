---
title: 互動式選項
description: '瞭解 F # Interactive 支援的命令列選項 fsi.exe。'
ms.date: 07/22/2020
ms.openlocfilehash: abddd1fd990be18ede139ab26ffe80513ba6e0dd
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855344"
---
# <a name="f-interactive-options"></a><span data-ttu-id="fe747-103">F # Interactive 選項</span><span class="sxs-lookup"><span data-stu-id="fe747-103">F# Interactive options</span></span>

<span data-ttu-id="fe747-104">本文說明 F # Interactive 支援的命令列選項 `fsi.exe` 。</span><span class="sxs-lookup"><span data-stu-id="fe747-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="fe747-105">F # Interactive 接受許多與 F # 編譯器相同的命令列選項，但也接受一些額外的選項。</span><span class="sxs-lookup"><span data-stu-id="fe747-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="fe747-106">使用 F # Interactive 進行腳本處理</span><span class="sxs-lookup"><span data-stu-id="fe747-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="fe747-107">F # Interactive， `dotnet fsi` 可以互動方式啟動，也可以從命令列啟動以執行腳本。</span><span class="sxs-lookup"><span data-stu-id="fe747-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="fe747-108">命令列語法為</span><span class="sxs-lookup"><span data-stu-id="fe747-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="fe747-109">F # 指令檔的副檔名為 `.fsx` 。</span><span class="sxs-lookup"><span data-stu-id="fe747-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="fe747-110">F # Interactive 選項的表格</span><span class="sxs-lookup"><span data-stu-id="fe747-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="fe747-111">下表摘要說明 F # Interactive 支援的選項。</span><span class="sxs-lookup"><span data-stu-id="fe747-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="fe747-112">您可以在命令列上或透過 Visual Studio IDE 來設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="fe747-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="fe747-113">若要在 Visual Studio IDE 中設定這些選項，請開啟 [**工具**] 功能表，選取 [**選項**]，展開 [ **f # 工具**] 節點，然後選取 [ **F # Interactive**]。</span><span class="sxs-lookup"><span data-stu-id="fe747-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="fe747-114">其中清單會出現在 F # Interactive 選項引數中，list 元素會以分號分隔 (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="fe747-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="fe747-115">選項</span><span class="sxs-lookup"><span data-stu-id="fe747-115">Option</span></span>|<span data-ttu-id="fe747-116">描述</span><span class="sxs-lookup"><span data-stu-id="fe747-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="fe747-117">用來指示 F # Interactive 將其餘引數視為 F # 程式或腳本的命令列引數，您可以使用清單**fsi.exe. my.application.commandlineargs**，在程式碼中存取。</span><span class="sxs-lookup"><span data-stu-id="fe747-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="fe747-118">**--已**核取 [ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-119">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-120">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-121">**--字碼頁： &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="fe747-122">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-123">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-125">以色彩輸出警告和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fe747-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="fe747-126">**--crossoptimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-127">啟用或停用跨模組優化。</span><span class="sxs-lookup"><span data-stu-id="fe747-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="fe747-128">**--debug**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="fe747-129">**--debug：**[**full**&#124;**pdbonly**&#124;**便攜**&#124;**embedded**]</span><span class="sxs-lookup"><span data-stu-id="fe747-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="fe747-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="fe747-131">**-g：**[**full**&#124;**pdbonly**&#124;**便攜**&#124;**embedded**]</span><span class="sxs-lookup"><span data-stu-id="fe747-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="fe747-132">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-133">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-134">**--define： &lt; 字串&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="fe747-135">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-136">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-137">**--決定性**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-138">產生具決定性的元件， (包括模組版本 GUID 和時間戳記) 。</span><span class="sxs-lookup"><span data-stu-id="fe747-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="fe747-139">**--exec**</span><span class="sxs-lookup"><span data-stu-id="fe747-139">**--exec**</span></span>|<span data-ttu-id="fe747-140">指示 F # interactive 會在載入檔案或執行命令列上指定的腳本檔案後結束。</span><span class="sxs-lookup"><span data-stu-id="fe747-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="fe747-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="fe747-141">**--fullpaths**</span></span>|<span data-ttu-id="fe747-142">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-143">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-144">**--gui**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-145">啟用或停用 Windows Forms 事件迴圈。</span><span class="sxs-lookup"><span data-stu-id="fe747-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="fe747-146">預設值為 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="fe747-146">The default is enabled.</span></span>|
|<span data-ttu-id="fe747-147">**--help**</span><span class="sxs-lookup"><span data-stu-id="fe747-147">**--help**</span></span><br /><br /><span data-ttu-id="fe747-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="fe747-148">**-?**</span></span>|<span data-ttu-id="fe747-149">用來顯示命令列語法，以及每個選項的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="fe747-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="fe747-150">**--lib： &lt; 資料夾-清單&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="fe747-151">**-I： &lt; 資料夾清單&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="fe747-152">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-153">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-154">**--load： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="fe747-155">在啟動時編譯指定的原始程式碼，並將編譯的 F # 結構載入會話中。</span><span class="sxs-lookup"><span data-stu-id="fe747-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span> <span data-ttu-id="fe747-156">如果目標來源包含腳本指示詞，例如 **#use**或 **#load**，則您必須使用 **--use**或 **#use** ，而不是 **--load**或 **#load**。</span><span class="sxs-lookup"><span data-stu-id="fe747-156">If the target source contains scripting directives such as **#use** or **#load**, then you must use **--use** or **#use** instead of **--load** or **#load**.</span></span>|
|<span data-ttu-id="fe747-157">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="fe747-157">**--mlcompatibility**</span></span>|<span data-ttu-id="fe747-158">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-158">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-159">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-159">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-160">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="fe747-160">**--noframework**</span></span>|<span data-ttu-id="fe747-161">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-161">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-162">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="fe747-162">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="fe747-163">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="fe747-163">**--nologo**</span></span>|<span data-ttu-id="fe747-164">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-164">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-165">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-165">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-166">**--nowarn： &lt; warning-list&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-166">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="fe747-167">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-167">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-168">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-168">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-169">**--optimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-169">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-170">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-170">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-171">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-171">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-172">**--preferreduilang： &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-172">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="fe747-173">指定慣用的輸出語言文化特性名稱 (例如，es、ja-jp) 。</span><span class="sxs-lookup"><span data-stu-id="fe747-173">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="fe747-174">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="fe747-174">**--quiet**</span></span>|<span data-ttu-id="fe747-175">將 F # Interactive 的輸出隱藏到**stdout**資料流程。</span><span class="sxs-lookup"><span data-stu-id="fe747-175">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="fe747-176">**--引號-debug**</span><span class="sxs-lookup"><span data-stu-id="fe747-176">**--quotations-debug**</span></span>|<span data-ttu-id="fe747-177">指定針對衍生自 F # 引號常值和反映定義的運算式，應發出額外的偵錯工具資訊。</span><span class="sxs-lookup"><span data-stu-id="fe747-177">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="fe747-178">偵錯工具資訊會加入至 F # 運算式樹狀結構節點的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="fe747-178">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="fe747-179">請參閱程式[代碼引號](code-quotations.md)和[Expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。</span><span class="sxs-lookup"><span data-stu-id="fe747-179">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="fe747-180">**--readline**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-180">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-181">在互動模式中啟用或停用 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="fe747-181">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="fe747-182">**--reference： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-182">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="fe747-183">**-r： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-183">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="fe747-184">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-184">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-185">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-185">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-186">**--tailcalls**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-186">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-187">啟用或停用 tail IL 指令，這會使堆疊框架重複用於尾遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="fe747-187">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="fe747-188">這個選項預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="fe747-188">This option is enabled by default.</span></span>|
|<span data-ttu-id="fe747-189">**--targetprofile： &lt; 字串&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-189">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="fe747-190">指定這個元件的目標 framework 設定檔。</span><span class="sxs-lookup"><span data-stu-id="fe747-190">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="fe747-191">有效值為 `mscorlib`、`netcore` 或 `netstandard`。</span><span class="sxs-lookup"><span data-stu-id="fe747-191">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="fe747-192">預設為 `mscorlib`。</span><span class="sxs-lookup"><span data-stu-id="fe747-192">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="fe747-193">**--使用： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-193">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="fe747-194">指示解譯器在啟動時使用指定的檔案做為初始輸入。</span><span class="sxs-lookup"><span data-stu-id="fe747-194">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="fe747-195">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="fe747-195">**--utf8output**</span></span>|<span data-ttu-id="fe747-196">與 fsc.exe 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-196">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="fe747-197">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-197">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-198">**--警告： &lt; 警告層級&gt;**</span><span class="sxs-lookup"><span data-stu-id="fe747-198">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="fe747-199">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-199">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-200">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-200">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-201">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="fe747-201">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="fe747-202">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-202">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-203">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-203">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="fe747-204">**--warnaserror**[ **+**&#124;**-** ]：\*\* &lt; int-list &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="fe747-204">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="fe747-205">與**fsc.exe**編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="fe747-205">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="fe747-206">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="fe747-206">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="fe747-207">F # 互動式結構化列印</span><span class="sxs-lookup"><span data-stu-id="fe747-207">F# Interactive structured printing</span></span>

<span data-ttu-id="fe747-208">F # Interactive (`dotnet fsi`) 會使用延伸版本的[結構化純文字格式](plaintext-formatting.md)來報告值。</span><span class="sxs-lookup"><span data-stu-id="fe747-208">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="fe747-209">`%A`支援純文字格式的所有功能，有些則可自訂。</span><span class="sxs-lookup"><span data-stu-id="fe747-209">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="fe747-210">如果輸出主控台支援色彩，則會以色彩標示列印。</span><span class="sxs-lookup"><span data-stu-id="fe747-210">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="fe747-211">除非您明確地評估該字串，否則會將限制放在顯示的字串長度。</span><span class="sxs-lookup"><span data-stu-id="fe747-211">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="fe747-212">透過物件可以使用一組使用者可定義的設定 `fsi` 。</span><span class="sxs-lookup"><span data-stu-id="fe747-212">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="fe747-213">針對報告的值自訂純文字列印的可用設定如下：</span><span class="sxs-lookup"><span data-stu-id="fe747-213">The available settings to customize plain text printing for reported values are:</span></span>

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="fe747-214">使用和自訂 `AddPrinter``AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="fe747-214">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="fe747-215">使用和可自訂 F # 互動式輸出中的 `fsi.AddPrinter` 列印 `fsi.AddPrintTransformer` 。</span><span class="sxs-lookup"><span data-stu-id="fe747-215">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="fe747-216">第一個函式會提供文字來取代物件的列印。</span><span class="sxs-lookup"><span data-stu-id="fe747-216">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="fe747-217">第二個函式會傳回要改為顯示的代理物件。</span><span class="sxs-lookup"><span data-stu-id="fe747-217">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="fe747-218">例如，請考慮下列 F # 程式碼：</span><span class="sxs-lookup"><span data-stu-id="fe747-218">For example, consider the following F# code:</span></span>

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

<span data-ttu-id="fe747-219">如果您執行 F # Interactive 中的範例，它會根據設定的格式化選項來輸出。</span><span class="sxs-lookup"><span data-stu-id="fe747-219">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="fe747-220">在此情況下，它會影響日期和時間的格式：</span><span class="sxs-lookup"><span data-stu-id="fe747-220">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="fe747-221">`fsi.AddPrintTransformer`可用來提供用於列印的代理物件：</span><span class="sxs-lookup"><span data-stu-id="fe747-221">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="fe747-222">這會輸出：</span><span class="sxs-lookup"><span data-stu-id="fe747-222">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="fe747-223">如果傳遞給的轉換器函式傳回 `fsi.AddPrintTransformer` `null` ，則會忽略列印轉換器。</span><span class="sxs-lookup"><span data-stu-id="fe747-223">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="fe747-224">這可以用來篩選任何輸入值，方法是從類型開始 `obj` 。</span><span class="sxs-lookup"><span data-stu-id="fe747-224">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="fe747-225">例如：</span><span class="sxs-lookup"><span data-stu-id="fe747-225">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="fe747-226">這會輸出：</span><span class="sxs-lookup"><span data-stu-id="fe747-226">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="fe747-227">相關主題</span><span class="sxs-lookup"><span data-stu-id="fe747-227">Related topics</span></span>

|<span data-ttu-id="fe747-228">Title</span><span class="sxs-lookup"><span data-stu-id="fe747-228">Title</span></span>|<span data-ttu-id="fe747-229">描述</span><span class="sxs-lookup"><span data-stu-id="fe747-229">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="fe747-230">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="fe747-230">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="fe747-231">描述 F # 編譯器可用的命令列選項， **fsc.exe**。</span><span class="sxs-lookup"><span data-stu-id="fe747-231">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
