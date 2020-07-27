---
title: Ilasm.exe (IL 組譯工具)
description: 開始使用 Ilasm.exe，也就是 IL 組合器。 此工具會從中繼語言（IL）產生可移植的可執行檔（PE）。
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166982"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="a4df2-104">Ilasm.exe (IL 組譯工具)</span><span class="sxs-lookup"><span data-stu-id="a4df2-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="a4df2-105">IL Assembler 可從中繼語言 (IL) 中產生可攜式執行檔 (PE)</span><span class="sxs-lookup"><span data-stu-id="a4df2-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="a4df2-106">（如需 IL 的詳細資訊，請參閱[Managed 執行](../../standard/managed-execution-process.md)程式）。您可以執行產生的可執行檔（其中包含 IL 和必要的中繼資料），以判斷 IL 是否如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="a4df2-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="a4df2-107">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="a4df2-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a4df2-108">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="a4df2-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a4df2-109">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="a4df2-110">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="a4df2-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="a4df2-111">語法</span><span class="sxs-lookup"><span data-stu-id="a4df2-111">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="a4df2-112">參數</span><span class="sxs-lookup"><span data-stu-id="a4df2-112">Parameters</span></span>

| <span data-ttu-id="a4df2-113">引數</span><span class="sxs-lookup"><span data-stu-id="a4df2-113">Argument</span></span> | <span data-ttu-id="a4df2-114">描述</span><span class="sxs-lookup"><span data-stu-id="a4df2-114">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="a4df2-115">.il 原始程式檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4df2-115">The name of the .il source file.</span></span> <span data-ttu-id="a4df2-116">這個檔案由中繼資料宣告指示詞和符號 IL 指令組成。</span><span class="sxs-lookup"><span data-stu-id="a4df2-116">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="a4df2-117">可以提供多個來源檔案引數，以產生具有*Ilasm.exe*的單一 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-117">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="a4df2-118">**注意：** 請確定 il 原始程式檔中的最後一行程式碼有尾端空白字元或行結尾字元。</span><span class="sxs-lookup"><span data-stu-id="a4df2-118">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="a4df2-119">選項</span><span class="sxs-lookup"><span data-stu-id="a4df2-119">Option</span></span> | <span data-ttu-id="a4df2-120">描述</span><span class="sxs-lookup"><span data-stu-id="a4df2-120">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="a4df2-121">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="a4df2-121">**/32bitpreferred**</span></span>|<span data-ttu-id="a4df2-122">建立一個 32 位元慣用的映像 (PE32)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-122">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="a4df2-123">**/alignment：**`integer`</span><span class="sxs-lookup"><span data-stu-id="a4df2-123">**/alignment:** `integer`</span></span>|<span data-ttu-id="a4df2-124">將 FileAlignment 設定為 NT Optional 標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="a4df2-124">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="a4df2-125">如果在檔案中指定了 .alignment IL 指示詞，這個選項會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="a4df2-125">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="a4df2-126">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="a4df2-126">**/appcontainer**</span></span>|<span data-ttu-id="a4df2-127">產生在 Windows 應用程式容器中執行的 *.dll*或 *.exe*檔案，做為輸出。</span><span class="sxs-lookup"><span data-stu-id="a4df2-127">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="a4df2-128">**/arm**</span><span class="sxs-lookup"><span data-stu-id="a4df2-128">**/arm**</span></span>|<span data-ttu-id="a4df2-129">指定進階 RISC 機器 (ARM) 為目標處理器。</span><span class="sxs-lookup"><span data-stu-id="a4df2-129">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="a4df2-130">如果沒有指定映像位元，則預設為 **/32bitpreferred**。</span><span class="sxs-lookup"><span data-stu-id="a4df2-130">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="a4df2-131">**/base：**`integer`</span><span class="sxs-lookup"><span data-stu-id="a4df2-131">**/base:** `integer`</span></span>|<span data-ttu-id="a4df2-132">將 ImageBase 設定為 NT Optional 標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="a4df2-132">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="a4df2-133">如果在檔案中指定了 .imagebase IL 指示詞，這個選項會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="a4df2-133">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="a4df2-134">**/clock**</span><span class="sxs-lookup"><span data-stu-id="a4df2-134">**/clock**</span></span>|<span data-ttu-id="a4df2-135">對指定的 .il 原始程式檔以毫秒為單位測量並且報告下列編譯時間：</span><span class="sxs-lookup"><span data-stu-id="a4df2-135">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="a4df2-136">**總共執行**：執行所有緊接在後之特定作業所花費的總時間。</span><span class="sxs-lookup"><span data-stu-id="a4df2-136">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="a4df2-137">**啟動**：載入和開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-137">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="a4df2-138">**發出 MD**：發出中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a4df2-138">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="a4df2-139">**定義參考解析**：解析檔案中的定義參考。</span><span class="sxs-lookup"><span data-stu-id="a4df2-139">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="a4df2-140">**產生 CEE 檔案**：在記憶體中產生檔案映像。</span><span class="sxs-lookup"><span data-stu-id="a4df2-140">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="a4df2-141">**撰寫 PE 檔案**：撰寫 PE 檔案的映像。</span><span class="sxs-lookup"><span data-stu-id="a4df2-141">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="a4df2-142">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="a4df2-142">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="a4df2-143">包含偵錯資訊 (區域變數和引數名稱以及行號)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-143">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="a4df2-144">建立 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-144">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="a4df2-145">不帶其他值的 **/debug** 會停用 JIT 最佳化，並使用 PDB 檔案的序列點。</span><span class="sxs-lookup"><span data-stu-id="a4df2-145">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="a4df2-146">**IMPL** 會停用 JIT 最佳化，並使用隱含序列點。</span><span class="sxs-lookup"><span data-stu-id="a4df2-146">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="a4df2-147">**OPT** 會啟用 JIT 最佳化，並使用隱含序列點。</span><span class="sxs-lookup"><span data-stu-id="a4df2-147">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="a4df2-148">**/dll**</span><span class="sxs-lookup"><span data-stu-id="a4df2-148">**/dll**</span></span>|<span data-ttu-id="a4df2-149">產生 *.dll*檔案做為輸出。</span><span class="sxs-lookup"><span data-stu-id="a4df2-149">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="a4df2-150">**/enc：**`file`</span><span class="sxs-lookup"><span data-stu-id="a4df2-150">**/enc:** `file`</span></span>|<span data-ttu-id="a4df2-151">從指定的原始程式檔建立編輯後繼續差異。</span><span class="sxs-lookup"><span data-stu-id="a4df2-151">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="a4df2-152">這個引數僅供教育使用，而不支援商業用途。</span><span class="sxs-lookup"><span data-stu-id="a4df2-152">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="a4df2-153">**/exe**</span><span class="sxs-lookup"><span data-stu-id="a4df2-153">**/exe**</span></span>|<span data-ttu-id="a4df2-154">產生可執行檔做為輸出。</span><span class="sxs-lookup"><span data-stu-id="a4df2-154">Produces an executable file as output.</span></span> <span data-ttu-id="a4df2-155">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a4df2-155">This is the default.</span></span>|
|<span data-ttu-id="a4df2-156">**/flags：**`integer`</span><span class="sxs-lookup"><span data-stu-id="a4df2-156">**/flags:** `integer`</span></span>|<span data-ttu-id="a4df2-157">將 ImageFlags 設定為通用語言執行平台標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="a4df2-157">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="a4df2-158">如果在檔案中指定了 .corflags IL 指示詞，這個選項會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="a4df2-158">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="a4df2-159">如需 *integer*有效值的清單，請參閱 CorHdr.h，COMIMAGE_FLAGS。</span><span class="sxs-lookup"><span data-stu-id="a4df2-159">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="a4df2-160">**/fold**</span><span class="sxs-lookup"><span data-stu-id="a4df2-160">**/fold**</span></span>|<span data-ttu-id="a4df2-161">將相同的方法主體摺疊為一。</span><span class="sxs-lookup"><span data-stu-id="a4df2-161">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="a4df2-162">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="a4df2-162">/**highentropyva**</span></span>|<span data-ttu-id="a4df2-163">產生一個輸出可執行檔，此檔支援高熵位址空間隨機載入 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-163">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="a4df2-164">(預設為 **/appcontainer**)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-164">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="a4df2-165">**/include：**`includePath`</span><span class="sxs-lookup"><span data-stu-id="a4df2-165">**/include:** `includePath`</span></span>|<span data-ttu-id="a4df2-166">設定路徑以搜尋與 `#include`一起包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-166">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="a4df2-167">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="a4df2-167">**/itanium**</span></span>|<span data-ttu-id="a4df2-168">將 Intel Itanium 指定為目標處理器。</span><span class="sxs-lookup"><span data-stu-id="a4df2-168">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="a4df2-169">如果沒有指定映像位元，則預設為 **/pe64**。</span><span class="sxs-lookup"><span data-stu-id="a4df2-169">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="a4df2-170">**/key：**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="a4df2-170">**/key:** `keyFile`</span></span>|<span data-ttu-id="a4df2-171">使用包含在 `keyFile` 的私密金鑰來編譯含有強式簽章的 `filename`。</span><span class="sxs-lookup"><span data-stu-id="a4df2-171">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="a4df2-172">**/key** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="a4df2-172">**/key:** @`keySource`</span></span>|<span data-ttu-id="a4df2-173">使用產生於 `keySource` 的私密金鑰來編譯含有強式簽章的 `filename`。</span><span class="sxs-lookup"><span data-stu-id="a4df2-173">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="a4df2-174">**/listing**</span><span class="sxs-lookup"><span data-stu-id="a4df2-174">**/listing**</span></span>|<span data-ttu-id="a4df2-175">產生標準輸出上的清單檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-175">Produces a listing file on the standard output.</span></span> <span data-ttu-id="a4df2-176">如果省略這個選項，將不會產生任何清單檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-176">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="a4df2-177">.NET Framework 2.0 (含) 以後不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="a4df2-177">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="a4df2-178">**/mdv：**`versionString`</span><span class="sxs-lookup"><span data-stu-id="a4df2-178">**/mdv:** `versionString`</span></span>|<span data-ttu-id="a4df2-179">設定中繼資料版本字串。</span><span class="sxs-lookup"><span data-stu-id="a4df2-179">Sets the metadata version string.</span></span>|
|<span data-ttu-id="a4df2-180">**/msv：** `major` 。`minor`</span><span class="sxs-lookup"><span data-stu-id="a4df2-180">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="a4df2-181">設定中繼資料流版本，其中 `major` 和 `minor` 是整數。</span><span class="sxs-lookup"><span data-stu-id="a4df2-181">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="a4df2-182">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="a4df2-182">**/noautoinherit**</span></span>|<span data-ttu-id="a4df2-183">沒有指定基底類別時，停用 <xref:System.Object> 的預設繼承。</span><span class="sxs-lookup"><span data-stu-id="a4df2-183">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="a4df2-184">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="a4df2-184">**/nocorstub**</span></span>|<span data-ttu-id="a4df2-185">隱藏 CORExeMain 虛設常式 (Stub) 的產生。</span><span class="sxs-lookup"><span data-stu-id="a4df2-185">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="a4df2-186">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="a4df2-186">**/nologo**</span></span>|<span data-ttu-id="a4df2-187">隱藏 Microsoft 程式啟始資訊顯示。</span><span class="sxs-lookup"><span data-stu-id="a4df2-187">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="a4df2-188">**/output：**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="a4df2-188">**/output:** `file.ext`</span></span>|<span data-ttu-id="a4df2-189">指定輸出檔的名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="a4df2-189">Specifies the output file name and extension.</span></span> <span data-ttu-id="a4df2-190">依預設值，輸出檔的名稱和第一個原始程式檔的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="a4df2-190">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="a4df2-191">預設副檔名為 *.exe*。</span><span class="sxs-lookup"><span data-stu-id="a4df2-191">The default extension is *.exe*.</span></span> <span data-ttu-id="a4df2-192">如果您指定 **/dll**選項，預設副檔名會是 *.dll*。</span><span class="sxs-lookup"><span data-stu-id="a4df2-192">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="a4df2-193">**注意：** 指定 **/output**:myfile.dll 不會設定 **/dll**選項。</span><span class="sxs-lookup"><span data-stu-id="a4df2-193">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="a4df2-194">如果您未指定 **/dll**，結果會是名為*myfile.dll*的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-194">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="a4df2-195">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="a4df2-195">**/optimize**</span></span>|<span data-ttu-id="a4df2-196">將長指令最佳化為短指令。</span><span class="sxs-lookup"><span data-stu-id="a4df2-196">Optimizes long instructions to short.</span></span> <span data-ttu-id="a4df2-197">例如， `br` 變成 `br.s`。</span><span class="sxs-lookup"><span data-stu-id="a4df2-197">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="a4df2-198">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="a4df2-198">**/pe64**</span></span>|<span data-ttu-id="a4df2-199">建立 64 位元的映像 (PE32+)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-199">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="a4df2-200">如果沒有指定目標處理器，則預設為 `/itanium`。</span><span class="sxs-lookup"><span data-stu-id="a4df2-200">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="a4df2-201">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="a4df2-201">**/pdb**</span></span>|<span data-ttu-id="a4df2-202">在不啟用偵錯資訊追蹤的情況下建立 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-202">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="a4df2-203">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="a4df2-203">**/quiet**</span></span>|<span data-ttu-id="a4df2-204">指定安靜模式；不報告組譯碼 (Assembly) 程序。</span><span class="sxs-lookup"><span data-stu-id="a4df2-204">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="a4df2-205">**/resource：**`file.res`</span><span class="sxs-lookup"><span data-stu-id="a4df2-205">**/resource:** `file.res`</span></span>|<span data-ttu-id="a4df2-206">以 .res 格式將指定的資源檔包含在 \* 產生的 *.exe*或 *.dll*檔案中。</span><span class="sxs-lookup"><span data-stu-id="a4df2-206">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="a4df2-207">使用 **/resource** 選項只能指定一個 .res 檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-207">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="a4df2-208">**/ssver：** `int` 。`int`</span><span class="sxs-lookup"><span data-stu-id="a4df2-208">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="a4df2-209">設定在 NT 選擇標題上的子系統版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a4df2-209">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="a4df2-210">對於 **/appcontainer** 和 **/arm** 的最小版本號碼為 6.02。</span><span class="sxs-lookup"><span data-stu-id="a4df2-210">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="a4df2-211">**/stack：**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="a4df2-211">**/stack:** `stackSize`</span></span>|<span data-ttu-id="a4df2-212">將 NT 選擇性標頭中的 SizeOfStackReserve 值設定為 `stackSize`。</span><span class="sxs-lookup"><span data-stu-id="a4df2-212">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="a4df2-213">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="a4df2-213">**/stripreloc**</span></span>|<span data-ttu-id="a4df2-214">指定不需要基底重新配置。</span><span class="sxs-lookup"><span data-stu-id="a4df2-214">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="a4df2-215">**/subsystem：**`integer`</span><span class="sxs-lookup"><span data-stu-id="a4df2-215">**/subsystem:** `integer`</span></span>|<span data-ttu-id="a4df2-216">將子系統設定為 NT Optional 標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="a4df2-216">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="a4df2-217">如果在檔案中指定了 .subsystem IL 指示詞，這個命令會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="a4df2-217">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="a4df2-218">如需 `integer`有效值的清單，請參閱 winnt.h，IMAGE_SUBSYSTEM。</span><span class="sxs-lookup"><span data-stu-id="a4df2-218">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="a4df2-219">**/x64**</span><span class="sxs-lookup"><span data-stu-id="a4df2-219">**/x64**</span></span>|<span data-ttu-id="a4df2-220">將 64 位元的 AMD 處理器指定為目標處理器。</span><span class="sxs-lookup"><span data-stu-id="a4df2-220">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="a4df2-221">如果沒有指定映像位元，則預設為 **/pe64**。</span><span class="sxs-lookup"><span data-stu-id="a4df2-221">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="a4df2-222">**/?**</span><span class="sxs-lookup"><span data-stu-id="a4df2-222">**/?**</span></span>|<span data-ttu-id="a4df2-223">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="a4df2-223">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="a4df2-224">*Ilasm.exe*的所有選項都不區分大小寫，且前三個字母都能辨識。</span><span class="sxs-lookup"><span data-stu-id="a4df2-224">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="a4df2-225">例如， **/lis**相當於 **/listing** ，而 **/res**： myresfile.res 相當於 **/resource**： myresfile.res. .res。指定引數的選項會接受冒號（:)或等號（=）做為選項和引數之間的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a4df2-225">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="a4df2-226">例如， **/output**：*file. ext*相當於 **/output** = *副檔名*。</span><span class="sxs-lookup"><span data-stu-id="a4df2-226">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4df2-227">備註</span><span class="sxs-lookup"><span data-stu-id="a4df2-227">Remarks</span></span>

