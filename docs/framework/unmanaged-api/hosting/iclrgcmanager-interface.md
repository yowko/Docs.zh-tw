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
ms.openlocfilehash: 76d1071ddde1509f16fd786afa4c05c05224d051
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966215"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager 介面
提供可讓主機與 common language runtime 的垃圾收集系統互動的方法。  
  
> [!NOTE]
> 從 .NET Framework 4.5 開始, 您可以使用[ICLRGCManager2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法, 將垃圾收集區段的大小, 以及垃圾收集系統層代0的大小上限設定為大於的`DWORD`值。 [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)方法所加諸的限制。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Collect 方法](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|強制執行指定之層代的垃圾收集。|  
|[GetStats 方法](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|取得有關垃圾收集系統的一組目前統計資料。|  
|[SetGCStartupLimits 方法](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|設定垃圾收集區段的大小, 以及垃圾收集系統層代0的大小上限。|  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 會使用 managed <xref:System.GC>類型來執行其垃圾收集機制。 如需垃圾收集系統的詳細資訊, 請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [自動管理記憶體](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS 結構](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
