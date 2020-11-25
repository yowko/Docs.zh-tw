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
ms.openlocfilehash: 3c3f4d644bd7073655d2d77fe7f65a3a46cfea24
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729898"
---
# <a name="startup_flags-enumeration"></a>STARTUP_FLAGS 列舉

包含值，指出 common language runtime (CLR) 的啟動行為。 依預設，垃圾收集並非並行的，而且只會將基底類別庫載入至網域中立的區域。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|指定應該使用並行垃圾收集。 如果呼叫端要求在單處理器電腦上進行伺服器組建和並行垃圾收集，則會改為執行工作站組建和非並行垃圾收集。 **注意：**  在64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集，這些系統會執行先前稱為 IA-64) 的 Intel Itanium 架構 (。 如需在64位 Windows 系統上使用 WOW64 的詳細資訊，請參閱執行 [32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|指定應進行載入器優化。|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|指定不將任何元件載入為網域中性。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|指定將所有元件載入為網域中性。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|指定將所有強式名稱的元件載入為網域中性。|  
|`STARTUP_LOADER_SAFEMODE`|指定 CLR 版本原則將不會套用至傳入的版本。 將載入 CLR 指定的確切版本。 填充碼不會評估原則以判斷最新的相容版本。|  
|`STARTUP_LOADER_SETPREFERENCE`|指定將設定慣用的執行時間，但不會實際啟動。|  
|`STARTUP_SERVER_GC`|指定將使用伺服器垃圾收集。|  
|`STARTUP_HOARD_GC_VM`|指定垃圾收集將保留使用的虛擬位址。|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|指定將不會允許混合裝載介面。|  
|`STARTUP_LEGACY_IMPERSONATION`|指定模擬預設不應流經非同步點。|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|指定當執行緒開始執行時，不應認可完整執行緒堆疊。|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|指定透過平台叫用達成的 managed 模擬和模擬會在非同步點之間流動。 依預設，只有 managed 模擬會在非同步點之間流動。|  
|`STARTUP_TRIM_GC_COMMIT`|指定當系統記憶體不足時，垃圾收集會使用較少認可的空間。 請 `gcTrimCommitOnLowMemory` 參閱 [共用 Web 裝載的優化](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md)。|  
|`STARTUP_ETW`|指定針對通用語言運行時間事件啟用 Windows (ETW) 的事件追蹤。 從 Windows Vista 開始，一律會啟用事件追蹤，因此此旗標不會有任何作用。 請參閱 [控制 .NET Framework 記錄](../../performance/controlling-logging.md)。|  
|`STARTUP_ARM`|指定啟用應用程式域資源監視。 請參閱 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> 屬性和[ \<appDomainResourceMonitoring> 元素](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
