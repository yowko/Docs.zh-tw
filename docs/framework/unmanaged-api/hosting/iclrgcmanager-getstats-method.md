---
title: ICLRGCManager::GetStats 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9df9263a0356b0c3c1a6d1da950c670f5a020d1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966221"
---
# <a name="iclrgcmanagergetstats-method"></a>ICLRGCManager::GetStats 方法
取得有關 common language runtime 之垃圾收集系統的一組目前統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>參數  
 `pStats`  
 [in、out]包含所要求統計資料的[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)實例。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetStats`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 CLR 會計算並只傳回`Flags` `pStats`欄位所指定的統計資料。  
  
 將 `Flags` 欄位設定為[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉的一個或多個值，以指定要設定 [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) 結構中的哪些統計資料。  
  
 使用方式的範例如下：  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [自動管理記憶體](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS 結構](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [COR_GC_STAT_TYPES 列舉](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
