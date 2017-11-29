---
title: "撰寫分析工具 (Mefx)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 740ba87fd247e05b1bc32e3732819514ba2806ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="38bca-102">撰寫分析工具 (Mefx)</span><span class="sxs-lookup"><span data-stu-id="38bca-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="38bca-103">撰寫分析工具 (Mefx) 是命令列應用程式，可分析包含 Managed Extensibility Framework (MEF) 組件的程式庫 (.dll) 和應用程式檔案 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="38bca-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="38bca-104">Mefx 的主要目的在於提供開發人員診斷其 MEF 應用程式中複合錯誤的方式，而不必將累贅的追蹤程式碼加入應用程式本身。</span><span class="sxs-lookup"><span data-stu-id="38bca-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="38bca-105">它還有助於了解協力廠商所提供程式庫的組件。</span><span class="sxs-lookup"><span data-stu-id="38bca-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="38bca-106">本主題說明如何使用 Mefx 及提供其語法的參考。</span><span class="sxs-lookup"><span data-stu-id="38bca-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="38bca-107">取得 Mefx</span><span class="sxs-lookup"><span data-stu-id="38bca-107">Getting Mefx</span></span>  
 <span data-ttu-id="38bca-108">Mefx 可在 GitHub 上[Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0)。</span><span class="sxs-lookup"><span data-stu-id="38bca-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="38bca-109">只要下載並解壓縮工具即可。</span><span class="sxs-lookup"><span data-stu-id="38bca-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="38bca-110">基本語法</span><span class="sxs-lookup"><span data-stu-id="38bca-110">Basic Syntax</span></span>  
 <span data-ttu-id="38bca-111">Mefx 是依照下列格式從命令列叫用：</span><span class="sxs-lookup"><span data-stu-id="38bca-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="38bca-112">第一個引數集會指定要從中載入組件進行分析的檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="38bca-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="38bca-113">使用 `/file:` 參數指定檔案，並使用 `/directory:` 參數指定目錄。</span><span class="sxs-lookup"><span data-stu-id="38bca-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="38bca-114">您可以指定多個檔案或目錄，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="38bca-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  <span data-ttu-id="38bca-115">每個 .dll 或 .exe 都應該只載入一次。</span><span class="sxs-lookup"><span data-stu-id="38bca-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="38bca-116">如果多次載入檔案，此工具可能傳回不正確的資訊。</span><span class="sxs-lookup"><span data-stu-id="38bca-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="38bca-117">在檔案與目錄清單之後，您必須指定命令，以及該命令使用的任何選項。</span><span class="sxs-lookup"><span data-stu-id="38bca-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="38bca-118">列出可用的組件</span><span class="sxs-lookup"><span data-stu-id="38bca-118">Listing Available Parts</span></span>  
 <span data-ttu-id="38bca-119">使用 `/parts` 動作列出所載入檔案中宣告的所有組件。</span><span class="sxs-lookup"><span data-stu-id="38bca-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="38bca-120">結果會產生簡單的組件名稱清單。</span><span class="sxs-lookup"><span data-stu-id="38bca-120">The result is a simple list of part names.</span></span>  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="38bca-121">如需組件的詳細資訊，請使用 `/verbose` 選項。</span><span class="sxs-lookup"><span data-stu-id="38bca-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="38bca-122">這樣將會輸出所有可用組件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="38bca-122">This will output more information for all available parts.</span></span> <span data-ttu-id="38bca-123">若要取得單一組件的詳細資訊，請使用 `/type` 動作，而非 `/parts`。</span><span class="sxs-lookup"><span data-stu-id="38bca-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="38bca-124">列出匯入和匯出</span><span class="sxs-lookup"><span data-stu-id="38bca-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="38bca-125">`/imports` 和 `/exports` 動作將分別列出所有匯入的組件和所有匯出的組件。</span><span class="sxs-lookup"><span data-stu-id="38bca-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="38bca-126">您也可以使用 `/importers` 或 `/exporters` 動作，列出匯入或匯出特定類型的組件。</span><span class="sxs-lookup"><span data-stu-id="38bca-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="38bca-127">您也可以將 `/verbose` 選項套用至這些動作。</span><span class="sxs-lookup"><span data-stu-id="38bca-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="38bca-128">尋找遭拒的組件</span><span class="sxs-lookup"><span data-stu-id="38bca-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="38bca-129">一旦 Mefx 載入了可用的組件，就會使用 MEF 組合引擎組合這些組件。</span><span class="sxs-lookup"><span data-stu-id="38bca-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="38bca-130">無法成功組合的組件即為 *「遭拒」*(rejected) 組件。</span><span class="sxs-lookup"><span data-stu-id="38bca-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="38bca-131">若要列出所有遭拒的組件，請使用 `/rejected` 動作。</span><span class="sxs-lookup"><span data-stu-id="38bca-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="38bca-132">您可以使用 `/verbose` 選項搭配 `/rejected` 動作，列印遭拒絕組件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="38bca-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="38bca-133">在下列範例中， `ClassLibrary1` DLL 包含 `AddIn` 組件，該組件會匯入 `MemberPart` 和 `ChainOne` 組件。</span><span class="sxs-lookup"><span data-stu-id="38bca-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="38bca-134">`ChainOne` 會匯入 `ChainTwo`，但是 `ChainTwo` 不存在。</span><span class="sxs-lookup"><span data-stu-id="38bca-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="38bca-135">這表示， `ChainOne` 遭拒，而這種情況會造成 `AddIn` 遭拒。</span><span class="sxs-lookup"><span data-stu-id="38bca-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="38bca-136">下面顯示前一個命令的完整輸出：</span><span class="sxs-lookup"><span data-stu-id="38bca-136">The following shows the complete output of the previous command:</span></span>  
  
