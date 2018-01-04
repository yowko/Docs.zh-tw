---
title: "裝載列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc6b5df39c9fad6182f0ee6e4ff95638e9aaf448
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-enumerations"></a>裝載列舉
本章節描述裝載 API 所使用的 unmanaged 的列舉。  
  
## <a name="in-this-section"></a>本節內容  
 [CLSID_RESOLUTION_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/clsid-resolution-flags-enumeration.md)  
 包含值，表示 common language runtime (CLR) 應該要如何解決`CLSID`。  
  
 [COR_GC_STAT_TYPES 列舉](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 指定要記錄的回收統計資料。  
  
 [COR_GC_THREAD_STATS_TYPES 列舉](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-types-enumeration.md)  
 指出執行緒的記憶體回收集合統計資料。  
  
 [EApiCategories 列舉](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 描述分類的主機可以封鎖無法在部分信任程式碼中執行的功能。  
  
 [EBindPolicyLevels 列舉](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)  
 提供指定的層級套用或修改組件原則的旗標。  
  
 [ECLRAssemblyIdentityFlags 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)  
 表示組件的識別類型。  
  
 [EClrEvent 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 描述主機可以註冊回呼的 CLR 事件。  
  
 [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 描述的主機可以設定原則動作失敗。  
  
 [EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 描述一組作業，主機可以套用原則的動作。  
  
 [EClrUnhandledException 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 描述可用於管理使用者程式碼中未處理的例外狀況的選項。  
  
 [EContextType 列舉](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 描述目前執行中執行緒的安全性內容。  
  
 [ECustomDumpFlavor 列舉](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 包含值，表示哪些項目来納入的自訂子堆積的傾印時報告錯誤。  
  
 [ECustomDumpItemKind 列舉](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 保留供未來擴充功能的[CustomDumpItem 結構](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)結構。  
  
 [EHostApplicationPolicy 列舉](../../../../docs/framework/unmanaged-api/hosting/ehostapplicationpolicy-enumeration.md)  
 指出如何修改[IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)介面物件。 這個列舉型別已被取代。  
  
 [EHostBindingPolicyModifyFlags 列舉](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)  
 可讓主機指定的重新導向時套用至目標組件的原則修改從來源組件，應執行 CLR 類型。  
  
 [EInitializeNewDomainFlags 列舉](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)  
 可讓主機提供的執行階段相關的應用程式定義域初始化資訊。  
  
 [EMemoryAvailable 列舉](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)  
 包含值，表示電腦上的可用實體記憶體數量。  
  
 [EMemoryCriticalLevel 列舉](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)  
 包含值，表示故障的影響，當有特定記憶體配置要求卻無法滿足。  
  
 [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 描述所描述的作業可以設定主機的原則動作[EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)和所描述的失敗[EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)。  
  
 [ESymbolReadingPolicy 列舉](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md)  
 包含值，設定原則的讀取程式資料庫 (PDB) 檔案。  
  
 [ETaskType 列舉](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md)  
 包含值，表示工作所代表類型[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)或[IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)介面。  
  
 [HOST_TYPE 列舉](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)  
 包含指定的啟動應用程式的主機類型的值。  
  
 [MALLOC_TYPE 列舉](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md)  
 包含值，指定所配置的記憶體的特性。  
  
 [METAHOST_CONFIG_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md)  
 描述可能的旗標中傳回`pdwConfigFlags`參數[iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法。  
  
 [METAHOST_POLICY_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)  
 提供通用於大多數的執行階段主機的繫結原則。  
  
 [RUNTIME_INFO_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)  
 包含值，表示應傳回在 CLR 的相關資訊。  
  
 [StackOverflowType 列舉](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)  
 包含值，表示造成堆疊溢位事件的根本原因。  
  
 [STARTUP_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
 包含值，表示 CLR 的啟動行為。  
  
 [ValidatorFlags 列舉](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)  
 包含值，表示應該執行的呼叫中的驗證類型[驗證方法](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)。  
  
 [WAIT_OPTION 列舉](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)  
 指出如果 CLR 區塊所要求的作業，主機應該採取的動作。  
  
## <a name="related-sections"></a>相關章節  
 [裝載 Coclass](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
