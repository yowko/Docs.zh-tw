---
title: "SecAnnotate.exe (.NET Security Annotator 工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7051e753c324933828e2447752f9c5ea13ed9d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="secannotateexe-net-security-annotator-tool"></a><span data-ttu-id="079dd-102">SecAnnotate.exe (.NET Security Annotator 工具)</span><span class="sxs-lookup"><span data-stu-id="079dd-102">SecAnnotate.exe (.NET Security Annotator Tool)</span></span>
<span data-ttu-id="079dd-103">.NET Security Annotator 工具 (SecAnnotate.exe) 是識別一個或多個組件之 `SecurityCritical` 和 `SecuritySafeCritical` 部分的命令列應用程式。</span><span class="sxs-lookup"><span data-stu-id="079dd-103">The .NET Security Annotator tool (SecAnnotate.exe) is a command-line application that identifies the `SecurityCritical` and `SecuritySafeCritical` portions of one or more assemblies.</span></span>  
  
 <span data-ttu-id="079dd-104">Visual Studio 延伸模組 ([Security Annotator](http://go.microsoft.com/fwlink/?LinkId=198007)) 提供 SecAnnotate.exe 的圖形化使用者介面，讓您能夠從 Visual Studio 執行該工具。</span><span class="sxs-lookup"><span data-stu-id="079dd-104">A Visual Studio extension, [Security Annotator](http://go.microsoft.com/fwlink/?LinkId=198007), provides a graphical user interface to SecAnnotate.exe and enables you to run the tool from Visual Studio.</span></span>  
  
 <span data-ttu-id="079dd-105">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="079dd-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="079dd-106">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="079dd-106">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="079dd-107">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="079dd-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="079dd-108">在命令提示字元下鍵入以下內容，*parameters* 會在下一節中說明，而 *assemblies* 則包含以空格分隔的一或多個組件名稱：</span><span class="sxs-lookup"><span data-stu-id="079dd-108">At the command prompt, type the following, where *parameters* are described in the following section, and *assemblies* consist of one or more assembly names separated by blanks:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079dd-109">語法</span><span class="sxs-lookup"><span data-stu-id="079dd-109">Syntax</span></span>  
  
```  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="079dd-110">參數</span><span class="sxs-lookup"><span data-stu-id="079dd-110">Parameters</span></span>  
  
|<span data-ttu-id="079dd-111">選項</span><span class="sxs-lookup"><span data-stu-id="079dd-111">Option</span></span>|<span data-ttu-id="079dd-112">說明</span><span class="sxs-lookup"><span data-stu-id="079dd-112">Description</span></span>|  
|------------|-----------------|  
|`/a`<br /><br /> <span data-ttu-id="079dd-113">或</span><span class="sxs-lookup"><span data-stu-id="079dd-113">or</span></span><br /><br /> `/showstatistics`|<span data-ttu-id="079dd-114">顯示要分析之組件中有關透明度使用的統計資料。</span><span class="sxs-lookup"><span data-stu-id="079dd-114">Shows statistics about the use of transparency in assemblies that are being analyzed.</span></span>|  
|<span data-ttu-id="079dd-115">`/d:` *directory*</span><span class="sxs-lookup"><span data-stu-id="079dd-115">`/d:` *directory*</span></span><br /><br /> <span data-ttu-id="079dd-116">或</span><span class="sxs-lookup"><span data-stu-id="079dd-116">or</span></span><br /><br /> <span data-ttu-id="079dd-117">`/referencedir:` *directory*</span><span class="sxs-lookup"><span data-stu-id="079dd-117">`/referencedir:` *directory*</span></span>|<span data-ttu-id="079dd-118">指定要在註釋期間搜尋相依組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="079dd-118">Specifies a directory to search for dependent assemblies during annotation.</span></span>|  
|`/i`<br /><br /> <span data-ttu-id="079dd-119">或</span><span class="sxs-lookup"><span data-stu-id="079dd-119">or</span></span><br /><br /> `/includesignatures`|<span data-ttu-id="079dd-120">在註釋報告檔中包含延伸的簽章資訊。</span><span class="sxs-lookup"><span data-stu-id="079dd-120">Includes extended signature information in the annotation report file.</span></span>|  
|`/n`<br /><br /> <span data-ttu-id="079dd-121">或</span><span class="sxs-lookup"><span data-stu-id="079dd-121">or</span></span><br /><br /> `/nogac`|<span data-ttu-id="079dd-122">撤銷對全域組件快取中參考組件的搜尋。</span><span class="sxs-lookup"><span data-stu-id="079dd-122">Suppresses searching for referenced assemblies in the global assembly cache.</span></span>|  
|<span data-ttu-id="079dd-123">`/o:` *output.xml*</span><span class="sxs-lookup"><span data-stu-id="079dd-123">`/o:` *output.xml*</span></span><br /><br /> <span data-ttu-id="079dd-124">或</span><span class="sxs-lookup"><span data-stu-id="079dd-124">or</span></span><br /><br /> <span data-ttu-id="079dd-125">`/out:` *output.xml*</span><span class="sxs-lookup"><span data-stu-id="079dd-125">`/out:` *output.xml*</span></span>|<span data-ttu-id="079dd-126">指定輸出的註釋檔案。</span><span class="sxs-lookup"><span data-stu-id="079dd-126">Specifies the output annotation file.</span></span>|  
|<span data-ttu-id="079dd-127">`/p:` *maxpasses*</span><span class="sxs-lookup"><span data-stu-id="079dd-127">`/p:` *maxpasses*</span></span><br /><br /> <span data-ttu-id="079dd-128">或</span><span class="sxs-lookup"><span data-stu-id="079dd-128">or</span></span><br /><br /> <span data-ttu-id="079dd-129">`/maximumpasses:` *maxpasses*</span><span class="sxs-lookup"><span data-stu-id="079dd-129">`/maximumpasses:` *maxpasses*</span></span>|<span data-ttu-id="079dd-130">指定停止產生新註釋前，嘗試傳遞組件註釋的最大值。</span><span class="sxs-lookup"><span data-stu-id="079dd-130">Specifies the maximum number of annotation passes to make on assemblies before stopping the generation of new annotations.</span></span>|  
|`/q`<br /><br /> <span data-ttu-id="079dd-131">或</span><span class="sxs-lookup"><span data-stu-id="079dd-131">or</span></span><br /><br /> `/quiet`|<span data-ttu-id="079dd-132">指定無訊息模式，在此模式中，註釋工具不會輸出狀態訊息，只會輸出錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="079dd-132">Specifies quiet mode, in which the annotator does not output status messages; it outputs only error information.</span></span>|  
|<span data-ttu-id="079dd-133">`/r:` *assembly*</span><span class="sxs-lookup"><span data-stu-id="079dd-133">`/r:` *assembly*</span></span><br /><br /> <span data-ttu-id="079dd-134">或</span><span class="sxs-lookup"><span data-stu-id="079dd-134">or</span></span><br /><br /> <span data-ttu-id="079dd-135">`/referenceassembly:` *assembly*</span><span class="sxs-lookup"><span data-stu-id="079dd-135">`/referenceassembly:` *assembly*</span></span>|<span data-ttu-id="079dd-136">註釋期間解析相依組件時包含指定的組件。</span><span class="sxs-lookup"><span data-stu-id="079dd-136">Includes the specified assembly when resolving dependent assemblies during annotation.</span></span> <span data-ttu-id="079dd-137">參考組件的優先順序高於參考路徑中的組件。</span><span class="sxs-lookup"><span data-stu-id="079dd-137">Reference assemblies are given priority over assemblies that are found in the reference path.</span></span>|  
|<span data-ttu-id="079dd-138">`/s:` *rulename*</span><span class="sxs-lookup"><span data-stu-id="079dd-138">`/s:` *rulename*</span></span><br /><br /> <span data-ttu-id="079dd-139">或</span><span class="sxs-lookup"><span data-stu-id="079dd-139">or</span></span><br /><br /> <span data-ttu-id="079dd-140">`/suppressrule:` *rulename*</span><span class="sxs-lookup"><span data-stu-id="079dd-140">`/suppressrule:` *rulename*</span></span>|<span data-ttu-id="079dd-141">隱藏執行輸入組件上的指定透明度規則。</span><span class="sxs-lookup"><span data-stu-id="079dd-141">Suppresses running the specified transparency rule on the input assemblies.</span></span>|  
|`/t`<br /><br /> <span data-ttu-id="079dd-142">或</span><span class="sxs-lookup"><span data-stu-id="079dd-142">or</span></span><br /><br /> `/forcetransparent`|<span data-ttu-id="079dd-143">強制 Annotator 工具將所有不具透明度註釋的組件視為完全透明。</span><span class="sxs-lookup"><span data-stu-id="079dd-143">Forces the Annotator tool to treat all assemblies that do not have any transparency annotations as if they were entirely transparent.</span></span>|  
|<span data-ttu-id="079dd-144">`/t`:*組件*</span><span class="sxs-lookup"><span data-stu-id="079dd-144">`/t`:*assembly*</span></span><br /><br /> <span data-ttu-id="079dd-145">或</span><span class="sxs-lookup"><span data-stu-id="079dd-145">or</span></span><br /><br /> <span data-ttu-id="079dd-146">`/forcetransparent`:*assembly*</span><span class="sxs-lookup"><span data-stu-id="079dd-146">`/forcetransparent`:*assembly*</span></span>|<span data-ttu-id="079dd-147">強制指定的組件呈現透明，無論目前組件層級註釋為何。</span><span class="sxs-lookup"><span data-stu-id="079dd-147">Force the given assembly to be transparent, regardless of its current assembly-level annotations.</span></span>|  
|||  
|`/v`<br /><br /> <span data-ttu-id="079dd-148">或</span><span class="sxs-lookup"><span data-stu-id="079dd-148">or</span></span><br /><br /> `/verify`|<span data-ttu-id="079dd-149">只用於驗證組件的註釋是否正確，如果組件並未驗證，請勿為了找出所有必要的註釋而嘗試多次傳遞。</span><span class="sxs-lookup"><span data-stu-id="079dd-149">Verifies only that an assembly's annotations are correct; does not attempt to make multiple passes to find all required annotations if the assembly does not verify.</span></span>|  
|`/x`<br /><br /> <span data-ttu-id="079dd-150">或</span><span class="sxs-lookup"><span data-stu-id="079dd-150">or</span></span><br /><br /> `/verbose`|<span data-ttu-id="079dd-151">指定標註提供詳細輸出。</span><span class="sxs-lookup"><span data-stu-id="079dd-151">Specifies verbose output while annotating.</span></span>|  
|<span data-ttu-id="079dd-152">`/y:` *directory*</span><span class="sxs-lookup"><span data-stu-id="079dd-152">`/y:` *directory*</span></span><br /><br /> <span data-ttu-id="079dd-153">或</span><span class="sxs-lookup"><span data-stu-id="079dd-153">or</span></span><br /><br /> <span data-ttu-id="079dd-154">`/symbolpath:` *directory*</span><span class="sxs-lookup"><span data-stu-id="079dd-154">`/symbolpath:` *directory*</span></span>|<span data-ttu-id="079dd-155">註釋期間搜尋符號檔時包含指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="079dd-155">Includes the specified directory when searching for symbol files during annotation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="079dd-156">備註</span><span class="sxs-lookup"><span data-stu-id="079dd-156">Remarks</span></span>  
 <span data-ttu-id="079dd-157">在命令列指定且前面加上一個 at 符號 (@) 的回應檔也可能會提供參數和組件。</span><span class="sxs-lookup"><span data-stu-id="079dd-157">Parameters and assemblies may also be provided in a response file that is specified on the command line and prefixed with an at sign (@).</span></span> <span data-ttu-id="079dd-158">回應檔中的每一行應該包含單一參數或組件名稱。</span><span class="sxs-lookup"><span data-stu-id="079dd-158">Each line in the response file should contain a single parameter or assembly name.</span></span>  
  
 <span data-ttu-id="079dd-159">如需 .NET Security Annotator 的詳細資訊，請參閱 .NET Security 部落格中的項目[使用 SecAnnotate 分析您的組件是否發生透明度違規](http://go.microsoft.com/fwlink/?LinkId=187648)。</span><span class="sxs-lookup"><span data-stu-id="079dd-159">For more information about the .NET Security Annotator, see the entry [Using SecAnnotate to Analyze Your Assemblies for Transparency Violations](http://go.microsoft.com/fwlink/?LinkId=187648) in the .NET Security blog.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="079dd-160">範例</span><span class="sxs-lookup"><span data-stu-id="079dd-160">Examples</span></span>
