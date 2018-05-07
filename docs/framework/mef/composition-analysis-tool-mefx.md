---
title: 撰寫分析工具 (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6851ac334d439f2e5c0f6056f5226e3faa1503d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="composition-analysis-tool-mefx"></a>撰寫分析工具 (Mefx)
撰寫分析工具 (Mefx) 是命令列應用程式，可分析包含 Managed Extensibility Framework (MEF) 組件的程式庫 (.dll) 和應用程式檔案 (.exe)。 Mefx 的主要目的在於提供開發人員診斷其 MEF 應用程式中複合錯誤的方式，而不必將累贅的追蹤程式碼加入應用程式本身。 它還有助於了解協力廠商所提供程式庫的組件。 本主題說明如何使用 Mefx 及提供其語法的參考。  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>取得 Mefx  
 Mefx 可在 GitHub 上[Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0)。 只要下載並解壓縮工具即可。  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>基本語法  
 Mefx 是依照下列格式從命令列叫用：  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 第一個引數集會指定要從中載入組件進行分析的檔案和目錄。 使用 `/file:` 參數指定檔案，並使用 `/directory:` 參數指定目錄。 您可以指定多個檔案或目錄，如下列範例所示：  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  每個 .dll 或 .exe 都應該只載入一次。 如果多次載入檔案，此工具可能傳回不正確的資訊。  
  
 在檔案與目錄清單之後，您必須指定命令，以及該命令使用的任何選項。  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>列出可用的組件  
 使用 `/parts` 動作列出所載入檔案中宣告的所有組件。 結果會產生簡單的組件名稱清單。  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 如需組件的詳細資訊，請使用 `/verbose` 選項。 這樣將會輸出所有可用組件的詳細資訊。 若要取得單一組件的詳細資訊，請使用 `/type` 動作，而非 `/parts`。  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>列出匯入和匯出  
 `/imports` 和 `/exports` 動作將分別列出所有匯入的組件和所有匯出的組件。 您也可以使用 `/importers` 或 `/exporters` 動作，列出匯入或匯出特定類型的組件。  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 您也可以將 `/verbose` 選項套用至這些動作。  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>尋找遭拒的組件  
 一旦 Mefx 載入了可用的組件，就會使用 MEF 組合引擎組合這些組件。 無法成功組合的組件即為 *「遭拒」*(rejected) 組件。 若要列出所有遭拒的組件，請使用 `/rejected` 動作。  
  
 您可以使用 `/verbose` 選項搭配 `/rejected` 動作，列印遭拒絕組件的詳細資訊。 在下列範例中， `ClassLibrary1` DLL 包含 `AddIn` 組件，該組件會匯入 `MemberPart` 和 `ChainOne` 組件。 `ChainOne` 會匯入 `ChainTwo`，但是 `ChainTwo` 不存在。 這表示， `ChainOne` 遭拒，而這種情況會造成 `AddIn` 遭拒。  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 下面顯示前一個命令的完整輸出：  
  
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
  
 重點資訊包含在 `[Exception]` 和 `[Unsuitable]` 結果中。 `[Exception]` 結果會提供資訊，說明組件遭拒的原因。 `[Unsuitable]` 結果會指出其他方面相符的組件無法用來填入匯入的原因，而在此案例中，是因為遺漏之匯入的組件本身遭拒。  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>分析主要原因  
 如果有數個組件在較長的相依性鏈結中連結，則底部附近的組件相關問題可能造成整個鏈結遭拒。 診斷這些問題可能不容易，因為失敗的根本原因不一定很明顯。 為協助解決問題，您可以使用 `/causes` 動作，該動作會嘗試尋找任何階層式拒絕的根本原因。  
  
 在前面的範例中使用 `/causes` 動作，可能只會列出 `ChainOne`的資訊，它的未填入匯入就是 `AddIn`遭拒的根本原因。 `/causes` 動作可以同時在一般和 `/verbose` 選項中使用。  
  
> [!NOTE]
>  大部分情況下，Mefx 都能夠診斷階層式失敗的根本原因。 不過，若組件是以程式設計的方式加入至容器、內含階層式容器的案例或內含自訂 `ExportProvider` 實作的案例，Mefx 就無法診斷原因。 一般而言，上述案例應盡量避免，因為失敗通常不易診斷出來。  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>允許清單  
 `/whitelist` 選項可讓您指定列出預期要拒絕之組件的文字檔。 非預期的拒絕將加上旗標。 當您分析不完整的程式庫或遺漏某些相依性的子程式庫時，這個選項可能會很實用。 `/whitelist` 選項可以套用至 `/rejected` 或 `/causes` 動作。  
  
 以名為 test.txt 且其中包含 "ClassLibrary1.ChainOne" 文字的檔案為例。 如果您對上述範例執行 `/rejected` 動作與 `/whitelist` 選項，它將會產生下列輸出：  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
