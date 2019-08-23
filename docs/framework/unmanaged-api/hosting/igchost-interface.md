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
ms.openlocfilehash: 1d3f588bfc9799ed4591114b28d081ab417678b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914801"
---
# <a name="igchost-interface"></a>IGCHost 介面
提供方法來取得垃圾收集系統的相關資訊, 以及控制垃圾收集的某些層面。  
  
> [!NOTE]
> 從 .NET Framework 4.5 開始, 您可以使用[IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法, 將垃圾收集區段的大小, 以及垃圾收集系統層代0的大小上限設定為大於的`DWORD`值。[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)方法所加諸的限制。  
  
> [!NOTE]
> 此介面僅供專家使用。 如果未正確使用, 它可能會影響應用程式的效能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Collect 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|無論目前垃圾收集的狀態為何, 都會強制針對給定的層代進行集合。|  
|[GetStats 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|取得垃圾收集系統目前狀態的統計資料。|  
|[GetThreadStats 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|取得垃圾收集的每個執行緒統計資料。|  
|[SetGCStartupLimits 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|設定層代0的區段大小和大小上限。|  
|[SetVirtualMemLimit 方法](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|設定執行時間虛擬記憶體的大小上限。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl, GCHost。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
