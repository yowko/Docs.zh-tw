---
title: "依分類列出 Visual Basic 編譯器選項 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ae85d1ac5cf2bff05df25cf0cfc623f6266063b4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-compiler-options-listed-by-category"></a><span data-ttu-id="cc3c5-102">依分類列出 Visual Basic 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-102">Visual Basic Compiler Options Listed by Category</span></span>
<span data-ttu-id="cc3c5-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 命令列編譯器可作為從 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 編譯程式的替代方法。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] command-line compiler is provided as an alternative to compiling programs from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] integrated development environment (IDE).</span></span> <span data-ttu-id="cc3c5-104">以下是依功能分類排序的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 命令列編譯器選項清單。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-104">The following is a list of the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] command-line compiler options sorted by functional category.</span></span>  
  
## <a name="compiler-output"></a><span data-ttu-id="cc3c5-105">編譯器輸出</span><span class="sxs-lookup"><span data-stu-id="cc3c5-105">Compiler Output</span></span>  
  
|<span data-ttu-id="cc3c5-106">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-106">Option</span></span>|<span data-ttu-id="cc3c5-107">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-107">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-108">/nologo</span><span class="sxs-lookup"><span data-stu-id="cc3c5-108">/nologo</span></span>](../../../visual-basic/reference/command-line-compiler/nologo.md)|<span data-ttu-id="cc3c5-109">隱藏編譯器橫幅資訊。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-109">Suppresses compiler banner information.</span></span>|  
|[<span data-ttu-id="cc3c5-110">/utf8output</span><span class="sxs-lookup"><span data-stu-id="cc3c5-110">/utf8output</span></span>](../../../visual-basic/reference/command-line-compiler/utf8output.md)|<span data-ttu-id="cc3c5-111">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-111">Displays compiler output using UTF-8 encoding.</span></span>|  
|[<span data-ttu-id="cc3c5-112">/verbose</span><span class="sxs-lookup"><span data-stu-id="cc3c5-112">/verbose</span></span>](../../../visual-basic/reference/command-line-compiler/verbose.md)|<span data-ttu-id="cc3c5-113">在編譯期間輸出額外資訊。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-113">Outputs extra information during compilation.</span></span>|  
|`/modulename:<string>`|<span data-ttu-id="cc3c5-114">指定來源模組的名稱</span><span class="sxs-lookup"><span data-stu-id="cc3c5-114">Specify the name of the source module</span></span>|  
|[<span data-ttu-id="cc3c5-115">/preferreduilang</span><span class="sxs-lookup"><span data-stu-id="cc3c5-115">/preferreduilang</span></span>](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|<span data-ttu-id="cc3c5-116">指定編譯器輸出的語言。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-116">Specify a language for compiler output.</span></span>|  
  
## <a name="optimization"></a><span data-ttu-id="cc3c5-117">最佳化</span><span class="sxs-lookup"><span data-stu-id="cc3c5-117">Optimization</span></span>  
  
|<span data-ttu-id="cc3c5-118">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-118">Option</span></span>|<span data-ttu-id="cc3c5-119">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-119">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-120">/filealign</span><span class="sxs-lookup"><span data-stu-id="cc3c5-120">/filealign</span></span>](../../../visual-basic/reference/command-line-compiler/filealign.md)|<span data-ttu-id="cc3c5-121">指定要對齊輸出檔案區段的位置。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-121">Specifies where to align the sections of the output file.</span></span>|  
|[<span data-ttu-id="cc3c5-122">/optimize</span><span class="sxs-lookup"><span data-stu-id="cc3c5-122">/optimize</span></span>](../../../visual-basic/reference/command-line-compiler/optimize.md)|<span data-ttu-id="cc3c5-123">啟用/停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-123">Enables/disables optimizations.</span></span>|  
  
## <a name="output-files"></a><span data-ttu-id="cc3c5-124">輸出檔</span><span class="sxs-lookup"><span data-stu-id="cc3c5-124">Output Files</span></span>  
  
|<span data-ttu-id="cc3c5-125">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-125">Option</span></span>|<span data-ttu-id="cc3c5-126">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-126">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-127">/doc</span><span class="sxs-lookup"><span data-stu-id="cc3c5-127">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)|<span data-ttu-id="cc3c5-128">將文件註解處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-128">Process documentation comments to an XML file.</span></span>|  
|[<span data-ttu-id="cc3c5-129">/netcf</span><span class="sxs-lookup"><span data-stu-id="cc3c5-129">/netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)|<span data-ttu-id="cc3c5-130">設定要以 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] 為目標的編譯器。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-130">Sets the compiler to target the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>|  
|[<span data-ttu-id="cc3c5-131">/out</span><span class="sxs-lookup"><span data-stu-id="cc3c5-131">/out</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)|<span data-ttu-id="cc3c5-132">指定輸出檔。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-132">Specifies an output file.</span></span>|  
|[<span data-ttu-id="cc3c5-133">/target</span><span class="sxs-lookup"><span data-stu-id="cc3c5-133">/target</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)|<span data-ttu-id="cc3c5-134">指定輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-134">Specifies the format of the output.</span></span>|  
  
