---
title: EPolicyAction 列舉
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138237"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction 列舉
描述主機可以針對[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)所描述的作業設定的原則動作，以及[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)所描述的失敗。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`eAbortThread`|指定 common language runtime （CLR）應正常中止執行緒。 「正常中止」包括嘗試執行所有 `finally` 區塊、與執行緒中止相關的任何 `catch` 區塊，以及完成項。|  
|`eDisableRuntime`|指定 CLR 應進入停用狀態。 在受影響的進程中無法執行進一步的 managed 程式碼，而且執行緒會遭到封鎖而無法進入 CLR。|  
|`eExitProcess`|指定 CLR 應該嘗試順利結束進程，包括執行完成項和執行清除和記錄作業。|  
|`eFastExitProcess`|指定 CLR 應該立即結束進程，而不執行完成項或清除和記錄作業。 不過，通知會傳送至偵錯工具。|  
|`eNoAction`|指定不採取任何動作。|  
|`eRudeAbortThread`|指定 CLR 應該執行強制執行緒中止。 只有標示 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 的 `catch` 和 `finally` 區塊才會執行。|  
|`eRudeExitProcess`|指定 CLR 應該結束進程，而不執行完成項或記錄作業。|  
|`eRudeUnloadAppDomain`|指定 CLR 應該執行 <xref:System.AppDomain>的強制卸載。 只會執行標示為 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 的完成項。 同樣地，此 <xref:System.AppDomain> 在其堆疊中的所有線程都會收到 `ThreadAbortException`，但只會執行標示為 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 的 `catch` 和 `finally` 區塊。|  
|`eThrowException`|指定應該擲回條件適用的例外狀況，例如記憶體不足、緩衝區溢位等等。|  
|`eUnloadAppDomain`|指定應該卸載 <xref:System.AppDomain>。 CLR 嘗試執行完成項。|  
  
## <a name="remarks"></a>備註  
 主機會藉由呼叫[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)介面的方法來設定原則動作。 如需有關強制性和正常中止的詳細資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列舉。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
