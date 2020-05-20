---
title: 裝載列舉
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
ms.openlocfilehash: e6fb22f91d57a356a9a7c3749e44a9fb3c36b699
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616108"
---
# <a name="hosting-enumerations"></a>裝載列舉
本節說明裝載 API 所使用的非受控列舉。  
  
## <a name="in-this-section"></a>本節內容  
 [CLSID_RESOLUTION_FLAGS 列舉](clsid-resolution-flags-enumeration.md)  
 包含表示 common language runtime （CLR）應如何解析的值 `CLSID` 。  
  
 [COR_GC_STAT_TYPES 列舉](cor-gc-stat-types-enumeration.md)  
 指定要記錄以進行垃圾收集的統計資料。  
  
 [COR_GC_THREAD_STATS_TYPES 列舉](cor-gc-thread-stats-types-enumeration.md)  
 表示執行緒的垃圾收集統計資料。  
  
 [EApiCategories 列舉](eapicategories-enumeration.md)  
 描述主機可以封鎖在部分信任程式碼中執行的功能類別。  
  
 [EBindPolicyLevels 列舉](ebindpolicylevels-enumeration.md)  
 提供旗標，用來指定要套用或修改元件原則的層級。  
  
 [ECLRAssemblyIdentityFlags 列舉](eclrassemblyidentityflags-enumeration.md)  
 表示元件的身分識別類型。  
  
 [EClrEvent 列舉](eclrevent-enumeration.md)  
 描述主機可以註冊回呼的 CLR 事件。  
  
 [EClrFailure 列舉](eclrfailure-enumeration.md)  
 描述主機可以設定原則動作的失敗集。  
  
 [EClrOperation 列舉](eclroperation-enumeration.md)  
 描述主機可以套用原則動作的一組作業。  
  
 [EClrUnhandledException 列舉](eclrunhandledexception-enumeration.md)  
 描述可用來管理使用者程式碼中未處理之例外狀況的選項。  
  
 [EContextType 列舉](econtexttype-enumeration.md)  
 描述目前執行中線程的安全性內容。  
  
 [ECustomDumpFlavor 列舉](ecustomdumpflavor-enumeration.md)  
 包含值，指出報告錯誤時，要包含在堆積傾印的自訂子集中的專案。  
  
 [ECustomDumpItemKind 列舉](ecustomdumpitemkind-enumeration.md)  
 保留以供未來[CustomDumpItem 結構](customdumpitem-structure.md)結構的延伸。  
  
 [EHostApplicationPolicy 列舉](ehostapplicationpolicy-enumeration.md)  
 表示如何修改[IHostAssemblyManager 介面](ihostassemblymanager-interface.md)介面物件。 這個列舉已被取代。  
  
 [EHostBindingPolicyModifyFlags 列舉](ehostbindingpolicymodifyflags-enumeration.md)  
 允許主機指定 CLR 在將原則修改從來源元件套用至目標群組件時，應執行的重新導向類型。  
  
 [EInitializeNewDomainFlags 列舉](einitializenewdomainflags-enumeration.md)  
 讓主機為執行時間提供初始化應用程式域的相關資訊。  
  
 [EMemoryAvailable 列舉](ememoryavailable-enumeration.md)  
 包含值，指出電腦上的可用實體記憶體數量。  
  
 [EMemoryCriticalLevel 列舉](ememorycriticallevel-enumeration.md)  
 包含值，指出當要求特定記憶體配置但無法滿足時，失敗的影響。  
  
 [EPolicyAction 列舉](epolicyaction-enumeration.md)  
 描述主機可以針對[EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)所描述的作業設定的原則動作，以及[EClrFailure 列舉](eclrfailure-enumeration.md)所描述的失敗。  
  
 [ESymbolReadingPolicy 列舉](esymbolreadingpolicy-enumeration.md)  
 包含設定讀取程式資料庫（PDB）檔案之原則的值。  
  
 [ETaskType 列舉](etasktype-enumeration.md)  
 包含值，指出[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)或[IHostTask 介面](ihosttask-interface.md)介面所代表的工作種類。  
  
 [HOST_TYPE 列舉](host-type-enumeration.md)  
 包含值，指定啟動應用程式的主控制項類型。  
  
 [MALLOC_TYPE 列舉](malloc-type-enumeration.md)  
 包含值，指定所配置記憶體的特性。  
  
 [METAHOST_CONFIG_FLAGS 列舉](metahost-config-flags-enumeration.md)  
 描述在 `pdwConfigFlags` [ICLRMetaHostPolicy：： GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md)方法的參數中傳回的可能旗標。  
  
 [METAHOST_POLICY_FLAGS 列舉](metahost-policy-flags-enumeration.md)  
 提供大部分執行時間主機通用的系結原則。  
  
 [RUNTIME_INFO_FLAGS 列舉](runtime-info-flags-enumeration.md)  
 包含值，指出應該傳回的 CLR 相關資訊。  
  
 [StackOverflowType 列舉](stackoverflowtype-enumeration.md)  
 包含值，指出堆疊溢位事件的根本原因。  
  
 [STARTUP_FLAGS 列舉](startup-flags-enumeration.md)  
 包含值，表示 CLR 的啟動行為。  
  
 [ValidatorFlags 列舉](validatorflags-enumeration.md)  
 包含值，指出應該在[驗證方法](iclrvalidator-validate-method.md)的呼叫中執行的驗證類型。  
  
 [WAIT_OPTION 列舉](wait-option-enumeration.md)  
 指出 CLR 區塊要求的作業時，主機應採取的動作。  
  
## <a name="related-sections"></a>相關章節  
 [裝載 Coclass](hosting-coclasses.md)  
  
 [裝載介面](hosting-interfaces.md)  
  
 [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)  
  
 [裝載結構](hosting-structures.md)