## <a name="net-assemblies"></a><span data-ttu-id="cc3c5-135">.NET 組件</span><span class="sxs-lookup"><span data-stu-id="cc3c5-135">.NET Assemblies</span></span>  
  
|<span data-ttu-id="cc3c5-136">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-136">Option</span></span>|<span data-ttu-id="cc3c5-137">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-137">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-138">/addmodule</span><span class="sxs-lookup"><span data-stu-id="cc3c5-138">/addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)|<span data-ttu-id="cc3c5-139">讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-139">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>|  
|[<span data-ttu-id="cc3c5-140">/delaysign</span><span class="sxs-lookup"><span data-stu-id="cc3c5-140">/delaysign</span></span>](../../../visual-basic/reference/command-line-compiler/delaysign.md)|<span data-ttu-id="cc3c5-141">指定將要完整簽署還是部分簽署組件。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-141">Specifies whether the assembly will be fully or partially signed.</span></span>|  
|[<span data-ttu-id="cc3c5-142">/imports</span><span class="sxs-lookup"><span data-stu-id="cc3c5-142">/imports</span></span>](../../../visual-basic/reference/command-line-compiler/imports.md)|<span data-ttu-id="cc3c5-143">從指定的組件匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-143">Imports a namespace from a specified assembly.</span></span>|  
|[<span data-ttu-id="cc3c5-144">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="cc3c5-144">/keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|<span data-ttu-id="cc3c5-145">指定金鑰組的金鑰容器名稱，為組件提供強式名稱。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-145">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="cc3c5-146">/keyfile</span><span class="sxs-lookup"><span data-stu-id="cc3c5-146">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)|<span data-ttu-id="cc3c5-147">指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-147">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="cc3c5-148">/libpath</span><span class="sxs-lookup"><span data-stu-id="cc3c5-148">/libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)|<span data-ttu-id="cc3c5-149">指定所參考的組件的位置[/參考](../../../visual-basic/reference/command-line-compiler/reference.md)選項。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-149">Specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>|  
|[<span data-ttu-id="cc3c5-150">/reference</span><span class="sxs-lookup"><span data-stu-id="cc3c5-150">/reference</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)|<span data-ttu-id="cc3c5-151">從組匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-151">Imports metadata from an assembly.</span></span>|  
|[<span data-ttu-id="cc3c5-152">/moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="cc3c5-152">/moduleassemblyname</span></span>](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|<span data-ttu-id="cc3c5-153">指定將包含模組的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-153">Specifies the name of the assembly that a module will be a part of.</span></span>|  
|`/analyzer`|<span data-ttu-id="cc3c5-154">從這個組件執行分析器 (簡短形式：/a)</span><span class="sxs-lookup"><span data-stu-id="cc3c5-154">Run the analyzers from this assembly (Short form: /a)</span></span>|  
|`/additionalfile`|<span data-ttu-id="cc3c5-155">命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-155">Names additional files that don't directly affect code generation but may be used by analyzers for producing errors or warnings.</span></span>|  
  
## <a name="debuggingerror-checking"></a><span data-ttu-id="cc3c5-156">偵錯/錯誤檢查</span><span class="sxs-lookup"><span data-stu-id="cc3c5-156">Debugging/Error Checking</span></span>  
  
|<span data-ttu-id="cc3c5-157">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-157">Option</span></span>|<span data-ttu-id="cc3c5-158">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-158">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-159">/bugreport</span><span class="sxs-lookup"><span data-stu-id="cc3c5-159">/bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)|<span data-ttu-id="cc3c5-160">建立檔案，其中包含可簡化錯誤回報的資訊。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-160">Creates a file that contains information that makes it easy to report a bug.</span></span>|  
|[<span data-ttu-id="cc3c5-161">/debug</span><span class="sxs-lookup"><span data-stu-id="cc3c5-161">/debug</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)|<span data-ttu-id="cc3c5-162">產生偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-162">Produces debugging information.</span></span>|  
|[<span data-ttu-id="cc3c5-163">/nowarn</span><span class="sxs-lookup"><span data-stu-id="cc3c5-163">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)|<span data-ttu-id="cc3c5-164">抑制編譯器產生警告的功能。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-164">Suppresses the compiler's ability to generate warnings.</span></span>|  
|[<span data-ttu-id="cc3c5-165">/quiet</span><span class="sxs-lookup"><span data-stu-id="cc3c5-165">/quiet</span></span>](../../../visual-basic/reference/command-line-compiler/quiet.md)|<span data-ttu-id="cc3c5-166">防止編譯器顯示語法相關錯誤和警告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-166">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>|  
|[<span data-ttu-id="cc3c5-167">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="cc3c5-167">/removeintchecks</span></span>](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|<span data-ttu-id="cc3c5-168">停用整數的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-168">Disables integer overflow checking.</span></span>|  
|[<span data-ttu-id="cc3c5-169">/warnaserror</span><span class="sxs-lookup"><span data-stu-id="cc3c5-169">/warnaserror</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|<span data-ttu-id="cc3c5-170">將警告提升為錯誤。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-170">Promotes warnings to errors.</span></span>|  
|`/ruleset:<file>`|<span data-ttu-id="cc3c5-171">指定停用特定診斷的規則集檔案。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-171">Specify a ruleset file that disables specific diagnostics.</span></span>|  
  
## <a name="help"></a><span data-ttu-id="cc3c5-172">說明</span><span class="sxs-lookup"><span data-stu-id="cc3c5-172">Help</span></span>  
  
|<span data-ttu-id="cc3c5-173">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-173">Option</span></span>|<span data-ttu-id="cc3c5-174">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-174">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-175">/?</span><span class="sxs-lookup"><span data-stu-id="cc3c5-175">/?</span></span>](../../../visual-basic/reference/command-line-compiler/help.md)|<span data-ttu-id="cc3c5-176">顯示編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-176">Displays the compiler options.</span></span> <span data-ttu-id="cc3c5-177">此命令的效用等同於指定 `/help` 選項。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-177">This command is the same as specifying the `/help` option.</span></span> <span data-ttu-id="cc3c5-178">未執行編譯。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-178">No compilation occurs.</span></span>|  
|[<span data-ttu-id="cc3c5-179">/help</span><span class="sxs-lookup"><span data-stu-id="cc3c5-179">/help</span></span>](../../../visual-basic/reference/command-line-compiler/help.md)|<span data-ttu-id="cc3c5-180">顯示編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-180">Displays the compiler options.</span></span> <span data-ttu-id="cc3c5-181">此命令的效用等同於指定 `/?` 選項。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-181">This command is the same as specifying the `/?` option.</span></span> <span data-ttu-id="cc3c5-182">未執行編譯。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-182">No compilation occurs.</span></span>|  
  
## <a name="language"></a><span data-ttu-id="cc3c5-183">語言</span><span class="sxs-lookup"><span data-stu-id="cc3c5-183">Language</span></span>  
  
|<span data-ttu-id="cc3c5-184">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-184">Option</span></span>|<span data-ttu-id="cc3c5-185">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-185">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-186">/langversion</span><span class="sxs-lookup"><span data-stu-id="cc3c5-186">/langversion</span></span>](../../../visual-basic/reference/command-line-compiler/langversion.md)|<span data-ttu-id="cc3c5-187">指定語言版本︰ 9 | 9.0 | 10 | 10.0 | 11 | 11.0。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-187">Specify language version: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.</span></span>|  
|[<span data-ttu-id="cc3c5-188">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="cc3c5-188">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|<span data-ttu-id="cc3c5-189">強制執行變數的明確宣告。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-189">Enforces explicit declaration of variables.</span></span>|  
|[<span data-ttu-id="cc3c5-190">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="cc3c5-190">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|<span data-ttu-id="cc3c5-191">強制執行嚴格類型語意。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-191">Enforces strict type semantics.</span></span>|  
|[<span data-ttu-id="cc3c5-192">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="cc3c5-192">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|<span data-ttu-id="cc3c5-193">指定字串比較是否應為二進位，或是使用地區設定特定的文字語意。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-193">Specifies whether string comparisons should be binary or use locale-specific text semantics.</span></span>|  
|[<span data-ttu-id="cc3c5-194">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="cc3c5-194">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|<span data-ttu-id="cc3c5-195">可讓您在變數宣告中使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-195">Enables the use of local type inference in variable declarations.</span></span>|  
  
## <a name="preprocessor"></a><span data-ttu-id="cc3c5-196">前置處理器</span><span class="sxs-lookup"><span data-stu-id="cc3c5-196">Preprocessor</span></span>  
  
|<span data-ttu-id="cc3c5-197">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-197">Option</span></span>|<span data-ttu-id="cc3c5-198">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-198">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-199">/define</span><span class="sxs-lookup"><span data-stu-id="cc3c5-199">/define</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)|<span data-ttu-id="cc3c5-200">定義條件式編譯的符號。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-200">Defines symbols for conditional compilation.</span></span>|  
  
## <a name="resources"></a><span data-ttu-id="cc3c5-201">資源</span><span class="sxs-lookup"><span data-stu-id="cc3c5-201">Resources</span></span>  
  
|<span data-ttu-id="cc3c5-202">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-202">Option</span></span>|<span data-ttu-id="cc3c5-203">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-203">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-204">/linkresource</span><span class="sxs-lookup"><span data-stu-id="cc3c5-204">/linkresource</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)|<span data-ttu-id="cc3c5-205">建立與 Managed 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-205">Creates a link to a managed resource.</span></span>|  
|[<span data-ttu-id="cc3c5-206">/resource</span><span class="sxs-lookup"><span data-stu-id="cc3c5-206">/resource</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)|<span data-ttu-id="cc3c5-207">將 Managed 資源內嵌至組件中。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-207">Embeds a managed resource in an assembly.</span></span>|  
|[<span data-ttu-id="cc3c5-208">/win32icon</span><span class="sxs-lookup"><span data-stu-id="cc3c5-208">/win32icon</span></span>](../../../visual-basic/reference/command-line-compiler/win32icon.md)|<span data-ttu-id="cc3c5-209">將 .ico 檔插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-209">Inserts an .ico file into the output file.</span></span>|  
|[<span data-ttu-id="cc3c5-210">/win32resource</span><span class="sxs-lookup"><span data-stu-id="cc3c5-210">/win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)|<span data-ttu-id="cc3c5-211">將 Win32 資源插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-211">Inserts a Win32 resource into the output file.</span></span>|  
  
## <a name="miscellaneous"></a><span data-ttu-id="cc3c5-212">其他</span><span class="sxs-lookup"><span data-stu-id="cc3c5-212">Miscellaneous</span></span>  
  
|<span data-ttu-id="cc3c5-213">選項</span><span class="sxs-lookup"><span data-stu-id="cc3c5-213">Option</span></span>|<span data-ttu-id="cc3c5-214">用途</span><span class="sxs-lookup"><span data-stu-id="cc3c5-214">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="cc3c5-215">@ (指定回應檔)</span><span class="sxs-lookup"><span data-stu-id="cc3c5-215">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|<span data-ttu-id="cc3c5-216">指定回應檔。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-216">Specifies a response file.</span></span>|  
|[<span data-ttu-id="cc3c5-217">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="cc3c5-217">/baseaddress</span></span>](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|<span data-ttu-id="cc3c5-218">指定 DLL 的基底位址。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-218">Specifies the base address of a DLL.</span></span>|  
|[<span data-ttu-id="cc3c5-219">/codepage</span><span class="sxs-lookup"><span data-stu-id="cc3c5-219">/codepage</span></span>](../../../visual-basic/reference/command-line-compiler/codepage.md)|<span data-ttu-id="cc3c5-220">指定編譯過程中所有原始程式碼檔使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-220">Specifies the code page to use for all source code files in the compilation.</span></span>|  
|[<span data-ttu-id="cc3c5-221">/errorreport</span><span class="sxs-lookup"><span data-stu-id="cc3c5-221">/errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)|<span data-ttu-id="cc3c5-222">指定 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器報告編譯器內部錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-222">Specifies how the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler should report internal compiler errors.</span></span>|  
|[<span data-ttu-id="cc3c5-223">/highentropyva</span><span class="sxs-lookup"><span data-stu-id="cc3c5-223">/highentropyva</span></span>](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|<span data-ttu-id="cc3c5-224">指示 Windows 核心某一特定可執行檔是否支援高熵位址空間配置隨機載入 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-224">Tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>|  
|[<span data-ttu-id="cc3c5-225">/main</span><span class="sxs-lookup"><span data-stu-id="cc3c5-225">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)|<span data-ttu-id="cc3c5-226">指定類別，其中包含`Sub``Main`程序在啟動時使用。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-226">Specifies the class that contains the `Sub``Main` procedure to use at startup.</span></span>|  
|[<span data-ttu-id="cc3c5-227">/noconfig</span><span class="sxs-lookup"><span data-stu-id="cc3c5-227">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)|<span data-ttu-id="cc3c5-228">不使用 Vbc.rsp 進行編譯</span><span class="sxs-lookup"><span data-stu-id="cc3c5-228">Do not compile with Vbc.rsp</span></span>|  
|[<span data-ttu-id="cc3c5-229">/nostdlib</span><span class="sxs-lookup"><span data-stu-id="cc3c5-229">/nostdlib</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|<span data-ttu-id="cc3c5-230">使編譯器不要參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-230">Causes the compiler not to reference the standard libraries.</span></span>|  
|[<span data-ttu-id="cc3c5-231">/nowin32manifest</span><span class="sxs-lookup"><span data-stu-id="cc3c5-231">/nowin32manifest</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|<span data-ttu-id="cc3c5-232">指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-232">Instructs the compiler not to embed any application manifest into the executable file.</span></span>|  
|[<span data-ttu-id="cc3c5-233">/platform</span><span class="sxs-lookup"><span data-stu-id="cc3c5-233">/platform</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)|<span data-ttu-id="cc3c5-234">指定編譯器為輸出檔設為目標的處理器平台。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-234">Specifies the processor platform the compiler targets for the output file.</span></span>|  
|[<span data-ttu-id="cc3c5-235">/recurse</span><span class="sxs-lookup"><span data-stu-id="cc3c5-235">/recurse</span></span>](../../../visual-basic/reference/command-line-compiler/recurse.md)|<span data-ttu-id="cc3c5-236">搜尋要編譯之原始程式檔的子目錄。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-236">Searches subdirectories for source files to compile.</span></span>|  
|[<span data-ttu-id="cc3c5-237">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="cc3c5-237">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|<span data-ttu-id="cc3c5-238">指定所有類型宣告的命名空間。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-238">Specifies a namespace for all type declarations.</span></span>|  
|[<span data-ttu-id="cc3c5-239">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="cc3c5-239">/sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|<span data-ttu-id="cc3c5-240">指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-240">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>|  
|[<span data-ttu-id="cc3c5-241">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="cc3c5-241">/vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|<span data-ttu-id="cc3c5-242">指定編譯器在編譯時不應使用 Visual Basic 執行階段程式庫的參考，或應使用特定執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-242">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>|  
|[<span data-ttu-id="cc3c5-243">/win32manifest</span><span class="sxs-lookup"><span data-stu-id="cc3c5-243">/win32manifest</span></span>](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|<span data-ttu-id="cc3c5-244">識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-244">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>|  
|`/parallel[+&#124;-]`|<span data-ttu-id="cc3c5-245">指定是否要使用並行組建 (+)。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-245">Specifies whether to use concurrent build (+).</span></span>|  
|`/checksumalgorithm:<alg>`|<span data-ttu-id="cc3c5-246">指定用於計算儲存在 PDB 的來源檔案總和檢查碼的演算法。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-246">Specify the algorithm for calculating the source file checksum stored in PDB.</span></span>  <span data-ttu-id="cc3c5-247">支援的值為：SHA1 (預設值) 或 SHA256。</span><span class="sxs-lookup"><span data-stu-id="cc3c5-247">Supported values are: SHA1 (default) or SHA256.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc3c5-248">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc3c5-248">See Also</span></span>  
 <span data-ttu-id="cc3c5-249">[依字母順序列出 Visual Basic 編譯器選項](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md) </span><span class="sxs-lookup"><span data-stu-id="cc3c5-249">[Visual Basic Compiler Options Listed Alphabetically](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md) </span></span>  
<span data-ttu-id="cc3c5-250"> [專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7) </span><span class="sxs-lookup"><span data-stu-id="cc3c5-250"> [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7) </span></span>  
<span data-ttu-id="cc3c5-251"> [依字母順序列出 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-alphabetically.md) </span><span class="sxs-lookup"><span data-stu-id="cc3c5-251"> [C# Compiler Options Listed Alphabetically](../../../csharp/language-reference/compiler-options/listed-alphabetically.md) </span></span>  
<span data-ttu-id="cc3c5-252"> [依分類列出的 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-by-category.md)</span><span class="sxs-lookup"><span data-stu-id="cc3c5-252"> [C# Compiler Options Listed by Category](../../../csharp/language-reference/compiler-options/listed-by-category.md)</span></span>
