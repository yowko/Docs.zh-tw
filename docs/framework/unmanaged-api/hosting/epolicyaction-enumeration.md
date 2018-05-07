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
ms.openlocfilehash: 14908ae641c8539659e6014deb2c5f35a6d1cfbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction 列舉
描述所描述的作業可以設定主機的原則動作[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)和所描述的失敗[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)。  
  
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
|`eAbortThread`|指定 common language runtime (CLR) 依正常程序應該中止的執行緒。 依正常程序中止包括嘗試執行所有`finally`封鎖任何`catch`區塊與執行緒中止與完成項。|  
|`eDisableRuntime`|指定 CLR 應該進入停用的狀態。 沒有進一步執行 managed 程式碼，在受影響的過程中，並進入 CLR 的執行緒會被封鎖。|  
|`eExitProcess`|指定 CLR 應該嘗試處理程序，包括執行完成項，以及執行清理和記錄作業的非失誤性結束。|  
|`eFastExitProcess`|指定的 CLR 程序會立即結束，而不需要執行完成項，或執行清除，以及記錄作業。 但是，傳送通知給偵錯工具。|  
|`eNoAction`|指定應該採取任何動作。|  
|`eRudeAbortThread`|指定 CLR 應該執行粗略的執行緒中止。 只有`catch`和`finally`區塊標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。|  
|`eRudeExitProcess`|指定 CLR 應該結束處理程序，而不執行完成項，或作業記錄。|  
|`eRudeUnloadAppDomain`|指定 CLR 應該執行的粗略卸載<xref:System.AppDomain>。 只有完成項標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。 同樣地，所有執行緒與這個<xref:System.AppDomain>其堆疊中接收`ThreadAbortException`，而是只有`catch`和`finally`區塊標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。|  
|`eThrowException`|指定應該擲回例外狀況，例如記憶體不足、 緩衝區溢位，以及其他等等。|  
|`eUnloadAppDomain`|指定<xref:System.AppDomain>應該卸載。 CLR 會嘗試執行完成項。|  
  
## <a name="remarks"></a>備註  
 主應用程式設定原則動作是呼叫的方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)介面。 中止粗略和依正常程序的相關資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列舉型別。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
