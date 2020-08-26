---
title: 互動式選項
description: 瞭解 F# 互動、fsi.exe 所支援的命令列選項。
ms.date: 08/15/2020
ms.openlocfilehash: adc8dc86f14366720e1acbf35115d4e318a76aef
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810527"
---
# <a name="f-interactive-options"></a><span data-ttu-id="be436-103">F# 互動選項</span><span class="sxs-lookup"><span data-stu-id="be436-103">F# Interactive options</span></span>

<span data-ttu-id="be436-104">本文說明 F# 互動所支援的命令列選項 `fsi.exe` 。</span><span class="sxs-lookup"><span data-stu-id="be436-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="be436-105">F# 互動接受許多與 F # 編譯器相同的命令列選項，但也接受一些額外的選項。</span><span class="sxs-lookup"><span data-stu-id="be436-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="be436-106">使用 F# 互動編寫腳本</span><span class="sxs-lookup"><span data-stu-id="be436-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="be436-107">F# 互動， `dotnet fsi` 可以透過互動方式啟動，也可以從命令列啟動來執行腳本。</span><span class="sxs-lookup"><span data-stu-id="be436-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="be436-108">命令列語法為</span><span class="sxs-lookup"><span data-stu-id="be436-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="be436-109">F # 腳本檔案的副檔名為 `.fsx` 。</span><span class="sxs-lookup"><span data-stu-id="be436-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="be436-110">F# 互動選項的表格</span><span class="sxs-lookup"><span data-stu-id="be436-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="be436-111">下表摘要說明 F# 互動所支援的選項。</span><span class="sxs-lookup"><span data-stu-id="be436-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="be436-112">您可以在命令列上或透過 Visual Studio IDE 來設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="be436-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="be436-113">若要在 Visual Studio IDE 中設定這些選項，請開啟 [ **工具** ] 功能表，選取 [ **選項**]，展開 [ **F # 工具** ] 節點，然後選取 [ **F# 互動**]。</span><span class="sxs-lookup"><span data-stu-id="be436-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="be436-114">清單元素會以分號分隔 F# 互動選項引數， (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="be436-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="be436-115">選項</span><span class="sxs-lookup"><span data-stu-id="be436-115">Option</span></span>|<span data-ttu-id="be436-116">描述</span><span class="sxs-lookup"><span data-stu-id="be436-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="be436-117">用來指示 F# 互動將其餘引數視為 F # 程式或腳本的命令列引數，您可以使用 **Fsi >my.application.commandlineargs**，在程式碼中存取這些引數。</span><span class="sxs-lookup"><span data-stu-id="be436-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="be436-118">**--checked**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-119">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-120">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-121">**--字碼頁： &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="be436-122">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-123">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-125">以色彩輸出警告和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="be436-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="be436-126">**--crossoptimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-127">啟用或停用跨模組優化。</span><span class="sxs-lookup"><span data-stu-id="be436-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="be436-128">**--debug**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="be436-129">**--debug：**[**full**&#124;**pdbonly**&#124;**便攜**&#124;**embedded**]</span><span class="sxs-lookup"><span data-stu-id="be436-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="be436-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="be436-131">**-g：**[**full**&#124;**pdbonly**&#124;**便攜**&#124;**embedded**]</span><span class="sxs-lookup"><span data-stu-id="be436-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="be436-132">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-133">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-134">**--define： &lt; 字串&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="be436-135">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-136">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-137">**--具決定性**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-138">產生具決定性的元件 (包括模組版本 GUID 和時間戳記) 。</span><span class="sxs-lookup"><span data-stu-id="be436-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="be436-139">**--exec**</span><span class="sxs-lookup"><span data-stu-id="be436-139">**--exec**</span></span>|<span data-ttu-id="be436-140">指示 F # interactive 在載入檔案或執行命令列上指定的腳本檔案後結束。</span><span class="sxs-lookup"><span data-stu-id="be436-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="be436-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="be436-141">**--fullpaths**</span></span>|<span data-ttu-id="be436-142">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-143">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-144">**--gui**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-145">啟用或停用 Windows Forms 事件迴圈。</span><span class="sxs-lookup"><span data-stu-id="be436-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="be436-146">預設值為 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="be436-146">The default is enabled.</span></span>|
|<span data-ttu-id="be436-147">**--說明**</span><span class="sxs-lookup"><span data-stu-id="be436-147">**--help**</span></span><br /><br /><span data-ttu-id="be436-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="be436-148">**-?**</span></span>|<span data-ttu-id="be436-149">用來顯示命令列語法及每個選項的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="be436-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="be436-150">**--lib： &lt; folder 清單&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="be436-151">**-I： &lt; 資料夾清單&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="be436-152">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-153">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-154">**--load： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="be436-155">在啟動時編譯指定的原始程式碼，並將編譯的 F # 結構載入至會話。</span><span class="sxs-lookup"><span data-stu-id="be436-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span>|
|<span data-ttu-id="be436-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="be436-156">**--mlcompatibility**</span></span>|<span data-ttu-id="be436-157">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-158">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-158">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-159">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="be436-159">**--noframework**</span></span>|<span data-ttu-id="be436-160">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-161">如需詳細資訊，請參閱 [編譯器選項](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="be436-161">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="be436-162">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="be436-162">**--nologo**</span></span>|<span data-ttu-id="be436-163">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-164">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-164">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-165">**--nowarn： &lt; 警告-清單&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="be436-166">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-167">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-167">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-168">**--optimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-169">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-170">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-170">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-171">**--preferreduilang： &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-171">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="be436-172">指定慣用的輸出語言文化特性名稱 (例如，es、ja-jp) 。</span><span class="sxs-lookup"><span data-stu-id="be436-172">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="be436-173">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="be436-173">**--quiet**</span></span>|<span data-ttu-id="be436-174">隱藏 F# 互動的輸出至 **stdout** 資料流程。</span><span class="sxs-lookup"><span data-stu-id="be436-174">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="be436-175">**--引號-debug**</span><span class="sxs-lookup"><span data-stu-id="be436-175">**--quotations-debug**</span></span>|<span data-ttu-id="be436-176">指定應針對衍生自 F # 引號常值和反映定義的運算式發出額外的偵錯工具資訊。</span><span class="sxs-lookup"><span data-stu-id="be436-176">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="be436-177">偵錯工具資訊會加入至 F # 運算式樹狀結構節點的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="be436-177">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="be436-178">請參閱程式 [代碼引號](code-quotations.md) 和 [CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes)。</span><span class="sxs-lookup"><span data-stu-id="be436-178">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes).</span></span>|
|<span data-ttu-id="be436-179">**--readline**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-179">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-180">啟用或停用互動式模式的 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="be436-180">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="be436-181">**--reference： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-181">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="be436-182">**-r： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-182">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="be436-183">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-183">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-184">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-184">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-185">**--tailcalls**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-185">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-186">啟用或停用 tail IL 指令，這會導致堆疊框架重複用於 tail 遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="be436-186">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="be436-187">這個選項預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="be436-187">This option is enabled by default.</span></span>|
|<span data-ttu-id="be436-188">**--targetprofile： &lt; 字串&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-188">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="be436-189">指定此元件的目標 framework 設定檔。</span><span class="sxs-lookup"><span data-stu-id="be436-189">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="be436-190">有效值為 `mscorlib`、`netcore` 或 `netstandard`。</span><span class="sxs-lookup"><span data-stu-id="be436-190">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="be436-191">預設為 `mscorlib`。</span><span class="sxs-lookup"><span data-stu-id="be436-191">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="be436-192">**--use： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-192">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="be436-193">告知解譯器在啟動時使用指定的檔案做為初始輸入。</span><span class="sxs-lookup"><span data-stu-id="be436-193">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="be436-194">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="be436-194">**--utf8output**</span></span>|<span data-ttu-id="be436-195">與 fsc.exe 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-195">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="be436-196">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-196">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-197">**--警告： &lt; 警告層級&gt;**</span><span class="sxs-lookup"><span data-stu-id="be436-197">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="be436-198">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-198">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-199">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-199">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-200">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="be436-200">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="be436-201">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-201">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-202">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-202">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="be436-203">**--warnaserror**[ **+**&#124;**-** ]：\*\* &lt; int-list &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="be436-203">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="be436-204">與 **fsc.exe** 編譯器選項相同。</span><span class="sxs-lookup"><span data-stu-id="be436-204">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="be436-205">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="be436-205">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="be436-206">F# 互動結構化列印</span><span class="sxs-lookup"><span data-stu-id="be436-206">F# Interactive structured printing</span></span>

<span data-ttu-id="be436-207">F# 互動 (`dotnet fsi`) 會使用延伸版本的 [結構化純文字格式](plaintext-formatting.md) 來報告值。</span><span class="sxs-lookup"><span data-stu-id="be436-207">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="be436-208">`%A`支援純文字格式的所有功能，而有些則是可自訂的。</span><span class="sxs-lookup"><span data-stu-id="be436-208">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="be436-209">如果輸出主控台支援色彩，則會以色彩標示列印。</span><span class="sxs-lookup"><span data-stu-id="be436-209">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="be436-210">除非您明確評估該字串，否則會將限制放在顯示的字串長度。</span><span class="sxs-lookup"><span data-stu-id="be436-210">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="be436-211">您可以透過物件取得一組使用者可定義的設定 `fsi` 。</span><span class="sxs-lookup"><span data-stu-id="be436-211">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="be436-212">針對報告值自訂純文字列印的可用設定如下：</span><span class="sxs-lookup"><span data-stu-id="be436-212">The available settings to customize plain text printing for reported values are:</span></span>

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

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="be436-213">使用和自訂 `AddPrinter``AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="be436-213">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="be436-214">您可以使用和自訂 F# 互動輸出中的列印 `fsi.AddPrinter` `fsi.AddPrintTransformer` 。</span><span class="sxs-lookup"><span data-stu-id="be436-214">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="be436-215">第一個函數會提供文字來取代物件的列印。</span><span class="sxs-lookup"><span data-stu-id="be436-215">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="be436-216">第二個函式會傳回要改為顯示的代理物件。</span><span class="sxs-lookup"><span data-stu-id="be436-216">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="be436-217">例如，請考慮下列 F # 程式碼：</span><span class="sxs-lookup"><span data-stu-id="be436-217">For example, consider the following F# code:</span></span>

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

<span data-ttu-id="be436-218">如果您在 F# 互動中執行此範例，它會根據格式化選項組進行輸出。</span><span class="sxs-lookup"><span data-stu-id="be436-218">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="be436-219">在此情況下，它會影響日期和時間的格式：</span><span class="sxs-lookup"><span data-stu-id="be436-219">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="be436-220">`fsi.AddPrintTransformer` 可以用來提供要列印的代理物件：</span><span class="sxs-lookup"><span data-stu-id="be436-220">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="be436-221">輸出如下：</span><span class="sxs-lookup"><span data-stu-id="be436-221">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="be436-222">如果傳遞的轉換器函式 `fsi.AddPrintTransformer` 傳回 `null` ，則會忽略列印轉換器。</span><span class="sxs-lookup"><span data-stu-id="be436-222">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="be436-223">這可以用來以型別開頭，以篩選任何輸入值 `obj` 。</span><span class="sxs-lookup"><span data-stu-id="be436-223">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="be436-224">例如：</span><span class="sxs-lookup"><span data-stu-id="be436-224">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="be436-225">輸出如下：</span><span class="sxs-lookup"><span data-stu-id="be436-225">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="be436-226">相關主題</span><span class="sxs-lookup"><span data-stu-id="be436-226">Related topics</span></span>

|<span data-ttu-id="be436-227">標題</span><span class="sxs-lookup"><span data-stu-id="be436-227">Title</span></span>|<span data-ttu-id="be436-228">描述</span><span class="sxs-lookup"><span data-stu-id="be436-228">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="be436-229">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="be436-229">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="be436-230">描述 F # 編譯器可用的命令列選項， **fsc.exe**。</span><span class="sxs-lookup"><span data-stu-id="be436-230">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