```  
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="38bca-137">重點資訊包含在 `[Exception]` 和 `[Unsuitable]` 結果中。</span><span class="sxs-lookup"><span data-stu-id="38bca-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="38bca-138">`[Exception]` 結果會提供資訊，說明組件遭拒的原因。</span><span class="sxs-lookup"><span data-stu-id="38bca-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="38bca-139">`[Unsuitable]` 結果會指出其他方面相符的組件無法用來填入匯入的原因，而在此案例中，是因為遺漏之匯入的組件本身遭拒。</span><span class="sxs-lookup"><span data-stu-id="38bca-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="38bca-140">分析主要原因</span><span class="sxs-lookup"><span data-stu-id="38bca-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="38bca-141">如果有數個組件在較長的相依性鏈結中連結，則底部附近的組件相關問題可能造成整個鏈結遭拒。</span><span class="sxs-lookup"><span data-stu-id="38bca-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="38bca-142">診斷這些問題可能不容易，因為失敗的根本原因不一定很明顯。</span><span class="sxs-lookup"><span data-stu-id="38bca-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="38bca-143">為協助解決問題，您可以使用 `/causes` 動作，該動作會嘗試尋找任何階層式拒絕的根本原因。</span><span class="sxs-lookup"><span data-stu-id="38bca-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="38bca-144">在前面的範例中使用 `/causes` 動作，可能只會列出 `ChainOne`的資訊，它的未填入匯入就是 `AddIn`遭拒的根本原因。</span><span class="sxs-lookup"><span data-stu-id="38bca-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="38bca-145">`/causes` 動作可以同時在一般和 `/verbose` 選項中使用。</span><span class="sxs-lookup"><span data-stu-id="38bca-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38bca-146">大部分情況下，Mefx 都能夠診斷階層式失敗的根本原因。</span><span class="sxs-lookup"><span data-stu-id="38bca-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="38bca-147">不過，若組件是以程式設計的方式加入至容器、內含階層式容器的案例或內含自訂 `ExportProvider` 實作的案例，Mefx 就無法診斷原因。</span><span class="sxs-lookup"><span data-stu-id="38bca-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="38bca-148">一般而言，上述案例應盡量避免，因為失敗通常不易診斷出來。</span><span class="sxs-lookup"><span data-stu-id="38bca-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="38bca-149">允許清單</span><span class="sxs-lookup"><span data-stu-id="38bca-149">White Lists</span></span>  
 <span data-ttu-id="38bca-150">`/whitelist` 選項可讓您指定列出預期要拒絕之組件的文字檔。</span><span class="sxs-lookup"><span data-stu-id="38bca-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="38bca-151">非預期的拒絕將加上旗標。</span><span class="sxs-lookup"><span data-stu-id="38bca-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="38bca-152">當您分析不完整的程式庫或遺漏某些相依性的子程式庫時，這個選項可能會很實用。</span><span class="sxs-lookup"><span data-stu-id="38bca-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="38bca-153">`/whitelist` 選項可以套用至 `/rejected` 或 `/causes` 動作。</span><span class="sxs-lookup"><span data-stu-id="38bca-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="38bca-154">以名為 test.txt 且其中包含 "ClassLibrary1.ChainOne" 文字的檔案為例。</span><span class="sxs-lookup"><span data-stu-id="38bca-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="38bca-155">如果您對上述範例執行 `/rejected` 動作與 `/whitelist` 選項，它將會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="38bca-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
