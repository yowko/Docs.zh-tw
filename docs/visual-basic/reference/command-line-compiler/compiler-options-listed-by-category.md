---
title: 依分類排列的編譯器選項
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 77a130b684d26cf7e4b9df9382348a371a60bc5d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072037"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a><span data-ttu-id="664ba-102">依類別列出的 Visual Basic 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="664ba-102">Visual Basic compiler options listed by category</span></span>

<span data-ttu-id="664ba-103">Visual Basic 的命令列編譯器可作為從 Visual Studio 整合式開發環境（ (IDE) ）編譯器的替代方案。</span><span class="sxs-lookup"><span data-stu-id="664ba-103">The Visual Basic command-line compiler is provided as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="664ba-104">以下是依功能類別目錄排序 Visual Basic 命令列編譯器選項的清單。</span><span class="sxs-lookup"><span data-stu-id="664ba-104">The following is a list of the Visual Basic command-line compiler options sorted by functional category.</span></span>  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a><span data-ttu-id="664ba-105">編譯器輸出</span><span class="sxs-lookup"><span data-stu-id="664ba-105">Compiler output</span></span>  
  
|<span data-ttu-id="664ba-106">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-106">Option</span></span>|<span data-ttu-id="664ba-107">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-107">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-108">-nologo</span><span class="sxs-lookup"><span data-stu-id="664ba-108">-nologo</span></span>](nologo.md)|<span data-ttu-id="664ba-109">隱藏編譯器橫幅資訊。</span><span class="sxs-lookup"><span data-stu-id="664ba-109">Suppresses compiler banner information.</span></span>|  
|[<span data-ttu-id="664ba-110">-utf8output</span><span class="sxs-lookup"><span data-stu-id="664ba-110">-utf8output</span></span>](utf8output.md)|<span data-ttu-id="664ba-111">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="664ba-111">Displays compiler output using UTF-8 encoding.</span></span>|  
|[<span data-ttu-id="664ba-112">-verbose</span><span class="sxs-lookup"><span data-stu-id="664ba-112">-verbose</span></span>](verbose.md)|<span data-ttu-id="664ba-113">在編譯期間輸出額外資訊。</span><span class="sxs-lookup"><span data-stu-id="664ba-113">Outputs extra information during compilation.</span></span>|  
|`-modulename:<string>`|<span data-ttu-id="664ba-114">指定來源模組的名稱</span><span class="sxs-lookup"><span data-stu-id="664ba-114">Specify the name of the source module</span></span>|  
|[<span data-ttu-id="664ba-115">-preferreduilang</span><span class="sxs-lookup"><span data-stu-id="664ba-115">-preferreduilang</span></span>](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|<span data-ttu-id="664ba-116">指定編譯器輸出的語言。</span><span class="sxs-lookup"><span data-stu-id="664ba-116">Specify a language for compiler output.</span></span>|
  
## <a name="optimization"></a><span data-ttu-id="664ba-117">Optimization</span><span class="sxs-lookup"><span data-stu-id="664ba-117">Optimization</span></span>  
  
|<span data-ttu-id="664ba-118">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-118">Option</span></span>|<span data-ttu-id="664ba-119">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-119">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-120">-filealign</span><span class="sxs-lookup"><span data-stu-id="664ba-120">-filealign</span></span>](filealign.md)|<span data-ttu-id="664ba-121">指定要對齊輸出檔案區段的位置。</span><span class="sxs-lookup"><span data-stu-id="664ba-121">Specifies where to align the sections of the output file.</span></span>|  
|[<span data-ttu-id="664ba-122">-優化</span><span class="sxs-lookup"><span data-stu-id="664ba-122">-optimize</span></span>](optimize.md)|<span data-ttu-id="664ba-123">啟用/停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="664ba-123">Enables/disables optimizations.</span></span>|  
  
## <a name="output-files"></a><span data-ttu-id="664ba-124">輸出檔案</span><span class="sxs-lookup"><span data-stu-id="664ba-124">Output files</span></span>  
  
|<span data-ttu-id="664ba-125">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-125">Option</span></span>|<span data-ttu-id="664ba-126">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-126">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-127">-doc</span><span class="sxs-lookup"><span data-stu-id="664ba-127">-doc</span></span>](doc.md)|<span data-ttu-id="664ba-128">將文件註解處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="664ba-128">Process documentation comments to an XML file.</span></span>|  
|[<span data-ttu-id="664ba-129">-具決定性</span><span class="sxs-lookup"><span data-stu-id="664ba-129">-deterministic</span></span>](deterministic.md)|<span data-ttu-id="664ba-130">可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。</span><span class="sxs-lookup"><span data-stu-id="664ba-130">Causes the compiler to output an assembly whose binary content is identical across compilations if inputs are identical.</span></span>|
|[<span data-ttu-id="664ba-131">-netcf</span><span class="sxs-lookup"><span data-stu-id="664ba-131">-netcf</span></span>](netcf.md)|<span data-ttu-id="664ba-132">將編譯器設定為以 .NET Compact Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="664ba-132">Sets the compiler to target the .NET Compact Framework.</span></span>|  
|[<span data-ttu-id="664ba-133">-out</span><span class="sxs-lookup"><span data-stu-id="664ba-133">-out</span></span>](out.md)|<span data-ttu-id="664ba-134">指定輸出檔。</span><span class="sxs-lookup"><span data-stu-id="664ba-134">Specifies an output file.</span></span>|  
|[<span data-ttu-id="664ba-135">-refonly</span><span class="sxs-lookup"><span data-stu-id="664ba-135">-refonly</span></span>](refonly-compiler-option.md)|<span data-ttu-id="664ba-136">只輸出參考元件。</span><span class="sxs-lookup"><span data-stu-id="664ba-136">Outputs only a reference assembly.</span></span>|
|[<span data-ttu-id="664ba-137">-refout</span><span class="sxs-lookup"><span data-stu-id="664ba-137">-refout</span></span>](refout-compiler-option.md)|<span data-ttu-id="664ba-138">指定參考元件的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="664ba-138">Specifies the output path of a reference assembly.</span></span>|
|[<span data-ttu-id="664ba-139">-目標</span><span class="sxs-lookup"><span data-stu-id="664ba-139">-target</span></span>](target.md)|<span data-ttu-id="664ba-140">指定輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="664ba-140">Specifies the format of the output.</span></span>|  
  
## <a name="net-assemblies"></a><span data-ttu-id="664ba-141">.NET 組件</span><span class="sxs-lookup"><span data-stu-id="664ba-141">.NET assemblies</span></span>  
  
|<span data-ttu-id="664ba-142">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-142">Option</span></span>|<span data-ttu-id="664ba-143">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-143">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-144">-addmodule</span><span class="sxs-lookup"><span data-stu-id="664ba-144">-addmodule</span></span>](addmodule.md)|<span data-ttu-id="664ba-145">讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="664ba-145">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>|  
|[<span data-ttu-id="664ba-146">-delaysign</span><span class="sxs-lookup"><span data-stu-id="664ba-146">-delaysign</span></span>](delaysign.md)|<span data-ttu-id="664ba-147">指定將要完整簽署還是部分簽署組件。</span><span class="sxs-lookup"><span data-stu-id="664ba-147">Specifies whether the assembly will be fully or partially signed.</span></span>|  
|[<span data-ttu-id="664ba-148">-imports</span><span class="sxs-lookup"><span data-stu-id="664ba-148">-imports</span></span>](imports.md)|<span data-ttu-id="664ba-149">從指定的組件匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="664ba-149">Imports a namespace from a specified assembly.</span></span>|  
|[<span data-ttu-id="664ba-150">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="664ba-150">-keycontainer</span></span>](keycontainer.md)|<span data-ttu-id="664ba-151">指定金鑰組的金鑰容器名稱，為組件提供強式名稱。</span><span class="sxs-lookup"><span data-stu-id="664ba-151">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="664ba-152">-keyfile</span><span class="sxs-lookup"><span data-stu-id="664ba-152">-keyfile</span></span>](keyfile.md)|<span data-ttu-id="664ba-153">指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。</span><span class="sxs-lookup"><span data-stu-id="664ba-153">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="664ba-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="664ba-154">-libpath</span></span>](libpath.md)|<span data-ttu-id="664ba-155">指定 [參考](reference.md) 選項所參考之元件的位置。</span><span class="sxs-lookup"><span data-stu-id="664ba-155">Specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>|  
|[<span data-ttu-id="664ba-156">-reference</span><span class="sxs-lookup"><span data-stu-id="664ba-156">-reference</span></span>](reference.md)|<span data-ttu-id="664ba-157">從組匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="664ba-157">Imports metadata from an assembly.</span></span>|  
|[<span data-ttu-id="664ba-158">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="664ba-158">-moduleassemblyname</span></span>](moduleassemblyname.md)|<span data-ttu-id="664ba-159">指定將包含模組的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="664ba-159">Specifies the name of the assembly that a module will be a part of.</span></span>|  
|`-analyzer`|<span data-ttu-id="664ba-160">從這個組件執行分析器 (簡短形式：-a)</span><span class="sxs-lookup"><span data-stu-id="664ba-160">Run the analyzers from this assembly (Short form: -a)</span></span>|  
|`-additionalfile`|<span data-ttu-id="664ba-161">命名不會直接影響程式碼產生，但可能被分析器用來產生錯誤或警告的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="664ba-161">Names additional files that don't directly affect code generation but may be used by analyzers for producing errors or warnings.</span></span>|  
  
