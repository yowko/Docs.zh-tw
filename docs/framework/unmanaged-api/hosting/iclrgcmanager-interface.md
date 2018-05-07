---
title: ICLRGCManager 介面
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045b924033630ea98d5a532a62f1037a5972df90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager 介面
提供方法，讓主應用程式與 common language runtime 的記憶體回收系統互動。  
  
> [!NOTE]
>  從開始[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以使用[iclrgcmanager2:: Setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小為的值大於比`DWORD`所加諸的限制[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Collect 方法](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|強制執行指定的層代的回收。|  
|[GetStats 方法](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|取得一組有關記憶體回收系統目前的統計資料。|  
|[SetGCStartupLimits 方法](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小。|  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 會實作與受管理的記憶體回收機制<xref:System.GC>型別。 如需記憶體回收系統的詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [自動管理記憶體](../../../../docs/standard/automatic-memory-management.md)  
 [COR_GC_STATS 結構](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
