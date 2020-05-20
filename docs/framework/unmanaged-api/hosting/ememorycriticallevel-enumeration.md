---
title: EMemoryCriticalLevel 列舉
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 248f1d281697923e2da14517ca174fe615bba4ff
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616199"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 列舉
包含值，指出當要求特定記憶體配置但無法滿足時，失敗的影響。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`eAppDomainCritical`|表示在要求配置的網域中執行 managed 程式碼時，配置是非常重要的。 如果無法配置記憶體，CLR 就無法保證該網域仍然可用。 主機會決定無法滿足配置時要採取的動作。 它可以指示 CLR `AppDomain` 自動中止，或藉由在[ICLRPolicyManager](iclrpolicymanager-interface.md)上呼叫方法，讓它繼續運作。|  
|`eProcessCritical`|表示配置對於進程中的 managed 程式碼執行而言非常重要。 這個值會在啟動期間和執行完成項時使用。 如果無法配置記憶體，CLR 就無法在進程中運作。 如果配置失敗，CLR 會有效地停用。 所有對 CLR 的後續呼叫都會失敗，並 HOST_E_CLRNOTAVAILABLE。|  
|`eTaskCritical`|指出配置對於執行已要求配置的工作而言非常重要。 如果無法配置記憶體，CLR 就無法保證可以執行工作。 發生失敗時，CLR 會在 <xref:System.Threading.ThreadAbortException> 實體作業系統執行緒上引發。|  
  
## <a name="remarks"></a>備註  
 [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)和[IHostMAlloc](ihostmalloc-interface.md)介面中定義的記憶體配置方法會採用此類型的參數。 視失敗的嚴重性而定，主機可以決定是否要立即讓配置要求失敗，或等到它可以滿足為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMemoryNotificationCallback 介面](iclrmemorynotificationcallback-interface.md)
- [裝載列舉](hosting-enumerations.md)
