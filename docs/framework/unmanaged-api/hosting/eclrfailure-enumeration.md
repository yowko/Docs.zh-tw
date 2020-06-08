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
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504390"
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
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|嘗試在不重要的程式碼區域中配置資源（例如執行緒、記憶體區塊或鎖定）時發生失敗。|  
|`FAIL_CriticalResource`|嘗試在程式碼的關鍵區域中配置資源（例如執行緒、記憶體區塊或鎖定）時發生失敗。|  
|`FAIL_FatalRuntime`|Common language runtime （CLR）不再能夠在進程中執行 managed 程式碼。 因而需要，對任何裝載函數的呼叫都會傳回 HRESULT 值 HOST_E_CLRNOTAVAILABLE。|  
|`FAIL_OrphanedLock`|執行緒無法在從物件傳回時釋放鎖定 <xref:System.AppDomain> 。 主機無法設定此失敗，導致執行緒中止。|  
|`FAIL_StackOverflow`|發生堆疊溢位。|  
|`FAIL_AccessViolation`|嘗試讀取或寫入受保護的記憶體。 在 .NET Framework 4 中不支援。|  
|`FAIL_CodeContract`|發生程式碼合約失敗。 請參閱程式[代碼合約](../../debug-trace-profile/code-contracts.md)。|  
  
## <a name="remarks"></a>備註  
 請參閱[ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)方法，以取得可供主機用來指定失敗狀況之原則動作的[EPolicyAction](epolicyaction-enumeration.md)值清單。 如需程式碼重要和非關鍵區域的詳細資訊，請參閱[EClrOperation](eclroperation-enumeration.md)。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [SetActionOnFailure 方法](iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager 介面](ihostpolicymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
