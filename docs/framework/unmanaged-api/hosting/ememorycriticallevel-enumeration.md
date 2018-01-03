---
title: "EMemoryCriticalLevel 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fb279402b2b677546f775b9a8badfbe2095fe4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 列舉
包含值，表示故障的影響，當有特定記憶體配置要求卻無法滿足。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`eAppDomainCritical`|表示配置要求此配置的網域中執行 managed 程式碼的重要。 如果無法配置記憶體，無法保證 CLR，網域是仍可使用。 主機會決定當無法滿足配置時要採取什麼動作。 它可以指示中止 CLR`AppDomain`自動執行，或允許繼續執行上呼叫方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。|  
|`eProcessCritical`|表示配置是重要的程序中的 managed 程式碼執行。 執行完成項時，在啟動期間，而且會使用此值。 如果無法配置記憶體，CLR 就無法執行操作中處理程序。 如果配置失敗，CLR 會有效停用。 Clr 的所有後續呼叫會失敗並 HOST_E_CLRNOTAVAILABLE。|  
|`eTaskCritical`|表示配置是重大執行所要求的配置工作。 如果無法配置記憶體，則 CLR 便無法保證可以執行此工作。 如果發生故障，CLR 會引發<xref:System.Threading.ThreadAbortException>實體作業系統執行緒上。|  
  
## <a name="remarks"></a>備註  
 中定義的記憶體配置方法[IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)和[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)介面採用這種類型的參數。 失敗的嚴重性而定，主機可以決定是否會立即配置要求失敗，或等候，直到可以滿足。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICLRMemoryNotificationCallback 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
