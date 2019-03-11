---
title: Peverify.exe (PEVerify 工具)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35ff03eb830a02b05dd128da4c072a8c2c918921
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501496"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="2841f-102">Peverify.exe (PEVerify 工具)</span><span class="sxs-lookup"><span data-stu-id="2841f-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="2841f-103">PEVerify 工具可以協助像是編譯器撰寫者、指令碼引擎開發人員等產生 Microsoft Intermediate Language (MSIL) 的開發人員，判斷其 MSIL 程式碼和相關聯的中繼資料是否符合類型安全需求。</span><span class="sxs-lookup"><span data-stu-id="2841f-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="2841f-104">只有在避免使用某些語言建構時，某些編譯器才會產生可驗證的類型安全程式碼。</span><span class="sxs-lookup"><span data-stu-id="2841f-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="2841f-105">如果您是使用這類編譯器的開發人員，可能會想要驗證您並未損及程式碼的類型安全。</span><span class="sxs-lookup"><span data-stu-id="2841f-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="2841f-106">在這種情況下，您可以在檔案上執行 PEVerify 工具來檢查 MSIL 和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2841f-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="2841f-107">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="2841f-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2841f-108">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="2841f-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="2841f-109">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="2841f-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="2841f-110">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="2841f-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2841f-111">語法</span><span class="sxs-lookup"><span data-stu-id="2841f-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="2841f-112">參數</span><span class="sxs-lookup"><span data-stu-id="2841f-112">Parameters</span></span>  
  