<span data-ttu-id="a4df2-228">IL 組譯工具可協助工具廠商設計及實作 IL 產生器。</span><span class="sxs-lookup"><span data-stu-id="a4df2-228">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="a4df2-229">使用*Ilasm.exe*，工具和編譯器開發人員可以專注于 il 和中繼資料的產生，而不需要擔心以 PE 檔案格式發出 il。</span><span class="sxs-lookup"><span data-stu-id="a4df2-229">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="a4df2-230">類似于以執行時間為目標的其他編譯器，例如 c # 和 Visual Basic， *Ilasm.exe*不會產生中繼目的檔，而且不需要連結階段來形成 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-230">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="a4df2-231">IL 組譯工具可以表示所有現有的中繼資料和以執行階段為目標之程式語言的 IL 功能。</span><span class="sxs-lookup"><span data-stu-id="a4df2-231">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="a4df2-232">這可讓以任何程式設計語言撰寫的 managed 程式碼，在 IL 組合器中適當地表示，並使用*Ilasm.exe*進行編譯。</span><span class="sxs-lookup"><span data-stu-id="a4df2-232">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="a4df2-233">如果 .il 原始程式檔中程式碼的最後一行沒有尾端空白字元或行結尾字元，編譯就可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="a4df2-233">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="a4df2-234">您可以使用*Ilasm.exe*搭配其附屬工具， [*Ildasm.exe*](ildasm-exe-il-disassembler.md)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-234">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="a4df2-235">*Ildasm.exe*採用包含 IL 程式碼的 PE 檔案，並建立適合做為*Ilasm.exe*輸入的文字檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-235">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="a4df2-236">這非常有用，例如在不支援所有執行階段中繼資料屬性的程式語言中編譯程式碼時。</span><span class="sxs-lookup"><span data-stu-id="a4df2-236">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="a4df2-237">在編譯器代碼並透過*Ildasm.exe*執行輸出之後，可以手動編輯產生的 IL 文字檔來加入遺漏的屬性。</span><span class="sxs-lookup"><span data-stu-id="a4df2-237">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="a4df2-238">接著，您可以透過*Ilasm.exe*執行這個文字檔，以產生最終的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-238">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="a4df2-239">您也可以使用這項技術來由不同編譯器所原始產生的數個 PE 檔中產生單一 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="a4df2-239">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="a4df2-240">目前您無法將這項技術用於包含內嵌機器碼的 PE 檔 (例如，由 Visual C++ 所產生的 PE 檔)。</span><span class="sxs-lookup"><span data-stu-id="a4df2-240">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="a4df2-241">為了讓*Ildasm.exe*和*Ilasm.exe*的結合使用盡可能精確，根據預設，組合器不會將簡短編碼取代為您可能已在 IL 來源（或由另一個編譯器發出的）中寫入的長時間。</span><span class="sxs-lookup"><span data-stu-id="a4df2-241">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="a4df2-242">使用 **/optimize** 選項在可能的情況下替代短編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a4df2-242">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="a4df2-243">*Ildasm.exe*只會對磁片上的檔案進行操作。</span><span class="sxs-lookup"><span data-stu-id="a4df2-243">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="a4df2-244">它無法在安裝於全域組件快取中的檔案上作業。</span><span class="sxs-lookup"><span data-stu-id="a4df2-244">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="a4df2-245">如需 IL 文法的詳細資訊，請參閱 Windows SDK 中的 asmparse.grammar 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-245">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="a4df2-246">版本資訊</span><span class="sxs-lookup"><span data-stu-id="a4df2-246">Version Information</span></span>

