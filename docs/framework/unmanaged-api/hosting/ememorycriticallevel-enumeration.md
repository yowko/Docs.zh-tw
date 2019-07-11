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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774225"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 列舉
包含值，表示失敗的影響，當有特定記憶體配置已要求但不能滿足。  
  
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
|`eAppDomainCritical`|指出配置已要求配置的網域中執行 managed 程式碼的重要。 如果無法配置記憶體，CLR 不保證仍可使用定義域。 主應用程式會決定當無法滿足配置時要採取什麼動作。 它可以指示 CLR 在中止`AppDomain`自動執行，或允許它繼續執行上呼叫方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。|  
|`eProcessCritical`|指出配置重要的程序中的 managed 程式碼執行。 這個值可在啟動期間，當執行完成項。 如果無法配置記憶體，CLR 無法在程序。 如果配置失敗，CLR 會有效地停用。 所有後續的呼叫，clr 會失敗並 HOST_E_CLRNOTAVAILABLE。|  
|`eTaskCritical`|表示配置務必執行之工作的要求配置。 如果無法配置記憶體，CLR 不保證可以執行此工作。 如果發生失敗，CLR 會引發<xref:System.Threading.ThreadAbortException>實體作業系統執行緒上。|  
  
## <a name="remarks"></a>備註  
 中所定義的記憶體配置方法[IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)並[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)介面採用這種類型的參數。 失敗的嚴重性而定，主機可以決定是否要立即拒絕配置要求，或等候，直到可以滿足。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMemoryNotificationCallback 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
