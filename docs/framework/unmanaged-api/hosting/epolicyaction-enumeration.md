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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa8589b3f27ba97d32e77dbfecb190edc69dbc18
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677327"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction 列舉
描述所描述的作業可以設定主應用程式的原則動作[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)和所描述的失敗[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|描述|  
|------------|-----------------|  
|`eAbortThread`|指定 common language runtime (CLR) 應該依正常程序中止執行緒。 依正常程序中止包含嘗試對執行所有`finally`封鎖任何`catch`區塊與執行緒中止和完成項。|  
|`eDisableRuntime`|指定 CLR 應該輸入停用的狀態。 沒有進一步執行 managed 程式碼，在受影響的程序，並進入 CLR 會封鎖執行緒。|  
|`eExitProcess`|指定 CLR 應該嘗試處理序，包括執行完成項，以及執行清理和記錄作業的非失誤性結束。|  
|`eFastExitProcess`|指定的 CLR 應該處理程序立即結束，而不需要執行完成項，或執行清理和記錄作業。 不過，通知會傳送至偵錯工具。|  
|`eNoAction`|指定應該採取任何動作。|  
|`eRudeAbortThread`|指定 CLR 應該執行執行緒粗暴中止。 只有`catch`並`finally`區塊標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。|  
|`eRudeExitProcess`|指定 CLR 應該結束處理程序，而不執行完成項，或記錄作業。|  
|`eRudeUnloadAppDomain`|指定 CLR 應該執行粗暴卸載<xref:System.AppDomain>。 唯一的完成項標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。 同樣地，所有執行緒與這個<xref:System.AppDomain>其堆疊中接收`ThreadAbortException`，而是只`catch`並`finally`區塊標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。|  
|`eThrowException`|指定應該擲回例外狀況，例如記憶體不足、 緩衝區溢位，等等，適當。|  
|`eUnloadAppDomain`|指定<xref:System.AppDomain>應該將它卸載。 CLR 會嘗試執行完成項。|  
  
## <a name="remarks"></a>備註  
 主應用程式設定原則的動作是呼叫的方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)介面。 粗暴和正常中止的相關資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列舉型別。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
