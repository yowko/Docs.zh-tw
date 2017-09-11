---
title: "Ilasm.exe (IL 組譯工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
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
caps.latest.revision: 41
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fba6c6a912cc9d2df9e1b9b11790840f782922d5
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="20b11-102">Ilasm.exe (IL 組譯工具)</span><span class="sxs-lookup"><span data-stu-id="20b11-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="20b11-103">IL Assembler 可從中繼語言 (IL) 中產生可攜式執行檔 (PE)</span><span class="sxs-lookup"><span data-stu-id="20b11-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="20b11-104">(如需 IL 的詳細資訊，請參閱 [Managed 執行程序](../../../docs/standard/managed-execution-process.md))。您可以執行產生的可執行檔 (包含 IL 和所需的中繼資料)，來判斷 IL 是否如預期般地執行。</span><span class="sxs-lookup"><span data-stu-id="20b11-104">(For more information on IL, see [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="20b11-105">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="20b11-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="20b11-106">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="20b11-106">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="20b11-107">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="20b11-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="20b11-108">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="20b11-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="20b11-109">語法</span><span class="sxs-lookup"><span data-stu-id="20b11-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

#### <a name="parameters"></a><span data-ttu-id="20b11-110">參數</span><span class="sxs-lookup"><span data-stu-id="20b11-110">Parameters</span></span>

| <span data-ttu-id="20b11-111">引數</span><span class="sxs-lookup"><span data-stu-id="20b11-111">Argument</span></span> | <span data-ttu-id="20b11-112">說明</span><span class="sxs-lookup"><span data-stu-id="20b11-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="20b11-113">.il 原始程式檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="20b11-113">The name of the .il source file.</span></span> <span data-ttu-id="20b11-114">這個檔案由中繼資料宣告指示詞和符號 IL 指令組成。</span><span class="sxs-lookup"><span data-stu-id="20b11-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="20b11-115">您可以提供多個來源檔案引數來使用 *Ilasm.exe* 產生單一 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="20b11-116">**注意：**請確認 .il 原始程式檔的最後一行有後置空白字元或行結尾字元。</span><span class="sxs-lookup"><span data-stu-id="20b11-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="20b11-117">選項</span><span class="sxs-lookup"><span data-stu-id="20b11-117">Option</span></span> | <span data-ttu-id="20b11-118">描述</span><span class="sxs-lookup"><span data-stu-id="20b11-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="20b11-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="20b11-119">**/32bitpreferred**</span></span>|<span data-ttu-id="20b11-120">建立一個 32 位元慣用的映像 (PE32)。</span><span class="sxs-lookup"><span data-stu-id="20b11-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="20b11-121">**/alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="20b11-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="20b11-122">將 FileAlignment 設定為 NT Optional 標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="20b11-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="20b11-123">如果在檔案中指定了 .alignment IL 指示詞，這個選項會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="20b11-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="20b11-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="20b11-124">**/appcontainer**</span></span>|<span data-ttu-id="20b11-125">產生在 Windows 應用程式容器中執行的 *.dll* 或 *.exe* 檔案，作為輸出。</span><span class="sxs-lookup"><span data-stu-id="20b11-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="20b11-126">**/arm**</span><span class="sxs-lookup"><span data-stu-id="20b11-126">**/arm**</span></span>|<span data-ttu-id="20b11-127">指定進階 RISC 機器 (ARM) 為目標處理器。</span><span class="sxs-lookup"><span data-stu-id="20b11-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="20b11-128">如果沒有指定映像位元，則預設為 **/32bitpreferred**。</span><span class="sxs-lookup"><span data-stu-id="20b11-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="20b11-129">**/base:** `integer`</span><span class="sxs-lookup"><span data-stu-id="20b11-129">**/base:** `integer`</span></span>|<span data-ttu-id="20b11-130">將 ImageBase 設定為 NT Optional 標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="20b11-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="20b11-131">如果在檔案中指定了 .imagebase IL 指示詞，這個選項會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="20b11-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="20b11-132">**/clock**</span><span class="sxs-lookup"><span data-stu-id="20b11-132">**/clock**</span></span>|<span data-ttu-id="20b11-133">對指定的 .il 原始程式檔以毫秒為單位測量並且報告下列編譯時間：</span><span class="sxs-lookup"><span data-stu-id="20b11-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="20b11-134">**總共執行**：執行所有緊接在後之特定作業所花費的總時間。</span><span class="sxs-lookup"><span data-stu-id="20b11-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="20b11-135">**啟動**：載入和開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="20b11-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="20b11-136">**發出 MD**：發出中繼資料。</span><span class="sxs-lookup"><span data-stu-id="20b11-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="20b11-137">**定義參考解析**：解析檔案中的定義參考。</span><span class="sxs-lookup"><span data-stu-id="20b11-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="20b11-138">**產生 CEE 檔案**：在記憶體中產生檔案映像。</span><span class="sxs-lookup"><span data-stu-id="20b11-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="20b11-139">**撰寫 PE 檔案**：撰寫 PE 檔案的映像。</span><span class="sxs-lookup"><span data-stu-id="20b11-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="20b11-140">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="20b11-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="20b11-141">包含偵錯資訊 (區域變數和引數名稱以及行號)。</span><span class="sxs-lookup"><span data-stu-id="20b11-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="20b11-142">建立 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="20b11-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="20b11-143">不帶其他值的**/debug** 會停用 JIT 最佳化，並使用 PDB 檔案的序列點。</span><span class="sxs-lookup"><span data-stu-id="20b11-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="20b11-144">**IMPL** 會停用 JIT 最佳化，並使用隱含序列點。</span><span class="sxs-lookup"><span data-stu-id="20b11-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="20b11-145">**OPT** 會啟用 JIT 最佳化，並使用隱含序列點。</span><span class="sxs-lookup"><span data-stu-id="20b11-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="20b11-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="20b11-146">**/dll**</span></span>|<span data-ttu-id="20b11-147">產生 *.dll* 檔案作為輸出。</span><span class="sxs-lookup"><span data-stu-id="20b11-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="20b11-148">**/enc:** `file`</span><span class="sxs-lookup"><span data-stu-id="20b11-148">**/enc:** `file`</span></span>|<span data-ttu-id="20b11-149">從指定的原始程式檔建立編輯後繼續差異。</span><span class="sxs-lookup"><span data-stu-id="20b11-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="20b11-150">這個引數僅供教育使用，而不支援商業用途。</span><span class="sxs-lookup"><span data-stu-id="20b11-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="20b11-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="20b11-151">**/exe**</span></span>|<span data-ttu-id="20b11-152">產生可執行檔做為輸出。</span><span class="sxs-lookup"><span data-stu-id="20b11-152">Produces an executable file as output.</span></span> <span data-ttu-id="20b11-153">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="20b11-153">This is the default.</span></span>|
|<span data-ttu-id="20b11-154">**/flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="20b11-154">**/flags:** `integer`</span></span>|<span data-ttu-id="20b11-155">將 ImageFlags 設定為通用語言執行平台標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="20b11-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="20b11-156">如果在檔案中指定了 .corflags IL 指示詞，這個選項會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="20b11-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="20b11-157">如需 *integer*有效值的清單，請參閱 CorHdr.h，COMIMAGE_FLAGS。</span><span class="sxs-lookup"><span data-stu-id="20b11-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="20b11-158">**/fold**</span><span class="sxs-lookup"><span data-stu-id="20b11-158">**/fold**</span></span>|<span data-ttu-id="20b11-159">將相同的方法主體摺疊為一。</span><span class="sxs-lookup"><span data-stu-id="20b11-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="20b11-160">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="20b11-160">/**highentropyva**</span></span>|<span data-ttu-id="20b11-161">產生一個輸出可執行檔，此檔支援高熵位址空間隨機載入 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="20b11-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="20b11-162">(預設為 **/appcontainer**)。</span><span class="sxs-lookup"><span data-stu-id="20b11-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="20b11-163">**/include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="20b11-163">**/include:** `includePath`</span></span>|<span data-ttu-id="20b11-164">設定路徑以搜尋與 `#include`一起包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="20b11-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="20b11-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="20b11-165">**/itanium**</span></span>|<span data-ttu-id="20b11-166">將 Intel Itanium 指定為目標處理器。</span><span class="sxs-lookup"><span data-stu-id="20b11-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="20b11-167">如果沒有指定映像位元，則預設為 **/pe64**。</span><span class="sxs-lookup"><span data-stu-id="20b11-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="20b11-168">**/key:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="20b11-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="20b11-169">使用包含在 `keyFile` 的私密金鑰來編譯含有強式簽章的 `filename`。</span><span class="sxs-lookup"><span data-stu-id="20b11-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="20b11-170">**/key:** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="20b11-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="20b11-171">使用產生於 `keySource` 的私密金鑰來編譯含有強式簽章的 `filename`。</span><span class="sxs-lookup"><span data-stu-id="20b11-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="20b11-172">**/listing**</span><span class="sxs-lookup"><span data-stu-id="20b11-172">**/listing**</span></span>|<span data-ttu-id="20b11-173">產生標準輸出上的清單檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="20b11-174">如果省略這個選項，將不會產生任何清單檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="20b11-175">.NET Framework 2.0 (含) 以後不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="20b11-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="20b11-176">**/mdv:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="20b11-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="20b11-177">設定中繼資料版本字串。</span><span class="sxs-lookup"><span data-stu-id="20b11-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="20b11-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="20b11-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="20b11-179">設定中繼資料流版本，其中 `major` 和 `minor` 是整數。</span><span class="sxs-lookup"><span data-stu-id="20b11-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="20b11-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="20b11-180">**/noautoinherit**</span></span>|<span data-ttu-id="20b11-181">沒有指定基底類別時，停用 <xref:System.Object> 的預設繼承。</span><span class="sxs-lookup"><span data-stu-id="20b11-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="20b11-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="20b11-182">**/nocorstub**</span></span>|<span data-ttu-id="20b11-183">隱藏 CORExeMain 虛設常式 (Stub) 的產生。</span><span class="sxs-lookup"><span data-stu-id="20b11-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="20b11-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="20b11-184">**/nologo**</span></span>|<span data-ttu-id="20b11-185">隱藏 Microsoft 程式啟始資訊顯示。</span><span class="sxs-lookup"><span data-stu-id="20b11-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="20b11-186">**/output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="20b11-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="20b11-187">指定輸出檔的名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="20b11-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="20b11-188">依預設值，輸出檔的名稱和第一個原始程式檔的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="20b11-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="20b11-189">預設副檔名是 *.exe*。</span><span class="sxs-lookup"><span data-stu-id="20b11-189">The default extension is *.exe*.</span></span> <span data-ttu-id="20b11-190">如果指定 **/dll** 選項，則預設副檔名會是 *.dll*。</span><span class="sxs-lookup"><span data-stu-id="20b11-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="20b11-191">**注意：**指定 **/output**:myfile.dll 並不會設定 **/dll** 選項。</span><span class="sxs-lookup"><span data-stu-id="20b11-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="20b11-192">如果沒有指定 **/dll**，結果將會是名稱為 *myfile.dll* 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="20b11-193">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="20b11-193">**/optimize**</span></span>|<span data-ttu-id="20b11-194">將長指令最佳化為短指令。</span><span class="sxs-lookup"><span data-stu-id="20b11-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="20b11-195">例如， `br` 變成 `br.s`。</span><span class="sxs-lookup"><span data-stu-id="20b11-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="20b11-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="20b11-196">**/pe64**</span></span>|<span data-ttu-id="20b11-197">建立 64 位元的映像 (PE32+)。</span><span class="sxs-lookup"><span data-stu-id="20b11-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="20b11-198">如果沒有指定目標處理器，則預設為 `/itanium`。</span><span class="sxs-lookup"><span data-stu-id="20b11-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="20b11-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="20b11-199">**/pdb**</span></span>|<span data-ttu-id="20b11-200">在不啟用偵錯資訊追蹤的情況下建立 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="20b11-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="20b11-201">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="20b11-201">**/quiet**</span></span>|<span data-ttu-id="20b11-202">指定安靜模式；不報告組譯碼 (Assembly) 程序。</span><span class="sxs-lookup"><span data-stu-id="20b11-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="20b11-203">**/resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="20b11-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="20b11-204">以 \*.res 格式將指定的資源檔包含在產生的 *.exe* 或 *.dll* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="20b11-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="20b11-205">使用 **/resource** 選項只能指定一個 .res 檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="20b11-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="20b11-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="20b11-207">設定在 NT 選擇標題上的子系統版本號碼。</span><span class="sxs-lookup"><span data-stu-id="20b11-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="20b11-208">對於 **/appcontainer** 和 **/arm** 的最小版本號碼為 6.02。</span><span class="sxs-lookup"><span data-stu-id="20b11-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="20b11-209">**/stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="20b11-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="20b11-210">將 NT 選擇性標頭中的 SizeOfStackReserve 值設定為 `stackSize`。</span><span class="sxs-lookup"><span data-stu-id="20b11-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="20b11-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="20b11-211">**/stripreloc**</span></span>|<span data-ttu-id="20b11-212">指定不需要基底重新配置。</span><span class="sxs-lookup"><span data-stu-id="20b11-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="20b11-213">**/subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="20b11-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="20b11-214">將子系統設定為 NT Optional 標頭中 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="20b11-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="20b11-215">如果在檔案中指定了 .subsystem IL 指示詞，這個命令會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="20b11-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="20b11-216">如需 `integer`有效值的清單，請參閱 winnt.h，IMAGE_SUBSYSTEM。</span><span class="sxs-lookup"><span data-stu-id="20b11-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="20b11-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="20b11-217">**/x64**</span></span>|<span data-ttu-id="20b11-218">將 64 位元的 AMD 處理器指定為目標處理器。</span><span class="sxs-lookup"><span data-stu-id="20b11-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="20b11-219">如果沒有指定映像位元，則預設為 **/pe64**。</span><span class="sxs-lookup"><span data-stu-id="20b11-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="20b11-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="20b11-220">**/?**</span></span>|<span data-ttu-id="20b11-221">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="20b11-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="20b11-222">*Ilasm.exe* 的所有選項都不區分大小寫，並以前三個字母來辨識。</span><span class="sxs-lookup"><span data-stu-id="20b11-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="20b11-223">例如，**/lis** 相當於 **/listing**，而 **/res**:myresfile.res 相當於 **/resource**:myresfile.res。</span><span class="sxs-lookup"><span data-stu-id="20b11-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res.</span></span> <span data-ttu-id="20b11-224">指定引數的選項可以接受冒號 (:) 或等號 (=) 做為選項與引數之間的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="20b11-224">Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="20b11-225">例如， **/output**:*file.ext* 等同於 **/output=**=*file.ext*。</span><span class="sxs-lookup"><span data-stu-id="20b11-225">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="20b11-226">備註</span><span class="sxs-lookup"><span data-stu-id="20b11-226">Remarks</span></span>

<span data-ttu-id="20b11-227">IL 組譯工具可協助工具廠商設計及實作 IL 產生器。</span><span class="sxs-lookup"><span data-stu-id="20b11-227">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="20b11-228">使用 *Ilasm.exe* 工具可讓編譯器開發人員專注於 IL 和中繼資料的產生，而不需考慮使用 PE 檔格式發出 IL。</span><span class="sxs-lookup"><span data-stu-id="20b11-228">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="20b11-229">類似其他以執行階段為目標的編譯器 (例如 C# 和 Visual Basic)，*Ilasm.exe* 並不會產生中繼目的檔，而且不需要連結階段來形成 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-229">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="20b11-230">IL 組譯工具可以表示所有現有的中繼資料和以執行階段為目標之程式語言的 IL 功能。</span><span class="sxs-lookup"><span data-stu-id="20b11-230">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="20b11-231">這樣以這些程式語言中任何一種所撰寫的 Managed 程式碼都能在 IL 組譯工具中適當表示，並且以 *Ilasm.exe* 編譯。</span><span class="sxs-lookup"><span data-stu-id="20b11-231">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="20b11-232">如果 .il 原始程式檔中程式碼的最後一行沒有尾端空白字元或行結尾字元，編譯就可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="20b11-232">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="20b11-233">您可以將 *Ilasm.exe* 和其附屬工具 [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 結合使用。</span><span class="sxs-lookup"><span data-stu-id="20b11-233">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="20b11-234">*Ildasm.exe* 使用包含 IL 程式碼的 PE 檔，建立適合作為 *Ilasm.exe* 輸入的文字檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-234">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="20b11-235">這非常有用，例如在不支援所有執行階段中繼資料屬性的程式語言中編譯程式碼時。</span><span class="sxs-lookup"><span data-stu-id="20b11-235">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="20b11-236">編譯完程式碼並透過 *Ildasm.exe* 執行輸出後，可以手動編輯產生的 IL 文字檔來新增遺漏的屬性。</span><span class="sxs-lookup"><span data-stu-id="20b11-236">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="20b11-237">然後可以透過 *Ilasm.exe* 執行這個文字檔來產生最終的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-237">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="20b11-238">您也可以使用這項技術來由不同編譯器所原始產生的數個 PE 檔中產生單一 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-238">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="20b11-239">目前您無法將這項技術用於包含內嵌機器碼的 PE 檔 (例如，由 Visual C++ 所產生的 PE 檔)。</span><span class="sxs-lookup"><span data-stu-id="20b11-239">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="20b11-240">為了使 *Ildasm.exe* 和 *Ilasm.exe* 的合併使用盡可能精確，根據預設，組譯工具不會將您可能在 IL 來源中撰寫的較長 (或可能已經由其他編譯器發出的) 編碼替換為較短的編碼。</span><span class="sxs-lookup"><span data-stu-id="20b11-240">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="20b11-241">使用 **/optimize** 選項在可能的情況下替代短編碼方式。</span><span class="sxs-lookup"><span data-stu-id="20b11-241">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="20b11-242">*Ildasm.exe* 只能在磁碟的檔案上作業。</span><span class="sxs-lookup"><span data-stu-id="20b11-242">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="20b11-243">它無法在安裝於全域組件快取中的檔案上作業。</span><span class="sxs-lookup"><span data-stu-id="20b11-243">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="20b11-244">如需 IL 文法的詳細資訊，請參閱 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]中的 asmparse.grammar 檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-244">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="version-information"></a><span data-ttu-id="20b11-245">版本資訊</span><span class="sxs-lookup"><span data-stu-id="20b11-245">Version Information</span></span>

<span data-ttu-id="20b11-246">從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]開始，您可以使用類似下列的程式碼附加自訂屬性至介面實作：</span><span class="sxs-lookup"><span data-stu-id="20b11-246">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```
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

<span data-ttu-id="20b11-247">從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]開始，您可以指定選擇性封送處理 BLOB (二進位大型物件) 使用它未經處理的二進位表示，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="20b11-247">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="20b11-248">如需 IL 文法的詳細資訊，請參閱 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]中的 asmparse.grammar 檔。</span><span class="sxs-lookup"><span data-stu-id="20b11-248">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="examples"></a><span data-ttu-id="20b11-249">範例</span><span class="sxs-lookup"><span data-stu-id="20b11-249">Examples</span></span>

<span data-ttu-id="20b11-250">下列命令會組譯 IL 檔 *myTestFile.il*，並產生可執行檔 *myTestFile.exe*。</span><span class="sxs-lookup"><span data-stu-id="20b11-250">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="20b11-251">下列命令會組譯 IL 檔 *myTestFile.il*，並產生 *.dll*檔案 *myTestFile.dll*。</span><span class="sxs-lookup"><span data-stu-id="20b11-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="20b11-252">下列命令會組譯 IL 檔 *myTestFile.il*，並產生 *.dll*檔案 *myNewTestFile.dll*。</span><span class="sxs-lookup"><span data-stu-id="20b11-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="20b11-253">下列程式碼範例會顯示極為簡單的應用程式，將 "Hello World!" 顯示</span><span class="sxs-lookup"><span data-stu-id="20b11-253">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="20b11-254">到主控台。</span><span class="sxs-lookup"><span data-stu-id="20b11-254">to the console.</span></span> <span data-ttu-id="20b11-255">您可以編譯此程式碼，然後使用 [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 工具來產生 IL 檔案。</span><span class="sxs-lookup"><span data-stu-id="20b11-255">You can compile this code and then use the [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="20b11-256">下列 IL 程式碼範例會對應至之前的 C# 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="20b11-256">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="20b11-257">您可以使用 IL 組譯工具，將這個程式碼編譯為組件。</span><span class="sxs-lookup"><span data-stu-id="20b11-257">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="20b11-258">IL 和 C# 這兩個程式碼範例都將 "Hello World!" 顯示</span><span class="sxs-lookup"><span data-stu-id="20b11-258">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="20b11-259">到主控台。</span><span class="sxs-lookup"><span data-stu-id="20b11-259">to the console.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="20b11-260">請參閱</span><span class="sxs-lookup"><span data-stu-id="20b11-260">See also</span></span>

[<span data-ttu-id="20b11-261">工具</span><span class="sxs-lookup"><span data-stu-id="20b11-261">Tools</span></span>](../../../docs/framework/tools/index.md)  
[<span data-ttu-id="20b11-262">*Ildasm.exe* (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="20b11-262">*Ildasm.exe* (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
[<span data-ttu-id="20b11-263">Managed 執行程序</span><span class="sxs-lookup"><span data-stu-id="20b11-263">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)  
[<span data-ttu-id="20b11-264">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="20b11-264">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

