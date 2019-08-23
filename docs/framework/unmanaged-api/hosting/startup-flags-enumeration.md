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
ms.openlocfilehash: f39608b39be7d5c25b916fb20877aa73d6e5a8bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916225"
---
# <a name="startup_flags-enumeration"></a>STARTUP_FLAGS 列舉
包含值, 表示 common language runtime (CLR) 的啟動行為。 根據預設, 垃圾收集是非並行的, 而且只有基類庫會載入至網域中立區域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
|`STARTUP_CONCURRENT_GC`|指定應該使用並行垃圾收集。 如果呼叫者要求在單處理器機器上進行伺服器組建和並行垃圾收集, 則會改為執行工作站組建和非並行垃圾收集。 **注意：** 在執行 Intel Itanium 架構 (先前稱為 IA-64) 的64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集。 如需在64位 Windows 系統上使用 WOW64 的詳細資訊, 請參閱執行[32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|指定應該進行載入器優化。|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|指定不將任何元件載入為網域中性。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|指定將所有元件載入為網域中性。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|指定將所有強式名稱的元件載入為網域中性。|  
|`STARTUP_LOADER_SAFEMODE`|指定 CLR 版本原則將不會套用至傳入的版本。 將會載入指定之 CLR 的確切版本。 填充碼不會評估原則來判斷最新的相容版本。|  
|`STARTUP_LOADER_SETPREFERENCE`|指定慣用的執行時間將會設定, 但不會實際啟動。|  
|`STARTUP_SERVER_GC`|指定將使用伺服器垃圾收集。|  
|`STARTUP_HOARD_GC_VM`|指定垃圾收集會保留使用的虛擬位址。|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|指定不允許混用主控介面。|  
|`STARTUP_LEGACY_IMPERSONATION`|指定模擬預設不應流經非同步點。|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|指定當執行緒開始執行時, 不應認可完整執行緒堆疊。|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|指定透過平台叫用達成的 managed 模擬和模擬會流經非同步點。 根據預設, 只有受管理的模擬會流經非同步點。|  
|`STARTUP_TRIM_GC_COMMIT`|指定當系統記憶體不足時, 垃圾收集會使用較少的認可空間。 請`gcTrimCommitOnLowMemory`參閱[共用 Web 裝載的優化](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md)。|  
|`STARTUP_ETW`|指定針對 common language runtime 事件啟用 Windows 事件追蹤 (ETW)。 從 Windows Vista 開始, 一律會啟用事件追蹤, 因此此旗標沒有任何作用。 請參閱[控制 .NET Framework 記錄](../../../../docs/framework/performance/controlling-logging.md)。|  
|`STARTUP_ARM`|指定啟用應用程式域資源監視。 請參閱[ \<屬性和appDomainResourceMonitoring > 元素。](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