## <a name="debuggingerror-checking"></a><span data-ttu-id="664ba-162">調試/錯誤檢查</span><span class="sxs-lookup"><span data-stu-id="664ba-162">Debugging/error checking</span></span>  
  
|<span data-ttu-id="664ba-163">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-163">Option</span></span>|<span data-ttu-id="664ba-164">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-164">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-165">-bugreport</span><span class="sxs-lookup"><span data-stu-id="664ba-165">-bugreport</span></span>](bugreport.md)|<span data-ttu-id="664ba-166">建立檔案，其中包含可簡化錯誤回報的資訊。</span><span class="sxs-lookup"><span data-stu-id="664ba-166">Creates a file that contains information that makes it easy to report a bug.</span></span>|  
|[<span data-ttu-id="664ba-167">-debug</span><span class="sxs-lookup"><span data-stu-id="664ba-167">-debug</span></span>](debug.md)|<span data-ttu-id="664ba-168">產生偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="664ba-168">Produces debugging information.</span></span>|  
|[<span data-ttu-id="664ba-169">-nowarn</span><span class="sxs-lookup"><span data-stu-id="664ba-169">-nowarn</span></span>](nowarn.md)|<span data-ttu-id="664ba-170">抑制編譯器產生警告的功能。</span><span class="sxs-lookup"><span data-stu-id="664ba-170">Suppresses the compiler's ability to generate warnings.</span></span>|  
|[<span data-ttu-id="664ba-171">-quiet</span><span class="sxs-lookup"><span data-stu-id="664ba-171">-quiet</span></span>](quiet.md)|<span data-ttu-id="664ba-172">防止編譯器顯示語法相關錯誤和警告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="664ba-172">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>|  
|[<span data-ttu-id="664ba-173">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="664ba-173">-removeintchecks</span></span>](removeintchecks.md)|<span data-ttu-id="664ba-174">停用整數的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="664ba-174">Disables integer overflow checking.</span></span>|  
|[<span data-ttu-id="664ba-175">-warnaserror</span><span class="sxs-lookup"><span data-stu-id="664ba-175">-warnaserror</span></span>](warnaserror.md)|<span data-ttu-id="664ba-176">將警告提升為錯誤。</span><span class="sxs-lookup"><span data-stu-id="664ba-176">Promotes warnings to errors.</span></span>|  
|`-ruleset:<file>`|<span data-ttu-id="664ba-177">指定停用特定診斷的規則集檔案。</span><span class="sxs-lookup"><span data-stu-id="664ba-177">Specify a ruleset file that disables specific diagnostics.</span></span>|  
  
