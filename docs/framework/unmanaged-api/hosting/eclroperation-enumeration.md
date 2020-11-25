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
ms.openlocfilehash: c24e4557695d26666682ee385131abaab707a24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720707"
---
# <a name="eclroperation-enumeration"></a>EClrOperation 列舉

描述主機可以套用原則動作的作業集合。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|當 <xref:System.AppDomain> 以非正常的 (的) 方式卸載時，主機可以指定要採取的原則動作。|  
|`OPR_AppDomainUnload`|主機可以指定卸載時要採取的原則動作 <xref:System.AppDomain> 。|  
|`OPR_FinalizerRun`|主機可以指定完成項執行時要採取的原則動作。|  
|`OPR_ProcessExit`|主機可以指定進程結束時要採取的原則動作。|  
|`OPR_ThreadAbort`|主機可以指定當執行緒中止時要採取的原則動作。|  
|`OPR_ThreadRudeAbortInCriticalRegion`|主機可以指定在程式碼的關鍵區域中發生強制執行緒中止時，所要採取的原則動作。|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|當在非關鍵性的程式碼區域中發生強制執行緒中止時，主機可以指定要採取的原則動作。|  
  
## <a name="remarks"></a>備註  

 Common language runtime (CLR) 可靠性基礎結構可區分在程式碼的重要區域中發生的中止和資源配置失敗，以及在非關鍵性的程式碼區域中發生的錯誤。 這項區別的設計目的是要讓主機根據程式碼中發生失敗的位置來設定不同的原則。  
  
 程式 *代碼的關鍵區域* 是 CLR 無法保證中止工作或無法完成資源要求的任何空間，只會影響目前的工作。 例如，如果工作正在持有鎖定，並收到表示在進行記憶體配置要求時失敗的 HRESULT，則只是要中止該工作以確保的穩定性， <xref:System.AppDomain> 因為 <xref:System.AppDomain> 可能包含其他等候相同鎖定的工作。 若要放棄目前的工作，可能會導致這些其他工作停止回應。 在這種情況下，主機必須能夠卸載整個， <xref:System.AppDomain> 而不是風險潛在的不穩定。  
  
 另一方面， *非關鍵性的程式碼區域* 是一個區域，CLR 可以保證中止或失敗只會影響發生錯誤的工作。  
  
 CLR 也會區分正常和非正常的 () 中止。 一般來說，正常或無錯誤的中止會讓每個工作在中止工作之前執行例外狀況處理常式和完成項，而強制性中止則不會造成這類保證。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](eclrfailure-enumeration.md)
- [EPolicyAction 列舉](epolicyaction-enumeration.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](ihostpolicymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
