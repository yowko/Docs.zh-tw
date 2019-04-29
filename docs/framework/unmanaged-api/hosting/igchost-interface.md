---
title: IGCHost 介面
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3202aa25261863dae953e3edac36f3406fa001d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699707"
---
# <a name="igchost-interface"></a>IGCHost 介面
提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。  
  
> [!NOTE]
>  開頭[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以使用[IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於`DWORD`所加諸的限制[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)方法。  
  
> [!NOTE]
>  這個介面是僅供專家使用。 如果不當使用，它可能會影響應用程式的效能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Collect 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|強制發生指定的層代，不論目前的記憶體回收集合的狀態。|  
|[GetStats 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|取得記憶體回收系統的目前狀態的統計資料。|  
|[GetThreadStats 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|取得每個執行緒統計資料進行記憶體回收。|  
|[SetGCStartupLimits 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|層代 0 設定區段的大小和大小上限。|  
|[SetVirtualMemLimit 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|設定執行階段的虛擬記憶體的大小上限。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl GCHost.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