## <a name="help"></a><span data-ttu-id="664ba-178">説明</span><span class="sxs-lookup"><span data-stu-id="664ba-178">Help</span></span>  
  
|<span data-ttu-id="664ba-179">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-179">Option</span></span>|<span data-ttu-id="664ba-180">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-180">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-181">-?</span><span class="sxs-lookup"><span data-stu-id="664ba-181">-?</span></span>](help.md)|<span data-ttu-id="664ba-182">顯示編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="664ba-182">Displays the compiler options.</span></span> <span data-ttu-id="664ba-183">此命令的效用等同於指定 `-help` 選項。</span><span class="sxs-lookup"><span data-stu-id="664ba-183">This command is the same as specifying the `-help` option.</span></span> <span data-ttu-id="664ba-184">未執行編譯。</span><span class="sxs-lookup"><span data-stu-id="664ba-184">No compilation occurs.</span></span>|  
|[<span data-ttu-id="664ba-185">-help</span><span class="sxs-lookup"><span data-stu-id="664ba-185">-help</span></span>](help.md)|<span data-ttu-id="664ba-186">顯示編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="664ba-186">Displays the compiler options.</span></span> <span data-ttu-id="664ba-187">此命令的效用等同於指定 `-?` 選項。</span><span class="sxs-lookup"><span data-stu-id="664ba-187">This command is the same as specifying the `-?` option.</span></span> <span data-ttu-id="664ba-188">未執行編譯。</span><span class="sxs-lookup"><span data-stu-id="664ba-188">No compilation occurs.</span></span>|  
  
