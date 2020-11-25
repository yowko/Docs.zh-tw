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
ms.openlocfilehash: 3b9ad4b40ce94420f2ab5fc25335c41dec15dc09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720545"
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
  
|member|描述|  
|------------|-----------------|  
|`eAppDomainCritical`|指出在已要求配置的網域中執行 managed 程式碼時，配置是不可或缺的。 如果無法配置記憶體，則 CLR 無法保證網域仍可使用。 主機決定無法滿足配置時要採取的動作。 它可以指示 CLR 中止 `AppDomain` 自動，或在 [ICLRPolicyManager](iclrpolicymanager-interface.md)上呼叫方法來讓它繼續執行。|  
|`eProcessCritical`|表示配置對於進程中的 managed 程式碼執行而言是不可或缺的。 在啟動和執行完成項時，會使用這個值。 如果無法配置記憶體，則 CLR 無法在進程中操作。 如果配置失敗，則會有效停用 CLR。 對 CLR 的所有後續呼叫都會失敗並 HOST_E_CLRNOTAVAILABLE。|  
|`eTaskCritical`|表示執行已要求配置的工作時，配置是不可或缺的。 如果無法配置記憶體，則 CLR 無法保證可以執行此工作。 發生失敗時，CLR 會 <xref:System.Threading.ThreadAbortException> 在實體作業系統執行緒上引發。|  
  
## <a name="remarks"></a>備註  

 [IHostMemoryManager](ihostmemorymanager-interface.md)和[IHostMAlloc](ihostmalloc-interface.md)介面中定義的記憶體配置方法會採用此類型的參數。 根據失敗的嚴重性而定，主機可以決定是否要立即讓配置要求失敗，或等到可以滿足此要求為止。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMemoryNotificationCallback 介面](iclrmemorynotificationcallback-interface.md)
- [裝載列舉](hosting-enumerations.md)
