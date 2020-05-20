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
ms.openlocfilehash: 8788d6e2220778a3f0926d5ed3dd59142487bcca
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616186"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction 列舉
描述主機可以針對[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)所描述的作業設定的原則動作，以及[EClrFailure](eclrfailure-enumeration.md)所描述的失敗。  
  
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
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`eAbortThread`|指定 common language runtime （CLR）應正常中止執行緒。 「正常中止」包括嘗試執行所有 `finally` 區塊、與 `catch` 執行緒中止相關的任何區塊，以及完成項。|  
|`eDisableRuntime`|指定 CLR 應進入停用狀態。 在受影響的進程中無法執行進一步的 managed 程式碼，而且執行緒會遭到封鎖而無法進入 CLR。|  
|`eExitProcess`|指定 CLR 應該嘗試順利結束進程，包括執行完成項和執行清除和記錄作業。|  
|`eFastExitProcess`|指定 CLR 應該立即結束進程，而不執行完成項或清除和記錄作業。 不過，通知會傳送至偵錯工具。|  
|`eNoAction`|指定不採取任何動作。|  
|`eRudeAbortThread`|指定 CLR 應該執行強制執行緒中止。 只有 `catch` 標示為 `finally` 的和區塊才 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 會執行。|  
|`eRudeExitProcess`|指定 CLR 應該結束進程，而不執行完成項或記錄作業。|  
|`eRudeUnloadAppDomain`|指定 CLR 應該執行的強制卸載 <xref:System.AppDomain> 。 只會執行標記為的完成項 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。 同樣地， <xref:System.AppDomain> 在其堆疊中的所有線程都會接收到 `ThreadAbortException` ，但 `catch` 只 `finally` 會執行標示為的那些和區塊 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。|  
|`eThrowException`|指定應該擲回條件適用的例外狀況，例如記憶體不足、緩衝區溢位等等。|  
|`eUnloadAppDomain`|指定應該卸載 <xref:System.AppDomain> 。 CLR 嘗試執行完成項。|  
  
## <a name="remarks"></a>備註  
 主機會藉由呼叫[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)介面的方法來設定原則動作。 如需有關強制性和正常中止的詳細資訊，請參閱[EClrOperation](eclroperation-enumeration.md)列舉。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](eclrfailure-enumeration.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](ihostpolicymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
