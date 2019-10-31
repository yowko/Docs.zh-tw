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
ms.openlocfilehash: 7d935bff023d806cf8cfb6d87bde0f82666b51b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131117"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure 列舉
描述主機可以設定原則動作的失敗集。  
  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|嘗試在不重要的程式碼區域中配置資源（例如執行緒、記憶體區塊或鎖定）時發生失敗。|  
|`FAIL_CriticalResource`|嘗試在程式碼的關鍵區域中配置資源（例如執行緒、記憶體區塊或鎖定）時發生失敗。|  
|`FAIL_FatalRuntime`|Common language runtime （CLR）不再能夠在進程中執行 managed 程式碼。 因而需要，對任何裝載函數的呼叫都會傳回 HRESULT 值 HOST_E_CLRNOTAVAILABLE。|  
|`FAIL_OrphanedLock`|執行緒無法在從 <xref:System.AppDomain> 物件傳回時釋放鎖定。 主機無法設定此失敗，導致執行緒中止。|  
|`FAIL_StackOverflow`|發生堆疊溢位。|  
|`FAIL_AccessViolation`|嘗試讀取或寫入受保護的記憶體。 在 .NET Framework 4 中不支援。|  
|`FAIL_CodeContract`|發生程式碼合約失敗。 請參閱程式[代碼合約](../../../../docs/framework/debug-trace-profile/code-contracts.md)。|  
  
## <a name="remarks"></a>備註  
 請參閱[ICLRPolicyManager：： SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)方法，以取得可供主機用來指定失敗狀況之原則動作的[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值清單。 如需程式碼重要和非關鍵區域的詳細資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnFailure 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
