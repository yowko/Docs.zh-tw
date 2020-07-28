---
title: Ildasm.exe (IL 反組譯工具)
description: 使用 Ildasm.exe （IL 解譯器），它會採用包含中繼語言（IL）程式碼的可移植執行檔（PE），並建立用於 Ilasm.exe 的文字檔。
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
ms.openlocfilehash: 6f2611488e7f653783cab833ad47131978bf74aa
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166832"
---
# <a name="ildasmexe-il-disassembler"></a><span data-ttu-id="14193-103">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="14193-103">Ildasm.exe (IL Disassembler)</span></span>

<span data-ttu-id="14193-104">IL 反組譯工具是 IL 組譯工具 (*Ilasm.exe*) 的附屬工具。</span><span class="sxs-lookup"><span data-stu-id="14193-104">The IL Disassembler is a companion tool to the IL Assembler (*Ilasm.exe*).</span></span> <span data-ttu-id="14193-105">*Ildasm.exe* 採用包含中繼語言 (IL) 程式碼的可攜式執行檔 (PE)，並建立適合用作 *Ilasm.exe* 輸入的文字檔。</span><span class="sxs-lookup"><span data-stu-id="14193-105">*Ildasm.exe* takes a portable executable (PE) file that contains intermediate language (IL) code and creates a text file suitable as input to *Ilasm.exe*.</span></span>

<span data-ttu-id="14193-106">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="14193-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="14193-107">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="14193-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="14193-108">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="14193-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="14193-109">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="14193-109">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="14193-110">語法</span><span class="sxs-lookup"><span data-stu-id="14193-110">Syntax</span></span>

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a><span data-ttu-id="14193-111">參數</span><span class="sxs-lookup"><span data-stu-id="14193-111">Parameters</span></span>

<span data-ttu-id="14193-112">下列選項適用于 *.exe*、 *.dll*、 *.obj*、 *.lib*和*winmd*檔案。</span><span class="sxs-lookup"><span data-stu-id="14193-112">The following options are available for *.exe*, *.dll*, *.obj*, *.lib*, and *.winmd* files.</span></span>

| <span data-ttu-id="14193-113">選項</span><span class="sxs-lookup"><span data-stu-id="14193-113">Option</span></span> | <span data-ttu-id="14193-114">描述</span><span class="sxs-lookup"><span data-stu-id="14193-114">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="14193-115">**/out =**`filename`</span><span class="sxs-lookup"><span data-stu-id="14193-115">**/out=** `filename`</span></span>|<span data-ttu-id="14193-116">建立具有指定 `filename` 的輸出檔案，而不是在圖形化使用者介面中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="14193-116">Creates an output file with the specified `filename`, rather than displaying the results in a graphical user interface.</span></span>|
|<span data-ttu-id="14193-117">**/rtf**</span><span class="sxs-lookup"><span data-stu-id="14193-117">**/rtf**</span></span>|<span data-ttu-id="14193-118">產生 Rich Text Format (RTF) 格式的輸出。</span><span class="sxs-lookup"><span data-stu-id="14193-118">Produces output in rich text format.</span></span> <span data-ttu-id="14193-119">使用 **/text** 選項時無效。</span><span class="sxs-lookup"><span data-stu-id="14193-119">Invalid with the **/text** option.</span></span>|
|<span data-ttu-id="14193-120">**/text**</span><span class="sxs-lookup"><span data-stu-id="14193-120">**/text**</span></span>|<span data-ttu-id="14193-121">在主控台視窗中顯示結果，而不是在圖形化使用者介面中顯示或做為輸出檔。</span><span class="sxs-lookup"><span data-stu-id="14193-121">Displays the results to the console window, rather than in a graphical user interface or as an output file.</span></span>|
|<span data-ttu-id="14193-122">**/html**</span><span class="sxs-lookup"><span data-stu-id="14193-122">**/html**</span></span>|<span data-ttu-id="14193-123">產生 HTML 格式的輸出。</span><span class="sxs-lookup"><span data-stu-id="14193-123">Produces output in HTML format.</span></span> <span data-ttu-id="14193-124">使用 **/output** 選項時才有效。</span><span class="sxs-lookup"><span data-stu-id="14193-124">Valid with the **/output** option only.</span></span>|
|<span data-ttu-id="14193-125">**/?**</span><span class="sxs-lookup"><span data-stu-id="14193-125">**/?**</span></span>|<span data-ttu-id="14193-126">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="14193-126">Displays the command syntax and options for the tool.</span></span>|

