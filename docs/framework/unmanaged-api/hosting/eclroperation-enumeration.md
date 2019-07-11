---
title: EClrOperation 列舉
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b000ed3d75ddb6a7882cb8f03ff2cec64fb9fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767872"
---
# <a name="eclroperation-enumeration"></a>EClrOperation 列舉
描述的作業主機可以套用原則的動作集合。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|主機可以指定應執行時的原則動作<xref:System.AppDomain>卸載非依正常程序 （粗略） 的方式。|  
|`OPR_AppDomainUnload`|主機可以指定應執行時的原則動作<xref:System.AppDomain>卸載。|  
|`OPR_FinalizerRun`|主機可以指定原則完成項執行時所要採取的動作。|  
|`OPR_ProcessExit`|主機可以指定原則的處理序結束時要採取的動作。|  
|`OPR_ThreadAbort`|主機可以指定原則會在中止執行緒時所要採取的動作。|  
|`OPR_ThreadRudeAbortInCriticalRegion`|主機可以指定原則在關鍵區域的程式碼中執行緒粗暴中止時要採取的動作。|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|主機可以指定原則才會發生非關鍵的程式碼區域中的執行緒粗暴中止時的動作。|  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 可靠性 infrastructure 區分中止和資源配置失敗的程式碼和發生非關鍵區域中的程式碼的關鍵區域中發生。 這項區別被設計來讓主機以設定不同的原則，根據程式碼中發生失敗。  
  
 A*的程式碼的重要區域*該中止工作或無法完成要求的資源將會影響目前的工作，CLR 中不能保證任何空間。 例如，如果工作會保留鎖定，並收到指出時進行記憶體配置要求失敗的 HRESULT，它不足，只是中止該工作，以確保穩定性<xref:System.AppDomain>，因為<xref:System.AppDomain>可能包含其他相同的鎖定所等候的工作。 若要放棄目前的工作可能會導致這些其他工作以停止回應。 在此情況下，主機必須能夠卸載整個<xref:System.AppDomain>而不是風險潛在的不穩定。  
  
 A*非關鍵的程式碼區域*，相反地，是 CLR 可以保證 「 中止 」 或 「 失敗會影響只有工作時就會發生錯誤的區域。  
  
 CLR 也會區分非失誤性和非依正常程序 （粗略） 中止。 一般情況下，正常的中止會盡全力之前中止工作，而粗暴中止不提供任何這類保證執行例外狀況處理常式和完成項。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
