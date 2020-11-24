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
ms.openlocfilehash: 72b371d72b2f055f2840da5595d9022ffd7e2507
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674726"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction 列舉

描述主機可針對 [EClrOperation](eclroperation-enumeration.md) 所描述的作業所設定的原則動作，以及 [EClrFailure](eclrfailure-enumeration.md)所描述的失敗。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`eAbortThread`|指定 common language runtime (CLR) 應正常中止執行緒。 正常中止包括嘗試執行所有 `finally` 區塊、與 `catch` 執行緒中止相關的任何區塊，以及完成項。|  
|`eDisableRuntime`|指定 CLR 應進入停用狀態。 無法在受影響的進程中執行任何進一步的 managed 程式碼，且會封鎖執行緒進入 CLR。|  
|`eExitProcess`|指定 CLR 應嘗試正常結束進程，包括執行完成項和執行清除和記錄作業。|  
|`eFastExitProcess`|指定 CLR 應該立即結束進程，而不執行完成項或執行清除和記錄作業。 不過，通知會傳送至偵錯工具。|  
|`eNoAction`|指定不採取任何動作。|  
|`eRudeAbortThread`|指定 CLR 應該執行強制執行緒中止。 只 `catch` `finally` 會執行標示為的和區塊 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。|  
|`eRudeExitProcess`|指定 CLR 應結束進程，而不執行完成項或記錄作業。|  
|`eRudeUnloadAppDomain`|指定 CLR 應該執行的強制卸載 <xref:System.AppDomain> 。 只會執行標示為的完成項 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。 同樣地， <xref:System.AppDomain> 在其堆疊中的所有線程都會接收 a `ThreadAbortException` ，但 `catch` 只 `finally` 會執行標示為的和區塊 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。|  
|`eThrowException`|指定應擲回適用于條件的例外狀況，例如記憶體不足、緩衝區溢位等。|  
|`eUnloadAppDomain`|指定應該卸載 <xref:System.AppDomain> 。 CLR 會嘗試執行完成項。|  
  
## <a name="remarks"></a>備註  

 主機會藉由呼叫 [ICLRPolicyManager](iclrpolicymanager-interface.md) 介面的方法來設定原則動作。 如需有關強制性和正常中止的詳細資訊，請參閱 [EClrOperation](eclroperation-enumeration.md) 列舉。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](eclrfailure-enumeration.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](ihostpolicymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
