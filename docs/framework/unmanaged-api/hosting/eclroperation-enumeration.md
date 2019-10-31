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
ms.openlocfilehash: 6becc44b061ff2baac63437b6a72375d1c3735b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131154"
---
# <a name="eclroperation-enumeration"></a>EClrOperation 列舉
描述主機可以套用原則動作的一組作業。  
  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|當以非正常（強制）方式卸載 <xref:System.AppDomain> 時，主機可以指定要採取的原則動作。|  
|`OPR_AppDomainUnload`|主機可以指定卸載 <xref:System.AppDomain> 時要採取的原則動作。|  
|`OPR_FinalizerRun`|主機可以指定在完成項執行時要採取的原則動作。|  
|`OPR_ProcessExit`|主機可以指定在進程結束時要採取的原則動作。|  
|`OPR_ThreadAbort`|主機可以指定要線上程中止時採取的原則動作。|  
|`OPR_ThreadRudeAbortInCriticalRegion`|主機可以指定在程式碼的重要區域中發生強制執行緒中止時，所要採取的原則動作。|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|主機可以指定在非關鍵的程式碼區域中發生強制執行緒中止時，所要採取的原則動作。|  
  
## <a name="remarks"></a>備註  
 通用語言執行平臺（CLR）可靠性基礎結構可區分在關鍵程式碼區域中發生的中止和資源配置失敗，以及在非關鍵的程式碼區域中發生的錯誤。 這項區別的設計，是為了讓主機根據程式碼中發生失敗的位置來設定不同的原則。  
  
 程式*代碼的關鍵區域*是 CLR 無法保證中止工作或無法完成資源要求的任何空間，將只會影響目前的工作。 例如，如果工作持有鎖定，並收到表示在建立記憶體配置要求時失敗的 HRESULT，則只是要中止該工作以確保 <xref:System.AppDomain>的穩定性，因為 <xref:System.AppDomain> 可能包含其他工作正在等候相同的鎖定。 若要放棄目前的工作，可能會導致這些其他工作停止回應。 在這種情況下，主機必須能夠卸載整個 <xref:System.AppDomain>，而不是風險潛在的不穩定。  
  
 另一方面，程式*代碼的非關鍵區域*是一個區域，其中 CLR 可以保證中止或失敗只會影響發生錯誤的工作。  
  
 CLR 也可以區別正常和非正常（強制性）中止。 一般來說，正常或正常的中止會在中止工作之前，讓每個工作執行例外狀況處理常式和完成項，而強制中止則不會進行這類保證。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
