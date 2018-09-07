---
title: STARTUP_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4680187de7318a6438bf6a5e6bd7c5f3acd05c2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44059933"
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS 列舉
包含值，表示 common language runtime (CLR) 的啟動行為。 根據預設，記憶體回收是非並行，而且只有基底類別程式庫載入定義域中性的區域。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|指定應該使用並行記憶體回收。 如果呼叫端要求的伺服器組建和並行記憶體回收在單一處理器電腦上，工作站組建和非並行記憶體回收會改為執行。 **注意：** WOW64 執行的應用程式中不支援並行記憶體回收 x86 實作 Intel Itanium 架構 （先前稱為 IA-64） 的 64 位元系統上的模擬器。 如需在 64 位元 Windows 系統上使用 WOW64 的詳細資訊，請參閱[執行的 32 位元應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|指定應該進行的載入器最佳化。|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|指定不以定義域中性方式載入任何組件。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|指定的所有組件以定義域中性方式載入。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|指定所有的強式名稱組件會載入為網域中性。|  
|`STARTUP_LOADER_SAFEMODE`|指定 CLR 版本原則不會套用至傳遞的版本。 會載入指定的 clr 的確切版本。 填充碼不會評估原則，以判斷最新的相容版本。|  
|`STARTUP_LOADER_SETPREFERENCE`|指定慣用的執行階段會設定，但不是會實際啟動。|  
|`STARTUP_SERVER_GC`|指定將會使用伺服器記憶體回收。|  
|`STARTUP_HOARD_GC_VM`|指定記憶體回收會保留所使用的虛擬位址。|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|指定不會允許混用裝載介面。|  
|`STARTUP_LEGACY_IMPERSONATION`|指定的模擬應該不流經非同步點預設。|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|指定完整執行緒堆疊不應該認可時在執行緒開始執行。|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|指定受管理的模擬和模擬可透過平台叫用會流經非同步點。 根據預設，只有受管理的模擬會流經非同步點。|  
|`STARTUP_TRIM_GC_COMMIT`|指定記憶體回收在系統記憶體偏低時，將使用較不認可的空間。 請參閱`gcTrimCommitOnLowMemory`中[共用的 Web 裝載的最佳化](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)。|  
|`STARTUP_ETW`|指定通用語言執行階段事件，會啟用事件追蹤的 Windows (ETW)。 從 Windows Vista 開始，事件追蹤會永遠啟用，因此這個旗標不有任何效果。 請參閱[控制.NET Framework 記錄](../../../../docs/framework/performance/controlling-logging.md)。|  
|`STARTUP_ARM`|指定啟用應用程式定義域資源監視。 請參閱<xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>屬性和[ \<appDomainResourceMonitoring > 項目](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