## <a name="language"></a><span data-ttu-id="664ba-189">Language</span><span class="sxs-lookup"><span data-stu-id="664ba-189">Language</span></span>  
  
|<span data-ttu-id="664ba-190">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-190">Option</span></span>|<span data-ttu-id="664ba-191">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-191">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-192">-langversion</span><span class="sxs-lookup"><span data-stu-id="664ba-192">-langversion</span></span>](langversion.md)|<span data-ttu-id="664ba-193">指定語言版本： 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0。</span><span class="sxs-lookup"><span data-stu-id="664ba-193">Specify language version: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.</span></span>|  
|[<span data-ttu-id="664ba-194">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="664ba-194">-optionexplicit</span></span>](optionexplicit.md)|<span data-ttu-id="664ba-195">強制執行變數的明確宣告。</span><span class="sxs-lookup"><span data-stu-id="664ba-195">Enforces explicit declaration of variables.</span></span>|  
|[<span data-ttu-id="664ba-196">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="664ba-196">-optionstrict</span></span>](optionstrict.md)|<span data-ttu-id="664ba-197">強制執行嚴格類型語意。</span><span class="sxs-lookup"><span data-stu-id="664ba-197">Enforces strict type semantics.</span></span>|  
|[<span data-ttu-id="664ba-198">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="664ba-198">-optioncompare</span></span>](optioncompare.md)|<span data-ttu-id="664ba-199">指定字串比較是否應為二進位，或是使用地區設定特定的文字語意。</span><span class="sxs-lookup"><span data-stu-id="664ba-199">Specifies whether string comparisons should be binary or use locale-specific text semantics.</span></span>|  
|[<span data-ttu-id="664ba-200">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="664ba-200">-optioninfer</span></span>](optioninfer.md)|<span data-ttu-id="664ba-201">可讓您在變數宣告中使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="664ba-201">Enables the use of local type inference in variable declarations.</span></span>|  
  
## <a name="preprocessor"></a><span data-ttu-id="664ba-202">前置處理器</span><span class="sxs-lookup"><span data-stu-id="664ba-202">Preprocessor</span></span>  
  
|<span data-ttu-id="664ba-203">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-203">Option</span></span>|<span data-ttu-id="664ba-204">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-204">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-205">-define</span><span class="sxs-lookup"><span data-stu-id="664ba-205">-define</span></span>](define.md)|<span data-ttu-id="664ba-206">定義條件式編譯的符號。</span><span class="sxs-lookup"><span data-stu-id="664ba-206">Defines symbols for conditional compilation.</span></span>|  
  
## <a name="resources"></a><span data-ttu-id="664ba-207">資源</span><span class="sxs-lookup"><span data-stu-id="664ba-207">Resources</span></span>  
  