<span data-ttu-id="a4df2-247">從 .NET Framework 4.5 開始，您可以使用類似下列的程式碼來附加自訂屬性至介面實作：</span><span class="sxs-lookup"><span data-stu-id="a4df2-247">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="a4df2-248">從 .NET Framework 4.5 開始，您可以指定選擇性封送處理 BLOB (二進位大型物件) 使用其未經處理的二進位表示，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="a4df2-248">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="a4df2-249">如需 IL 文法的詳細資訊，請參閱 Windows SDK 中的 asmparse.grammar 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-249">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="a4df2-250">範例</span><span class="sxs-lookup"><span data-stu-id="a4df2-250">Examples</span></span>

<span data-ttu-id="a4df2-251">下列命令會組譯 IL 檔 *myTestFile.il*，並產生可執行檔 *myTestFile.exe*。</span><span class="sxs-lookup"><span data-stu-id="a4df2-251">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="a4df2-252">下列命令會組譯 IL 檔 *myTestFile.il*，並產生 *.dll*檔案 *myTestFile.dll*。</span><span class="sxs-lookup"><span data-stu-id="a4df2-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="a4df2-253">下列命令會組譯 IL 檔 *myTestFile.il*，並產生 *.dll*檔案 *myNewTestFile.dll*。</span><span class="sxs-lookup"><span data-stu-id="a4df2-253">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="a4df2-254">下列程式碼範例會顯示極為簡單的應用程式，將 "Hello World!" 顯示</span><span class="sxs-lookup"><span data-stu-id="a4df2-254">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="a4df2-255">。</span><span class="sxs-lookup"><span data-stu-id="a4df2-255">to the console.</span></span> <span data-ttu-id="a4df2-256">您可以編譯此程式碼，然後使用[*Ildasm.exe*](ildasm-exe-il-disassembler.md)工具來產生 IL 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4df2-256">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="a4df2-257">下列 IL 程式碼範例會對應至之前的 C# 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="a4df2-257">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="a4df2-258">您可以使用 IL 組譯工具，將這個程式碼編譯為組件。</span><span class="sxs-lookup"><span data-stu-id="a4df2-258">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="a4df2-259">IL 和 C# 這兩個程式碼範例都將 "Hello World!" 顯示</span><span class="sxs-lookup"><span data-stu-id="a4df2-259">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="a4df2-260">。</span><span class="sxs-lookup"><span data-stu-id="a4df2-260">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="a4df2-261">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4df2-261">See also</span></span>

- [<span data-ttu-id="a4df2-262">工具</span><span class="sxs-lookup"><span data-stu-id="a4df2-262">Tools</span></span>](index.md)
- [<span data-ttu-id="a4df2-263">*Ildasm.exe* （IL 解譯器）</span><span class="sxs-lookup"><span data-stu-id="a4df2-263">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="a4df2-264">Managed 執行進程</span><span class="sxs-lookup"><span data-stu-id="a4df2-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="a4df2-265">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="a4df2-265">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
