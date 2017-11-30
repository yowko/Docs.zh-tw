---
title: "載入器 ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1643e5d645ec6c3ae35b2e57b8cb4f4bcb048379
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="loader-etw-events"></a>載入器 ETW 事件
<a name="top"></a> 這些事件收集載入及卸載應用程式定義域、組件和模組的相關資訊。  
  
 所有的載入器事件都會在 `LoaderKeyword` (0x8) 關鍵字底下引發。 `DCStart` 和 `DCEnd` 事件會在啟用 `StartRundown`/`EndRundown` 時，於 `LoaderRundownKeyword` (0x8) 底下引發。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。  
  
 載入器事件可細分為下列事件：  
  
-   [應用程式定義域事件](#application_domain_events)  
  
-   [CLR 載入器組件事件](#clr_loader_assembly_events)  
  
-   [模組事件](#module_events)  
  
-   [CLR 定義域模組事件](#clr_domain_module_events)  
  
-   [模組範圍事件](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>應用程式定義域事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|事件|層級|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` 和 `AppDomainUnLoad_V1`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|告知性 (4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1` (針對所有應用程式定義域記錄)|156|每當在處理序的存留期間建立應用程式定義域時引發。|  
|`AppDomainUnLoad_V1`|157|每當在處理序的存留期間終結應用程式定義域時引發。|  
|`AppDomainDCStart_V1`|157|在開始取消期間列舉應用程式定義域。|  
|`AppDomainDCEnd_V1`|158|在結束取消期間列舉應用程式定義域。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|應用程式定義域的唯一識別項。|  
|AppDomainFlags|win:UInt32|0x1：預設定義域。<br /><br /> 0x2：可執行檔。<br /><br /> 0x4：應用程式定義域，位元 28-31：這個定義域的共用原則。<br /><br /> 0：共用的定義域。|  
|AppDomainName|win:UnicodeString|易記的應用程式定義域名稱。 在處理序的存留期間可能會變更。|  
|AppDomainIndex|win:UInt32|這個應用程式定義域的索引。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>CLR 載入器組件事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|事件|層級|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` 和 `AssemblyUnload`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|告知性 (4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|載入組件時引發。|  
|`AssemblyUnload_V1`|155|卸載組件時引發。|  
|`AssemblyDCStart_V1`|155|在開始取消期間列舉組件。|  
|`AssemblyDCEnd_V1`|156|在結束取消期間列舉組件。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|AssemblyID|win:UInt64|組件的唯一 ID。|  
|AppDomainID|win:UInt64|這個組件之定義域的 ID。|  
|BindingID|win:UInt64|可唯一識別組件繫結的 ID。|  
|AssemblyFlags|win:UInt32|0x1：定義域中性組件。<br /><br /> 0x2：動態組件。<br /><br /> 0x4：組件具有原生映像。<br /><br /> 0x8：可回收組件。|  
|AssemblyName|win:UnicodeString|完整的組件名稱。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>模組事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|事件|層級|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` 和 `ModuleUnload_V2`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|告知性 (4)|  
||||  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|在處理序的存留期間載入模組時引發。|  
|`ModuleUnload_V2`|153|在處理序的存留期間卸載模組時引發。|  
|`ModuleDCStart_V2`|153|在開始取消期間列舉模組。|  
|`ModuleDCEnd_V2`|154|在結束取消期間列舉模組。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|模組的唯一 ID。|  
|AssemblyID|win:UInt64|這個模組所在之組件的 ID。|  
|ModuleFlags|win:UInt32|0x1：定義域中性模組。<br /><br /> 0x2：模組具有原生映像。<br /><br /> 0x4：動態模組。<br /><br /> 0x8：資訊清單模組。|  
|Reserved1|win:UInt32|保留的欄位。|  
|ModuleILPath|win:UnicodeString|模組之 Microsoft Intermediate Language (MSIL) 映像的路徑，或動態模組名稱 (如果它是動態組件 (以 Null 終止) 的話)。|  
|ModuleNativePath|win:UnicodeString|模組原生映像的路徑 (如果存在的話 (以 Null 終止))。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
|ManagedPdbSignature|win:GUID|符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。 (請參閱＜備註＞)。|  
|ManagedPdbAge|win:UInt32|寫入至受管理 PDB 並符合此模組的保留時間數值。 (請參閱＜備註＞)。|  
|ManagedPdbBuildPath|win:UnicodeString|符合此模組之受管理 PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。 (請參閱＜備註＞)。|  
|NativePdbSignature|win:GUID|符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。 (請參閱＜備註＞)。|  
|NativePdbAge|win:UInt32|寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。 (請參閱＜備註＞)。|  
|NativePdbBuildPath|win:UnicodeString|符合此模組之 NGen PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。 (請參閱＜備註＞)。|  
  
### <a name="remarks"></a>備註  
  
-   名稱中擁有 "Pdb" 的欄位可供程式碼剖析工具使用，以找出與剖析工作階段時載入之模組相符的 PDB。 這些欄位的值對應於寫入模組中 IMAGE_DIRECTORY_ENTRY_DEBUG 區段的資料，且通常用於偵錯工具以協助尋找符合已載入模組的 PDB。  
  
-   以 "ManagedPdb" 開頭的欄位名稱表示受管理的 PDB 所對應的 MSIL 模組，其是由受管理的編譯器 (例如 C# 或 Visual Basic 的編譯器) 所產生。 這個 PDB 會使用受管理的 PDB 格式，並描述各個項目如何從原始的受管理來源程式碼 (例如檔案、行號和符號名稱) 對應至編譯成 MSIL 模組的 MSIL 項目。  
  
-   以 "NativePdb" 開頭的欄位名稱表示該 NGen PDB 是透過呼叫 `NGEN createPDB`而產生。 這個 PDB 會使用受管理的 PDB 格式，並描述各個項目如何從原始的受管理來源程式碼 (例如檔案、行號和符號名稱) 對應至編譯成 NGen 模組的原生項目。  
  
 [回到頁首](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>CLR 定義域模組事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|事件|層級|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|告知性 (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|告知性 (4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|針對應用程式定義域載入模組時引發。|  
|`DomainModuleDCStart_V1`|151|在開始取消期間列舉針對應用程式定義域所載入的模組，並且針對所有應用程式定義域記錄。|  
|`DomainModuleDCEnd_V1`|152|在結束取消期間列舉針對應用程式定義域所載入的模組，並且針對所有應用程式定義域記錄。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|識別這個模組所屬的組件。|  
|AssemblyID|win:UInt64|這個模組所在之組件的 ID。|  
|AppDomainID|win:UInt64|使用這個模組之應用程式定義域的 ID。|  
|ModuleFlags|win:UInt32|0x1：定義域中性模組。<br /><br /> 0x2：模組具有原生映像。<br /><br /> 0x4：動態模組。<br /><br /> 0x8：資訊清單模組。|  
|Reserved1|win:UInt32|保留的欄位。|  
|ModuleILPath|win:UnicodeString|模組之 MSIL 映像的路徑，或動態模組名稱 (如果它是動態組件 (以 Null 終止) 的話)。|  
|ModuleNativePath|win:UnicodeString|模組原生映像的路徑 (如果存在的話 (以 Null 終止))。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>模組範圍事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|事件|層級|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|告知性 (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|告知性 (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|告知性 (4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|如果已載入的原生映像產生器 (NGen) 已使用 IBC 最佳化，就會出現這個事件，其中包含有關 NGen 映像作用範圍的資訊。|  
|`ModuleRangeDCStart`|160|在開始取消期間引發的 `ModuleRange` 事件。|  
|`ModuleRangeDCEnd`|161|在結束取消期間引發的 `ModuleRange` 事件。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:UInt16|載入 CLR 的多個執行個體時，可在處理序中唯一識別 CLR 的特定執行個體。|  
|ModuleID|win:UInt64|識別這個模組所屬的組件。|  
|RangeBegin|win:UInt32|模組中的位移，表示指定範圍類別的起始範圍。|  
|RangeSize|win:UInt32|指定範圍的大小 (以位元組為單位)。|  
|RangeType|win:UInt32|單一值 0x4，用來代表非作用 IBC 範圍。 此欄位在未來可以代表更多值。|  
|RangeSize1|win:UInt32|0 表示不正確的資料。|  
|RangeBegin2|win:UnicodeString||  
  
### <a name="remarks"></a>備註  
 如果 .NET Framework 處理序中載入的 NGen 影像已使用 IBC 最佳化，則包含 NGen 影像中作用範圍的 `ModuleRange` 事件會與其 `moduleID` 和 `ClrInstanceID`一起記錄。  如果 NGen 影像未經過 IBC 最佳化，則不會記錄這個事件。 若要判斷模組名稱，這個事件必須以模組載入 ETW 事件定序。  
  
 這個事件的承載大小是可變的， `Count` 欄位會指出事件中包含的範圍位移數。  這個事件必須以 Windows `IStart` 事件定序，以便判斷實際範圍。 每當載入影像時，就會記錄 Windows 影像載入事件，並且包含所載入影像的虛擬位址。  
  
 模組範圍事件會在任何 ETW 層級大於或等於 4 且分類為告知性事件時引發。  
  
## <a name="see-also"></a>另請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