|<span data-ttu-id="2841f-113">引數</span><span class="sxs-lookup"><span data-stu-id="2841f-113">Argument</span></span>|<span data-ttu-id="2841f-114">說明</span><span class="sxs-lookup"><span data-stu-id="2841f-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2841f-115">*filename*</span><span class="sxs-lookup"><span data-stu-id="2841f-115">*filename*</span></span>|<span data-ttu-id="2841f-116">要檢查其 MSIL 和中繼資料的可攜式執行檔 (PE)。</span><span class="sxs-lookup"><span data-stu-id="2841f-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="2841f-117">選項</span><span class="sxs-lookup"><span data-stu-id="2841f-117">Option</span></span>|<span data-ttu-id="2841f-118">說明</span><span class="sxs-lookup"><span data-stu-id="2841f-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2841f-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="2841f-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="2841f-120">發生 *maxErrorCount* 錯誤之後中止驗證。</span><span class="sxs-lookup"><span data-stu-id="2841f-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="2841f-121">.NET Framework 2.0 (含) 以後版本不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="2841f-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="2841f-122">**/clock**</span><span class="sxs-lookup"><span data-stu-id="2841f-122">**/clock**</span></span>|<span data-ttu-id="2841f-123">以毫秒為單位測量並報告下列驗證時間：</span><span class="sxs-lookup"><span data-stu-id="2841f-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="2841f-124">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="2841f-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="2841f-125">中繼資料驗證週期</span><span class="sxs-lookup"><span data-stu-id="2841f-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="2841f-126">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="2841f-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="2841f-127">單純中繼資料驗證</span><span class="sxs-lookup"><span data-stu-id="2841f-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="2841f-128">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="2841f-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="2841f-129">Microsoft Intermediate Language (MSIL) 驗證週期</span><span class="sxs-lookup"><span data-stu-id="2841f-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="2841f-130">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="2841f-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="2841f-131">單純 MSIL 驗證</span><span class="sxs-lookup"><span data-stu-id="2841f-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="2841f-132">**MD Val. cycle** 和 **IL Ver. cycle** 時間包括了執行必要的啟始和關閉程序所需的時間。</span><span class="sxs-lookup"><span data-stu-id="2841f-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="2841f-133">**MD Val. pure** 和 **IL Ver pure** 時間則是反映純粹執行驗證所需的時間。</span><span class="sxs-lookup"><span data-stu-id="2841f-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="2841f-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="2841f-134">**/help**</span></span>|<span data-ttu-id="2841f-135">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="2841f-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="2841f-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="2841f-136">**/hresult**</span></span>|<span data-ttu-id="2841f-137">以十六進位格式顯示錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2841f-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="2841f-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="2841f-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="2841f-139">忽略指定的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2841f-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="2841f-140">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="2841f-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="2841f-141">忽略指定的回應檔中列出的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2841f-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="2841f-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="2841f-142">**/il**</span></span>|<span data-ttu-id="2841f-143">針對 *filename* 所指定組件中實作的方法，執行 MSIL 型別安全驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="2841f-144">除非您指定 **/quiet** 選項，否則此工具會針對每個找到的問題傳回詳細描述。</span><span class="sxs-lookup"><span data-stu-id="2841f-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="2841f-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="2841f-145">**/md**</span></span>|<span data-ttu-id="2841f-146">在 *filename* 所指定的組件上，執行中繼資料驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="2841f-147">這會逐步檢查檔案內的所有中繼資料結構，並報告遇到的所有驗證問題。</span><span class="sxs-lookup"><span data-stu-id="2841f-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="2841f-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="2841f-148">**/nologo**</span></span>|<span data-ttu-id="2841f-149">不顯示產品版本和著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="2841f-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="2841f-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="2841f-150">**/nosymbols**</span></span>|<span data-ttu-id="2841f-151">在 .NET Framework 2.0 版中，隱藏回溯相容性的行號。</span><span class="sxs-lookup"><span data-stu-id="2841f-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="2841f-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="2841f-152">**/quiet**</span></span>|<span data-ttu-id="2841f-153">指定無訊息模式，隱藏驗證問題報告的輸出。</span><span class="sxs-lookup"><span data-stu-id="2841f-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="2841f-154">Peverify.exe 仍會報告檔案是否為類型安全，但不會報告阻礙類型安全驗證之問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="2841f-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="2841f-155">只驗證透明方法。</span><span class="sxs-lookup"><span data-stu-id="2841f-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="2841f-156">**/unique**</span><span class="sxs-lookup"><span data-stu-id="2841f-156">**/unique**</span></span>|<span data-ttu-id="2841f-157">忽略重複的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2841f-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="2841f-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="2841f-158">**/verbose**</span></span>|<span data-ttu-id="2841f-159">在 .NET Framework 2.0 版中，使用 MSIL 驗證訊息顯示其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2841f-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="2841f-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="2841f-160">**/?**</span></span>|<span data-ttu-id="2841f-161">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="2841f-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2841f-162">備註</span><span class="sxs-lookup"><span data-stu-id="2841f-162">Remarks</span></span>  
 <span data-ttu-id="2841f-163">通用語言執行平台透過以類型安全的方式執行應用程式程式碼，協助強制執行安全性和隔離機制。</span><span class="sxs-lookup"><span data-stu-id="2841f-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="2841f-164">正常情況下，不是[可驗證型別安全](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)的程式碼無法執行，但是您可以設定安全性原則，讓受信任但無法驗證的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="2841f-164">Normally, code that is not [verifiably type safe](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="2841f-165">如果 **/md** 和 **/il** 兩個選項都未指定，則 Peverify.exe 會執行這兩種檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="2841f-166">Peverify.exe 會先執行 **/md** 檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="2841f-167">如果沒有任何錯誤，則會執行 **/il** 檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="2841f-168">如果您同時指定 **/md** 和 **/il**，則即使中繼資料有錯誤，還是會執行 **/il** 檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="2841f-169">因此，如果中繼資料沒有錯誤，**peverify** *filename* 就相當於 **peverify** *filename* **/md** **/il**。</span><span class="sxs-lookup"><span data-stu-id="2841f-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="2841f-170">Peverify.exe 會依據資料流分析加上有效的中繼資料上數百項規則的清單，執行全面性的 MSIL 驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="2841f-171">如需 Peverify.exe 所執行檢查的詳細資訊，請參閱 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 的 [Tools Developers Guide] 資料夾中的＜中繼資料驗證規格＞和＜MSIL 指令集規格＞。</span><span class="sxs-lookup"><span data-stu-id="2841f-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="2841f-172">請注意，.NET Framework 2.0 版 (含) 以後版本支援傳回使用下列 MSIL 指令指定的可驗證 `byref`：`dup`、`ldsflda`、`ldflda`、`ldelema`、`call` 和 `unbox`。</span><span class="sxs-lookup"><span data-stu-id="2841f-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2841f-173">範例</span><span class="sxs-lookup"><span data-stu-id="2841f-173">Examples</span></span>  
 <span data-ttu-id="2841f-174">下列命令會對 `myAssembly.exe` 組件中實作的方法，執行中繼資料驗證檢查和 MSIL 類型安全驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="2841f-175">成功完成上述要求之後，Peverify.exe 會顯示下列訊息。</span><span class="sxs-lookup"><span data-stu-id="2841f-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="2841f-176">下列命令會對 `myAssembly.exe` 組件中實作的方法，執行中繼資料驗證檢查和 MSIL 類型安全驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="2841f-177">工具會顯示執行這些檢查所需的時間。</span><span class="sxs-lookup"><span data-stu-id="2841f-177">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="2841f-178">成功完成上述要求之後，Peverify.exe 會顯示下列訊息。</span><span class="sxs-lookup"><span data-stu-id="2841f-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="2841f-179">下列命令會對 `myAssembly.exe` 組件中實作的方法，執行中繼資料驗證檢查和 MSIL 類型安全驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="2841f-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="2841f-180">不過，Peverify.exe 會在達到最大錯誤計數 100 時停止。</span><span class="sxs-lookup"><span data-stu-id="2841f-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="2841f-181">工具也會忽略指定的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2841f-181">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="2841f-182">下列命令會產生與上面的前一個範例相同的結果，但是會指定回應檔 `ignoreErrors.rsp` 中要忽略的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2841f-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="2841f-183">回應檔可包含逗號分隔的錯誤碼清單。</span><span class="sxs-lookup"><span data-stu-id="2841f-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="2841f-184">或者，回應檔可以透過每行一個錯誤碼的方式格式化。</span><span class="sxs-lookup"><span data-stu-id="2841f-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="2841f-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2841f-185">See also</span></span>
- [<span data-ttu-id="2841f-186">工具</span><span class="sxs-lookup"><span data-stu-id="2841f-186">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="2841f-187">撰寫可驗證的型別安全程式碼</span><span class="sxs-lookup"><span data-stu-id="2841f-187">Writing Verifiably Type-Safe Code</span></span>](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="2841f-188">型別安全和安全性</span><span class="sxs-lookup"><span data-stu-id="2841f-188">Type Safety and Security</span></span>](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="2841f-189">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="2841f-189">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
