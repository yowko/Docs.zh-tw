---
title: EClrFailure 列舉
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f3e39d94996f14f1ae6593b9adaa5db3ef674c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769661"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure 列舉
描述的主機可以設定的原則動作失敗。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|嘗試配置的資源 （例如執行緒、 記憶體、 區塊或鎖定） 期間發生非關鍵的程式碼區域中的失敗。|  
|`FAIL_CriticalResource`|在關鍵區域的程式碼中，嘗試配置的資源 （例如執行緒、 記憶體、 區塊或鎖定） 期間發生失敗。|  
|`FAIL_FatalRuntime`|Common language runtime (CLR) 已不再能夠執行程序中的 managed 程式碼。 從此以後，任何裝載的函式的呼叫會傳回 HOST_E_CLRNOTAVAILABLE HRESULT 值。|  
|`FAIL_OrphanedLock`|執行緒無法釋放鎖定時<xref:System.AppDomain>物件。 主應用程式無法設定此失敗會造成執行緒中止。|  
|`FAIL_StackOverflow`|發生堆疊溢位。|  
|`FAIL_AccessViolation`|嘗試讀取或寫入受保護的記憶體。 不支援在.NET Framework 4。|  
|`FAIL_CodeContract`|程式碼合約失敗。 請參閱[程式碼合約](../../../../docs/framework/debug-trace-profile/code-contracts.md)。|  
  
## <a name="remarks"></a>備註  
 請參閱[iclrpolicymanager:: Setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)方法，取得一份[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)主應用程式可用來指定原則動作失敗狀況的值。 程式碼的重大和非關鍵區域的相關資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnFailure 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
