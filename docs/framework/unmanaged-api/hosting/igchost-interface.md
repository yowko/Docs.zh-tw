---
title: "IGCHost 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost
helpviewer_keywords: IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0f398c09569a855291a1565ce63b513161a803
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="igchost-interface"></a>IGCHost 介面
提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。  
  
> [!NOTE]
>  從開始[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以使用[igchost2:: Setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於`DWORD`所加諸的限制[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)方法。  
  
> [!NOTE]
>  這個介面是僅供專家使用。 如果使用不當，它會影響應用程式的效能。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[Collect 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|強制發生在指定的層代，不論目前的記憶體回收集合的狀態。|  
|[GetStats 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|取得目前的記憶體回收系統狀態的統計資料。|  
|[GetThreadStats 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|取得每個執行緒統計資料記憶體回收。|  
|[SetGCStartupLimits 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|層代 0 設定區段的大小和大小上限。|  
|[SetVirtualMemLimit 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|設定執行階段的虛擬記憶體的大小上限。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl、 GCHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
