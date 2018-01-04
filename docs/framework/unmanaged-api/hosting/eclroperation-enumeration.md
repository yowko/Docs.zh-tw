---
title: "EClrOperation 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrOperation
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrOperation
helpviewer_keywords: EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a>EClrOperation 列舉
描述一組作業，主機可以套用原則的動作。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|描述|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|主機可以指定時採取的動作原則<xref:System.AppDomain>卸載非正常程序 （粗略） 的方式。|  
|`OPR_AppDomainUnload`|主機可以指定時採取的動作原則<xref:System.AppDomain>卸載。|  
|`OPR_FinalizerRun`|主機可以指定原則完成執行時要採取的動作。|  
|`OPR_ProcessExit`|主機可以指定原則的處理序結束時要採取的動作。|  
|`OPR_ThreadAbort`|主機可以指定原則會在中止執行緒時要採取的動作。|  
|`OPR_ThreadRudeAbortInCriticalRegion`|主機可以指定原則的程式碼的重要區域中的粗略的執行緒中止發生時要採取的動作。|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|主機可以指定原則粗略的執行緒中止發生非關鍵的程式碼區域中時可採取的動作。|  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 可靠性基礎結構以區別中止而資源會發生在程式碼和發生非關鍵的程式碼區域中的關鍵區域的配置失敗。 這個差別被為了讓主應用程式設定不同的原則，根據程式碼中發生失敗。  
  
 A*的程式碼的重要區域*當該中止工作或無法完成要求的資源將會影響目前的工作不能保證 CLR 任何空間。 比方說，如果工作會保留鎖定，並收到指出時進行記憶體配置要求失敗的 HRESULT，是不足，無法只是終止該工作，以確保穩定性<xref:System.AppDomain>，因為<xref:System.AppDomain>可能包含其他針對相同鎖定等候的工作。 要放棄目前的工作可能會使這些其他工作，來停止回應 （或擱置） 無限期。 在這種情況下，主機必須能卸載整個<xref:System.AppDomain>而不是風險潛在的不穩定。  
  
 A*非關鍵的程式碼區域*，相反地，是 CLR 可保證 「 中止 」 或 「 失敗將會影響只有工作錯誤發生所在的區域。  
  
 CLR 也區分非失誤性和非正常程序 （粗略） 中止。 一般情況下，正常的中止會盡全力之前中止工作，而粗略中止可不讓任何這類保證執行例外狀況處理常式和完成項。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