<span data-ttu-id="14193-127">下列其他選項可用於 *.exe*、*.dll* 和 *.winmd* 檔案。</span><span class="sxs-lookup"><span data-stu-id="14193-127">The following additional options are available for *.exe*, *.dll*, and *.winmd* files.</span></span>

| <span data-ttu-id="14193-128">選項</span><span class="sxs-lookup"><span data-stu-id="14193-128">Option</span></span> | <span data-ttu-id="14193-129">描述</span><span class="sxs-lookup"><span data-stu-id="14193-129">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="14193-130">**/bytes**</span><span class="sxs-lookup"><span data-stu-id="14193-130">**/bytes**</span></span>|<span data-ttu-id="14193-131">顯示十六進位格式的實際位元組做為指令註解。</span><span class="sxs-lookup"><span data-stu-id="14193-131">Shows actual bytes, in hexadecimal format, as instruction comments.</span></span>|
|<span data-ttu-id="14193-132">**/caverbal**</span><span class="sxs-lookup"><span data-stu-id="14193-132">**/caverbal**</span></span>|<span data-ttu-id="14193-133">以動詞化格式產生自訂屬性 BLOB。</span><span class="sxs-lookup"><span data-stu-id="14193-133">Produces custom attribute blobs in verbal form.</span></span> <span data-ttu-id="14193-134">預設為二進位格式。</span><span class="sxs-lookup"><span data-stu-id="14193-134">The default is binary form.</span></span>|
|<span data-ttu-id="14193-135">**/linenum**</span><span class="sxs-lookup"><span data-stu-id="14193-135">**/linenum**</span></span>|<span data-ttu-id="14193-136">包含原始程式行的參考。</span><span class="sxs-lookup"><span data-stu-id="14193-136">Includes references to original source lines.</span></span>|
|<span data-ttu-id="14193-137">**/nobar**</span><span class="sxs-lookup"><span data-stu-id="14193-137">**/nobar**</span></span>|<span data-ttu-id="14193-138">隱藏反組譯碼進度指示器快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="14193-138">Suppresses the disassembly progress indicator pop-up window.</span></span>|
|<span data-ttu-id="14193-139">**/noca**</span><span class="sxs-lookup"><span data-stu-id="14193-139">**/noca**</span></span>|<span data-ttu-id="14193-140">隱藏自訂屬性的輸出。</span><span class="sxs-lookup"><span data-stu-id="14193-140">Suppresses the output of custom attributes.</span></span>|
|<span data-ttu-id="14193-141">**/project**</span><span class="sxs-lookup"><span data-stu-id="14193-141">**/project**</span></span>|<span data-ttu-id="14193-142">以對受控程式碼顯示的方式顯示中繼資料，而不採用在原生 Windows 執行階段中顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="14193-142">Displays metadata the way it appears to managed code, instead of the way it appears in the native Windows Runtime.</span></span> <span data-ttu-id="14193-143">如果 `PEfilename` 不是 Windows 中繼資料 (*.winmd*) 檔案，這個選項就沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="14193-143">If `PEfilename` is not a Windows metadata (*.winmd*) file, this option has no effect.</span></span> <span data-ttu-id="14193-144">請參閱[適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="14193-144">See [.NET Framework Support for Windows Store Apps and Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).</span></span>|
|<span data-ttu-id="14193-145">**/pubonly**</span><span class="sxs-lookup"><span data-stu-id="14193-145">**/pubonly**</span></span>|<span data-ttu-id="14193-146">僅反組譯公用類型和成員。</span><span class="sxs-lookup"><span data-stu-id="14193-146">Disassembles only public types and members.</span></span> <span data-ttu-id="14193-147">相當於 **/visibility:PUB**。</span><span class="sxs-lookup"><span data-stu-id="14193-147">Equivalent to **/visibility:PUB**.</span></span>|
|<span data-ttu-id="14193-148">**/quoteallnames**</span><span class="sxs-lookup"><span data-stu-id="14193-148">**/quoteallnames**</span></span>|<span data-ttu-id="14193-149">將所有名稱包含在單引號內。</span><span class="sxs-lookup"><span data-stu-id="14193-149">Includes all names in single quotes.</span></span>|
|<span data-ttu-id="14193-150">**/raweh**</span><span class="sxs-lookup"><span data-stu-id="14193-150">**/raweh**</span></span>|<span data-ttu-id="14193-151">以未經處理格式顯示例外狀況處理子句。</span><span class="sxs-lookup"><span data-stu-id="14193-151">Shows exception handling clauses in raw form.</span></span>|
|<span data-ttu-id="14193-152">**/source**</span><span class="sxs-lookup"><span data-stu-id="14193-152">**/source**</span></span>|<span data-ttu-id="14193-153">將原來的原始程式行顯示成註解。</span><span class="sxs-lookup"><span data-stu-id="14193-153">Shows original source lines as comments.</span></span>|
|<span data-ttu-id="14193-154">**/tokens**</span><span class="sxs-lookup"><span data-stu-id="14193-154">**/tokens**</span></span>|<span data-ttu-id="14193-155">顯示類別和成員的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="14193-155">Shows metadata tokens of classes and members.</span></span>|
|<span data-ttu-id="14193-156">**/visibility:** `vis`[+`vis`...]</span><span class="sxs-lookup"><span data-stu-id="14193-156">**/visibility:** `vis`[+`vis`...]</span></span>|<span data-ttu-id="14193-157">僅反組譯具有所指定可視性的類型或成員。</span><span class="sxs-lookup"><span data-stu-id="14193-157">Disassembles only types or members with the specified visibility.</span></span> <span data-ttu-id="14193-158">以下是 `vis` 的有效值：</span><span class="sxs-lookup"><span data-stu-id="14193-158">The following are valid values for `vis`:</span></span><br /><br /> <span data-ttu-id="14193-159">**PUB**：公開</span><span class="sxs-lookup"><span data-stu-id="14193-159">**PUB** — Public</span></span><br /><br /> <span data-ttu-id="14193-160">**PRI**：私用</span><span class="sxs-lookup"><span data-stu-id="14193-160">**PRI** — Private</span></span><br /><br /> <span data-ttu-id="14193-161">**FAM**：家族</span><span class="sxs-lookup"><span data-stu-id="14193-161">**FAM** — Family</span></span><br /><br /> <span data-ttu-id="14193-162">**ASM**：組件</span><span class="sxs-lookup"><span data-stu-id="14193-162">**ASM** — Assembly</span></span><br /><br /> <span data-ttu-id="14193-163">**FAA**：家族和組件</span><span class="sxs-lookup"><span data-stu-id="14193-163">**FAA** — Family and Assembly</span></span><br /><br /> <span data-ttu-id="14193-164">**FOA**：家族或組件</span><span class="sxs-lookup"><span data-stu-id="14193-164">**FOA** — Family or Assembly</span></span><br /><br /> <span data-ttu-id="14193-165">**PSC**：私用範圍</span><span class="sxs-lookup"><span data-stu-id="14193-165">**PSC** — Private Scope</span></span><br /><br /> <span data-ttu-id="14193-166">如需這些可視性修飾詞的定義，請參閱 <xref:System.Reflection.MethodAttributes> 和 <xref:System.Reflection.TypeAttributes>。</span><span class="sxs-lookup"><span data-stu-id="14193-166">For definitions of these visibility modifiers, see <xref:System.Reflection.MethodAttributes> and <xref:System.Reflection.TypeAttributes>.</span></span>|

<span data-ttu-id="14193-167">下列選項只對檔案或主控台輸出的 *.exe*、 *.dll*和*winmd*檔案有效。</span><span class="sxs-lookup"><span data-stu-id="14193-167">The following options are valid for *.exe*, *.dll*, and *.winmd* files for file or console output only.</span></span>

| <span data-ttu-id="14193-168">選項</span><span class="sxs-lookup"><span data-stu-id="14193-168">Option</span></span> | <span data-ttu-id="14193-169">描述</span><span class="sxs-lookup"><span data-stu-id="14193-169">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="14193-170">**/all**</span><span class="sxs-lookup"><span data-stu-id="14193-170">**/all**</span></span>|<span data-ttu-id="14193-171">指定 **/header**、**/bytes**、**/stats**、**/classlist** 與 **/tokens** 選項的組合。</span><span class="sxs-lookup"><span data-stu-id="14193-171">Specifies a combination of the **/header**, **/bytes**, **/stats**, **/classlist**, and **/tokens** options.</span></span>|
|<span data-ttu-id="14193-172">**/classlist**</span><span class="sxs-lookup"><span data-stu-id="14193-172">**/classlist**</span></span>|<span data-ttu-id="14193-173">包括模組中定義的類別清單。</span><span class="sxs-lookup"><span data-stu-id="14193-173">Includes a list of classes defined in the module.</span></span>|
|<span data-ttu-id="14193-174">**/forward**</span><span class="sxs-lookup"><span data-stu-id="14193-174">**/forward**</span></span>|<span data-ttu-id="14193-175">使用 forward 類別宣告。</span><span class="sxs-lookup"><span data-stu-id="14193-175">Uses forward class declaration.</span></span>|
|<span data-ttu-id="14193-176">**/headers**</span><span class="sxs-lookup"><span data-stu-id="14193-176">**/headers**</span></span>|<span data-ttu-id="14193-177">在輸出中包含檔案標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="14193-177">Includes file header information in the output.</span></span>|
|<span data-ttu-id="14193-178">**/item：** `class`[**::** `member`[`(sig`]]</span><span class="sxs-lookup"><span data-stu-id="14193-178">**/item:** `class`[**::** `member`[`(sig`]]</span></span>|<span data-ttu-id="14193-179">根據提供的引數反組譯下列項目：</span><span class="sxs-lookup"><span data-stu-id="14193-179">Disassembles the following depending upon the argument supplied:</span></span><br /><br /> <span data-ttu-id="14193-180">-   反組譯指定的 `class`。</span><span class="sxs-lookup"><span data-stu-id="14193-180">-   Disassembles the specified `class`.</span></span><br /><span data-ttu-id="14193-181">-   反組譯 `class` 的指定 `member`。</span><span class="sxs-lookup"><span data-stu-id="14193-181">-   Disassembles the specified `member` of the `class`.</span></span><br /><span data-ttu-id="14193-182">-   以指定的簽章 `sig` 反組譯 `class` 的 `member`。</span><span class="sxs-lookup"><span data-stu-id="14193-182">-   Disassembles the `member` of the `class` with the specified signature `sig`.</span></span> <span data-ttu-id="14193-183">`sig` 的格式為：</span><span class="sxs-lookup"><span data-stu-id="14193-183">The format of `sig` is:</span></span><br />     <span data-ttu-id="14193-184">[`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)</span><span class="sxs-lookup"><span data-stu-id="14193-184">[`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)</span></span><br />     <span data-ttu-id="14193-185">**注意**在 .NET Framework 版本1.0 和1.1 中， `sig` 後面必須接著右括弧： `(sig)` 。</span><span class="sxs-lookup"><span data-stu-id="14193-185">**Note** In the .NET Framework versions 1.0 and 1.1, `sig` must be followed by a closing parenthesis: `(sig)`.</span></span> <span data-ttu-id="14193-186">從 Net Framework 2.0 開始，必須省略右括號：`(sig`。</span><span class="sxs-lookup"><span data-stu-id="14193-186">Starting with the Net Framework 2.0 the closing parenthesis must be omitted: `(sig`.</span></span>|
|<span data-ttu-id="14193-187">**/noil**</span><span class="sxs-lookup"><span data-stu-id="14193-187">**/noil**</span></span>|<span data-ttu-id="14193-188">隱藏 IL 組件的程式碼輸出。</span><span class="sxs-lookup"><span data-stu-id="14193-188">Suppresses IL assembly code output.</span></span>|
|<span data-ttu-id="14193-189">**/stats**</span><span class="sxs-lookup"><span data-stu-id="14193-189">**/stats**</span></span>|<span data-ttu-id="14193-190">包含影像中的統計資料。</span><span class="sxs-lookup"><span data-stu-id="14193-190">Includes statistics on the image.</span></span>|
|<span data-ttu-id="14193-191">**/typelist**</span><span class="sxs-lookup"><span data-stu-id="14193-191">**/typelist**</span></span>|<span data-ttu-id="14193-192">產生完整的類型清單，以便在反覆存取時保留類型順序。</span><span class="sxs-lookup"><span data-stu-id="14193-192">Produces the full list of types, to preserve type ordering in a round trip.</span></span>|
|<span data-ttu-id="14193-193">**/unicode**</span><span class="sxs-lookup"><span data-stu-id="14193-193">**/unicode**</span></span>|<span data-ttu-id="14193-194">使用 Unicode 編碼輸出。</span><span class="sxs-lookup"><span data-stu-id="14193-194">Uses Unicode encoding for the output.</span></span>|
|<span data-ttu-id="14193-195">**/utf8**</span><span class="sxs-lookup"><span data-stu-id="14193-195">**/utf8**</span></span>|<span data-ttu-id="14193-196">使用 UTF-8 編碼輸出。</span><span class="sxs-lookup"><span data-stu-id="14193-196">Uses UTF-8 encoding for the output.</span></span> <span data-ttu-id="14193-197">預設值為 ANSI。</span><span class="sxs-lookup"><span data-stu-id="14193-197">ANSI is the default.</span></span>|

<span data-ttu-id="14193-198">下列選項僅適用于檔案或主控台輸出的 *.exe*、 *.dll*、 *.obj*、 *.lib*和*winmd*檔案。</span><span class="sxs-lookup"><span data-stu-id="14193-198">The following options are valid for *.exe*, *.dll*, *.obj*, *.lib*, and *.winmd* files for file or console output only.</span></span>

| <span data-ttu-id="14193-199">選項</span><span class="sxs-lookup"><span data-stu-id="14193-199">Option</span></span> | <span data-ttu-id="14193-200">描述</span><span class="sxs-lookup"><span data-stu-id="14193-200">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="14193-201">**/metadata**[= `specifier` ]</span><span class="sxs-lookup"><span data-stu-id="14193-201">**/metadata**[=`specifier`]</span></span>|<span data-ttu-id="14193-202">顯示中繼資料，其中 `specifier` 是：</span><span class="sxs-lookup"><span data-stu-id="14193-202">Shows metadata, where `specifier` is:</span></span><br /><br /> <span data-ttu-id="14193-203">**MDHEADER**：顯示中繼資料的標頭資訊和大小。</span><span class="sxs-lookup"><span data-stu-id="14193-203">**MDHEADER** — Show the metadata header information and sizes.</span></span><br /><br /> <span data-ttu-id="14193-204">**HEX**：使用十六進位和文字顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="14193-204">**HEX** — Show information in hex as well as in words.</span></span><br /><br /> <span data-ttu-id="14193-205">**CSV**：顯示記錄計數和堆積大小。</span><span class="sxs-lookup"><span data-stu-id="14193-205">**CSV** — Show the record counts and heap sizes.</span></span><br /><br /> <span data-ttu-id="14193-206">**UNREX**：顯示無法解析的外部符號。</span><span class="sxs-lookup"><span data-stu-id="14193-206">**UNREX** — Show unresolved externals.</span></span><br /><br /> <span data-ttu-id="14193-207">**SCHEMA**：顯示中繼資料的標頭和結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="14193-207">**SCHEMA** — Show the metadata header and schema information.</span></span><br /><br /> <span data-ttu-id="14193-208">**RAW**：顯示原始中繼資料表。</span><span class="sxs-lookup"><span data-stu-id="14193-208">**RAW** — Show the raw metadata tables.</span></span><br /><br /> <span data-ttu-id="14193-209">**HEAPS**：顯示原始的堆積。</span><span class="sxs-lookup"><span data-stu-id="14193-209">**HEAPS** — Show the raw heaps.</span></span><br /><br /> <span data-ttu-id="14193-210">**VALIDATE**：驗證中繼資料的一致性。</span><span class="sxs-lookup"><span data-stu-id="14193-210">**VALIDATE** — Validate the consistency of the metadata.</span></span><br /><br /> <span data-ttu-id="14193-211">您可以多次指定 **/metadata**，每次使用不同的 `specifier` 值。</span><span class="sxs-lookup"><span data-stu-id="14193-211">You can specify **/metadata** multiple times, with different values for `specifier`.</span></span>|

<span data-ttu-id="14193-212">下列選項只對檔案或主控台輸出的 *.lib*檔案有效。</span><span class="sxs-lookup"><span data-stu-id="14193-212">The following options are valid for *.lib* files for file or console output only.</span></span>

| <span data-ttu-id="14193-213">選項</span><span class="sxs-lookup"><span data-stu-id="14193-213">Option</span></span> | <span data-ttu-id="14193-214">描述</span><span class="sxs-lookup"><span data-stu-id="14193-214">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="14193-215">**/objectfile**=`filename`</span><span class="sxs-lookup"><span data-stu-id="14193-215">**/objectfile**=`filename`</span></span>|<span data-ttu-id="14193-216">顯示所指定程式庫中單一物件檔案的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="14193-216">Shows the metadata of a single object file in the specified library.</span></span>|

> [!NOTE]
> <span data-ttu-id="14193-217">*Ildasm.exe* 的所有選項都不區分大小寫，並以前三個字母來辨識。</span><span class="sxs-lookup"><span data-stu-id="14193-217">All options for *Ildasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="14193-218">例如，**/quo** 相當於 **/quoteallnames**。</span><span class="sxs-lookup"><span data-stu-id="14193-218">For example, **/quo** is equivalent to **/quoteallnames**.</span></span> <span data-ttu-id="14193-219">指定引數的選項可以接受冒號 (:) 或等號 (=) 做為選項與引數之間的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="14193-219">Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="14193-220">例如，**/output: <檔案名稱>** \*\* 相當於 **/output= <檔案名稱>** \*\*。</span><span class="sxs-lookup"><span data-stu-id="14193-220">For example, **/output:** *filename* is equivalent to **/output=** *filename*.</span></span>

## <a name="remarks"></a><span data-ttu-id="14193-221">備註</span><span class="sxs-lookup"><span data-stu-id="14193-221">Remarks</span></span>

<span data-ttu-id="14193-222">*Ildasm.exe*只會在磁片上的 PE 檔案上運作。</span><span class="sxs-lookup"><span data-stu-id="14193-222">*Ildasm.exe* only operates on PE files on disk.</span></span> <span data-ttu-id="14193-223">它無法在安裝於全域組件快取中的檔案上作業。</span><span class="sxs-lookup"><span data-stu-id="14193-223">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="14193-224">*Ildasm.exe* 所產生的文字檔可以用作 IL 組譯工具 (*Ilasm.exe*) 的輸入。</span><span class="sxs-lookup"><span data-stu-id="14193-224">The text file produced by *Ildasm.exe* can be used as input to the IL Assembler (*Ilasm.exe*).</span></span> <span data-ttu-id="14193-225">這非常有用，例如在不支援所有執行階段中繼資料屬性的程式語言中編譯程式碼時。</span><span class="sxs-lookup"><span data-stu-id="14193-225">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="14193-226">在編譯器代碼並透過*Ildasm.exe*執行其輸出之後，可以手動編輯產生的 IL 文字檔來加入遺漏的屬性。</span><span class="sxs-lookup"><span data-stu-id="14193-226">After compiling the code and running its output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="14193-227">然後可以透過 IL 組譯工具執行這個文字檔來產生最後的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="14193-227">You can then run this text file through the IL Assembler to produce a final executable file.</span></span>

> [!NOTE]
> <span data-ttu-id="14193-228">目前您無法將這項技術用於包含內嵌機器碼的 PE 檔 (例如，由 Visual C++ 所產生的 PE 檔)。</span><span class="sxs-lookup"><span data-stu-id="14193-228">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>  

<span data-ttu-id="14193-229">您可以使用 IL 反組譯工具中的預設 GUI，檢視階層樹狀檢視中任何現有 PE 檔的中繼資料和反組譯碼。</span><span class="sxs-lookup"><span data-stu-id="14193-229">You can use the default GUI in the IL Disassembler to view the metadata and disassembled code of any existing PE file in a hierarchical tree view.</span></span> <span data-ttu-id="14193-230">若要使用 GUI，請在命令列鍵入 **ildasm**，但不提供 *PEfilename* 引數或任何選項。</span><span class="sxs-lookup"><span data-stu-id="14193-230">To use the GUI, type **ildasm** at the command line without supplying the *PEfilename* argument or any options.</span></span> <span data-ttu-id="14193-231">從 [檔案 **] 功能表中**，您可以流覽至您想要載入*Ildasm.exe*的 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="14193-231">From the **File** menu, you can navigate to the PE file that you want to load into *Ildasm.exe*.</span></span> <span data-ttu-id="14193-232">若要儲存針對所選取 PE 顯示的中繼資料和反組譯程式碼，請選取 [檔案]\*\*\*\* 功能表中的 [傾印]\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="14193-232">To save the metadata and disassembled code displayed for the selected PE, select the **Dump** command from the **File** menu.</span></span> <span data-ttu-id="14193-233">若只要儲存階層樹狀檢閱，請從 [檔案]\*\*\*\* 功能表中選取 [傾印樹狀檢視]\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="14193-233">To save the hierarchical tree view only, select the **Dump Treeview** command from the **File** menu.</span></span> <span data-ttu-id="14193-234">如需將檔案載入 *Ildasm.exe* 及解譯輸出的詳細指南，請參閱位於 Windows SDK 隨附 [Samples] 資料夾中的 *Ildasm.exe* 教學課程。</span><span class="sxs-lookup"><span data-stu-id="14193-234">For a detailed guide to loading a file into *Ildasm.exe* and interpreting the output, see the *Ildasm.exe* Tutorial, located in the Samples folder that ships with the Windows SDK.</span></span>

<span data-ttu-id="14193-235">如果您提供*Ildasm.exe*包含內嵌資源的*PEfilename*引數，此工具會產生多個輸出檔案：包含 IL 程式碼的文字檔，以及針對每個內嵌的 managed 資源，使用來自中繼資料的資源名稱所產生的 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="14193-235">If you provide *Ildasm.exe* with a *PEfilename* argument that contains embedded resources, the tool produces multiple output files: a text file that contains IL code and, for each embedded managed resource, a .resources file produced using the resource's name from metadata.</span></span> <span data-ttu-id="14193-236">如果 Unmanaged 資源內嵌於 *PEfilename*，**/output** 選項就會使用為 IL 指定的檔案名稱來產生 .res 檔案。</span><span class="sxs-lookup"><span data-stu-id="14193-236">If an unmanaged resource is embedded in *PEfilename*, a .res file is produced using the filename specified for IL output by the **/output** option.</span></span>

> [!NOTE]
> <span data-ttu-id="14193-237">*Ildasm.exe*只會顯示 *.obj*和 *.lib*輸入檔的中繼資料描述。</span><span class="sxs-lookup"><span data-stu-id="14193-237">*Ildasm.exe* shows only metadata descriptions for *.obj* and *.lib* input files.</span></span> <span data-ttu-id="14193-238">這些檔案類型的 IL 程式碼不會進行反組譯。</span><span class="sxs-lookup"><span data-stu-id="14193-238">IL code for these file types is not disassembled.</span></span>

<span data-ttu-id="14193-239">您可以透過 an.exe 或 *.dll*檔案執行*Ildasm.exe* ，以判斷檔案是否受管理。</span><span class="sxs-lookup"><span data-stu-id="14193-239">You can run *Ildasm.exe* over an.exe or *.dll* file to determine whether the file is managed.</span></span> <span data-ttu-id="14193-240">如果檔案不是 Managed，工具便會顯示一則訊息，說明該檔案沒有有效的通用語言執行平台標頭而且無法進行反組譯。</span><span class="sxs-lookup"><span data-stu-id="14193-240">If the file is not managed, the tool displays a message stating that the file has no valid common language runtime header and cannot be disassembled.</span></span> <span data-ttu-id="14193-241">如果檔案是 Managed，工具就會成功執行。</span><span class="sxs-lookup"><span data-stu-id="14193-241">If the file is managed, the tool runs successfully.</span></span>

## <a name="version-information"></a><span data-ttu-id="14193-242">版本資訊</span><span class="sxs-lookup"><span data-stu-id="14193-242">Version Information</span></span>

<span data-ttu-id="14193-243">從 .NET Framework 4.5 開始，*Ildasm.exe* 會藉由顯示原始二進位內容來處理無法辨認的封送處理 BLOB (二進位大型物件)。</span><span class="sxs-lookup"><span data-stu-id="14193-243">Starting with the .NET Framework 4.5, *Ildasm.exe* handles an unrecognized marshal BLOB (binary large object) by displaying the raw binary content.</span></span> <span data-ttu-id="14193-244">例如，下列程式碼將示範如何顯示 C# 程式所產生的封送處理 BLOB：</span><span class="sxs-lookup"><span data-stu-id="14193-244">For example, the following code shows how a marshal BLOB generated by a C# program is displayed:</span></span>

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

<span data-ttu-id="14193-245">從 .NET Framework 4.5 開始，*Ildasm.exe* 會顯示套用至介面實作的屬性，如 *Ildasm.exe* 輸出的下列摘要所示：</span><span class="sxs-lookup"><span data-stu-id="14193-245">Starting with the .NET Framework 4.5, *Ildasm.exe* displays attributes that are applied to interface implementations, as shown in the following excerpt from *Ildasm.exe* output:</span></span>

```il
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

## <a name="examples"></a><span data-ttu-id="14193-246">範例</span><span class="sxs-lookup"><span data-stu-id="14193-246">Examples</span></span>

<span data-ttu-id="14193-247">下列命令會讓 PE 檔的中繼資料和反組譯程式碼 `MyHello.exe` 顯示在*Ildasm.exe*預設 GUI 中。</span><span class="sxs-lookup"><span data-stu-id="14193-247">The following command causes the metadata and disassembled code for the PE file `MyHello.exe` to display in the *Ildasm.exe* default GUI.</span></span>

```console
ildasm myHello.exe
```

<span data-ttu-id="14193-248">下列命令會反組譯 `MyFile.exe` 檔案，並將產生的 IL 組譯工具文字儲存到 *MyFile.il* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="14193-248">The following command disassembles the file `MyFile.exe` and stores the resulting IL Assembler text in the file *MyFile.il*.</span></span>

```console
ildasm MyFile.exe /output:MyFile.il
```

<span data-ttu-id="14193-249">下列命令會反組譯 `MyFile.exe` 檔案，並在主控台視窗中顯示產生的 IL 組譯工具文字。</span><span class="sxs-lookup"><span data-stu-id="14193-249">The following command disassembles the file `MyFile.exe` and displays the resulting IL Assembler text to the console window.</span></span>

```console
ildasm MyFile.exe /text
```

<span data-ttu-id="14193-250">如果檔案 `MyApp.exe` 包含內嵌的 Managed 和 Unmanaged 資源，則下列命令會產生四個檔案：*MyApp.il*、*MyApp.res*、*Icons.resources*和 *Message.resources*：</span><span class="sxs-lookup"><span data-stu-id="14193-250">If the file `MyApp.exe` contains embedded managed and unmanaged resources, the following command produces four files: *MyApp.il*, *MyApp.res*, *Icons.resources*, and *Message.resources*:</span></span>

```console
ildasm MyApp.exe /output:MyApp.il
```

<span data-ttu-id="14193-251">下列命令會反組譯 `MyFile.exe` 中 `MyClass` 類別內的 `MyMethod` 方法，並且在主控台視窗中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="14193-251">The following command disassembles the method `MyMethod` within the class `MyClass` in `MyFile.exe` and displays the output to the console window.</span></span>

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

<span data-ttu-id="14193-252">在上述範例中，可能有數個名為 `MyMethod` 但具有不同簽章的方法。</span><span class="sxs-lookup"><span data-stu-id="14193-252">In the previous example, there could be several methods named `MyMethod` with different signatures.</span></span> <span data-ttu-id="14193-253">下列命令會反組譯傳回型別為 **void** 以及參數類型為 **int32** 和 **string** 的執行個體方法 `MyMethod`。</span><span class="sxs-lookup"><span data-stu-id="14193-253">The following command disassembles the instance method `MyMethod` with the return type of **void** and the parameter types **int32** and **string**.</span></span>

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> <span data-ttu-id="14193-254">在 .NET Framework 1.0 和 1.1 版中，方法名稱後的左括號必須與簽章後的右括號保持對稱：`MyMethod(instance void(int32))`。</span><span class="sxs-lookup"><span data-stu-id="14193-254">In the .NET Framework versions 1.0 and 1.1, the left parenthesis that follows the method name must be balanced by a right parenthesis after the signature: `MyMethod(instance void(int32))`.</span></span> <span data-ttu-id="14193-255">從 .NET Framework 2.0 開始，必須省略右括號：`MyMethod(instance void(int32)`。</span><span class="sxs-lookup"><span data-stu-id="14193-255">Starting with the .NET Framework 2.0 the closing parenthesis must be omitted: `MyMethod(instance void(int32)`.</span></span>

<span data-ttu-id="14193-256">若要擷取 `static` 方法 (在 Visual Basic 中為 `Shared` 方法)，請省略關鍵字 `instance`。</span><span class="sxs-lookup"><span data-stu-id="14193-256">To retrieve a `static` method (`Shared` method in Visual Basic), omit the keyword `instance`.</span></span> <span data-ttu-id="14193-257">不是 `int32` 和 `string` 等基本類型 (Primitive Type) 的類別類型，都必須包含命名空間，而且前面必須加上關鍵字 `class`。</span><span class="sxs-lookup"><span data-stu-id="14193-257">Class types that are not primitive types like `int32` and `string` must include the namespace and must be preceded by the keyword `class`.</span></span> <span data-ttu-id="14193-258">外部類型的前面必須加上以方括號括住的程式庫名稱。</span><span class="sxs-lookup"><span data-stu-id="14193-258">External types must be preceded by the library name in square brackets.</span></span> <span data-ttu-id="14193-259">下列命令會反組譯名為 `MyMethod` 的靜態方法，該靜態方法具有一個 <xref:System.AppDomain> 類型的參數，而且傳回類型為 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="14193-259">The following command disassembles a static method named `MyMethod` that has one parameter of type <xref:System.AppDomain> and has a return type of <xref:System.AppDomain>.</span></span>

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

<span data-ttu-id="14193-260">巢狀類型的前面必須加上它的包含類別，並以正斜線分隔。</span><span class="sxs-lookup"><span data-stu-id="14193-260">A nested type must be preceded by its containing class, delimited by a forward slash.</span></span> <span data-ttu-id="14193-261">例如，如果 `MyNamespace.MyClass` 類別包含名為 `NestedClass` 的巢狀類別，則該巢狀類別的識別方式如下：`class MyNamespace.MyClass/NestedClass`。</span><span class="sxs-lookup"><span data-stu-id="14193-261">For example, if the `MyNamespace.MyClass` class contains a nested class named `NestedClass`, the nested class is identified as follows: `class MyNamespace.MyClass/NestedClass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="14193-262">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14193-262">See also</span></span>

- [<span data-ttu-id="14193-263">工具</span><span class="sxs-lookup"><span data-stu-id="14193-263">Tools</span></span>](index.md)
- [<span data-ttu-id="14193-264">Ilasm.exe （IL 組譯工具）</span><span class="sxs-lookup"><span data-stu-id="14193-264">Ilasm.exe (IL Assembler)</span></span>](ilasm-exe-il-assembler.md)
- [<span data-ttu-id="14193-265">Managed 執行進程</span><span class="sxs-lookup"><span data-stu-id="14193-265">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="14193-266">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="14193-266">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