|<span data-ttu-id="664ba-208">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-208">Option</span></span>|<span data-ttu-id="664ba-209">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-209">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-210">-linkresource</span><span class="sxs-lookup"><span data-stu-id="664ba-210">-linkresource</span></span>](linkresource.md)|<span data-ttu-id="664ba-211">建立與 Managed 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="664ba-211">Creates a link to a managed resource.</span></span>|  
|[<span data-ttu-id="664ba-212">-資源</span><span class="sxs-lookup"><span data-stu-id="664ba-212">-resource</span></span>](resource.md)|<span data-ttu-id="664ba-213">將 Managed 資源內嵌至組件中。</span><span class="sxs-lookup"><span data-stu-id="664ba-213">Embeds a managed resource in an assembly.</span></span>|  
|[<span data-ttu-id="664ba-214">-win32icon</span><span class="sxs-lookup"><span data-stu-id="664ba-214">-win32icon</span></span>](win32icon.md)|<span data-ttu-id="664ba-215">將 .ico 檔插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="664ba-215">Inserts an .ico file into the output file.</span></span>|  
|[<span data-ttu-id="664ba-216">-win32resource</span><span class="sxs-lookup"><span data-stu-id="664ba-216">-win32resource</span></span>](win32resource.md)|<span data-ttu-id="664ba-217">將 Win32 資源插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="664ba-217">Inserts a Win32 resource into the output file.</span></span>|  
  
## <a name="miscellaneous"></a><span data-ttu-id="664ba-218">其他</span><span class="sxs-lookup"><span data-stu-id="664ba-218">Miscellaneous</span></span>  
  
|<span data-ttu-id="664ba-219">選項</span><span class="sxs-lookup"><span data-stu-id="664ba-219">Option</span></span>|<span data-ttu-id="664ba-220">目的</span><span class="sxs-lookup"><span data-stu-id="664ba-220">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="664ba-221">@ (指定回應檔)</span><span class="sxs-lookup"><span data-stu-id="664ba-221">@ (Specify Response File)</span></span>](specify-response-file.md)|<span data-ttu-id="664ba-222">指定回應檔。</span><span class="sxs-lookup"><span data-stu-id="664ba-222">Specifies a response file.</span></span>|  
|[<span data-ttu-id="664ba-223">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="664ba-223">-baseaddress</span></span>](baseaddress.md)|<span data-ttu-id="664ba-224">指定 DLL 的基底位址。</span><span class="sxs-lookup"><span data-stu-id="664ba-224">Specifies the base address of a DLL.</span></span>|  
|[<span data-ttu-id="664ba-225">-字碼頁</span><span class="sxs-lookup"><span data-stu-id="664ba-225">-codepage</span></span>](codepage.md)|<span data-ttu-id="664ba-226">指定編譯過程中所有原始程式碼檔使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="664ba-226">Specifies the code page to use for all source code files in the compilation.</span></span>|  
|[<span data-ttu-id="664ba-227">-errorreport</span><span class="sxs-lookup"><span data-stu-id="664ba-227">-errorreport</span></span>](errorreport.md)|<span data-ttu-id="664ba-228">指定 Visual Basic 編譯器應該如何報告內部編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="664ba-228">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>|  
|[<span data-ttu-id="664ba-229">-highentropyva</span><span class="sxs-lookup"><span data-stu-id="664ba-229">-highentropyva</span></span>](highentropyva.md)|<span data-ttu-id="664ba-230">指示 Windows 核心某一特定可執行檔是否支援高熵位址空間配置隨機載入 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="664ba-230">Tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>|  
|[<span data-ttu-id="664ba-231">-main</span><span class="sxs-lookup"><span data-stu-id="664ba-231">-main</span></span>](main.md)|<span data-ttu-id="664ba-232">指定包含啟動時所要使用之程式的類別 `Sub Main` 。</span><span class="sxs-lookup"><span data-stu-id="664ba-232">Specifies the class that contains the `Sub Main` procedure to use at startup.</span></span>|  
|[<span data-ttu-id="664ba-233">-noconfig</span><span class="sxs-lookup"><span data-stu-id="664ba-233">-noconfig</span></span>](noconfig.md)|<span data-ttu-id="664ba-234">不使用 Vbc.rsp 進行編譯</span><span class="sxs-lookup"><span data-stu-id="664ba-234">Do not compile with Vbc.rsp</span></span>|  
|[<span data-ttu-id="664ba-235">-nostdlib</span><span class="sxs-lookup"><span data-stu-id="664ba-235">-nostdlib</span></span>](nostdlib.md)|<span data-ttu-id="664ba-236">使編譯器不要參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="664ba-236">Causes the compiler not to reference the standard libraries.</span></span>|  
|[<span data-ttu-id="664ba-237">-nowin32manifest</span><span class="sxs-lookup"><span data-stu-id="664ba-237">-nowin32manifest</span></span>](nowin32manifest.md)|<span data-ttu-id="664ba-238">指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="664ba-238">Instructs the compiler not to embed any application manifest into the executable file.</span></span>|  
|[<span data-ttu-id="664ba-239">-platform</span><span class="sxs-lookup"><span data-stu-id="664ba-239">-platform</span></span>](platform.md)|<span data-ttu-id="664ba-240">指定編譯器為輸出檔設為目標的處理器平台。</span><span class="sxs-lookup"><span data-stu-id="664ba-240">Specifies the processor platform the compiler targets for the output file.</span></span>|  
|[<span data-ttu-id="664ba-241">-遞迴</span><span class="sxs-lookup"><span data-stu-id="664ba-241">-recurse</span></span>](recurse.md)|<span data-ttu-id="664ba-242">搜尋要編譯之原始程式檔的子目錄。</span><span class="sxs-lookup"><span data-stu-id="664ba-242">Searches subdirectories for source files to compile.</span></span>|  
|[<span data-ttu-id="664ba-243">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="664ba-243">-rootnamespace</span></span>](rootnamespace.md)|<span data-ttu-id="664ba-244">指定所有類型宣告的命名空間。</span><span class="sxs-lookup"><span data-stu-id="664ba-244">Specifies a namespace for all type declarations.</span></span>|  
|[<span data-ttu-id="664ba-245">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="664ba-245">-sdkpath</span></span>](sdkpath.md)|<span data-ttu-id="664ba-246">指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="664ba-246">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>|  
|[<span data-ttu-id="664ba-247">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="664ba-247">-vbruntime</span></span>](vbruntime.md)|<span data-ttu-id="664ba-248">指定編譯器在編譯時不應使用 Visual Basic 執行階段程式庫的參考，或應使用特定執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="664ba-248">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>|  
|[<span data-ttu-id="664ba-249">-win32manifest</span><span class="sxs-lookup"><span data-stu-id="664ba-249">-win32manifest</span></span>](win32manifest.md)|<span data-ttu-id="664ba-250">識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="664ba-250">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>|  
|`-parallel[+&#124;-]`|<span data-ttu-id="664ba-251">指定是否要使用並行組建 (+)。</span><span class="sxs-lookup"><span data-stu-id="664ba-251">Specifies whether to use concurrent build (+).</span></span>|  
|`-checksumalgorithm:<alg>`|<span data-ttu-id="664ba-252">指定用於計算儲存在 PDB 的來源檔案總和檢查碼的演算法。</span><span class="sxs-lookup"><span data-stu-id="664ba-252">Specify the algorithm for calculating the source file checksum stored in PDB.</span></span>  <span data-ttu-id="664ba-253">支援的值為：SHA1 (預設值) 或 SHA256。</span><span class="sxs-lookup"><span data-stu-id="664ba-253">Supported values are: SHA1 (default) or SHA256.</span></span> <br><span data-ttu-id="664ba-254">由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="664ba-254">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="664ba-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="664ba-255">See also</span></span>

- [<span data-ttu-id="664ba-256">Visual Basic Compiler Options Listed Alphabetically</span><span class="sxs-lookup"><span data-stu-id="664ba-256">Visual Basic Compiler Options Listed Alphabetically</span></span>](compiler-options-listed-alphabetically.md)
- [<span data-ttu-id="664ba-257">管理專案和解決方案屬性</span><span class="sxs-lookup"><span data-stu-id="664ba-257">Manage project and solution properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
