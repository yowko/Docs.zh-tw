---
title: COR_GC_STATS 結構
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1085bec812d797d3fbe4ea63ef447d4c466149f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965062"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS 結構
提供有關 common language runtime (CLR) 之垃圾收集機制的統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`Flags`|指出應該計算並傳回的域值。|  
|`ExplicitGCCount`|指出外部要求所強制執行的垃圾收集數目。|  
|`GenCollectionsTaken`|指出每個層代所執行的垃圾收集數目。|  
|`CommittedKBytes`|所有堆積中認可的總 kb 數。|  
|`ReservedKBytes`|所有堆積中保留的 kb 總數。|  
|`Gen0HeapSizeKBytes`|層代-零堆積的大小 (以 kb 為單位)。|  
|`Gen1HeapSizeKBytes`|層代-單一堆積的大小 (以 kb 為單位)。|  
|`Gen2HeapSizeKBytes`|層代-兩個堆積的大小 (以 kb 為單位)。|  
|`LargeObjectHeapSizeKBytes`|大型物件堆積的大小 (以 kb 為單位)。|  
|`KBytesPromotedFromGen0`|從層代零升級到第一代的物件大小 (以 kb 為單位)。|  
|`KBytesPromotedFromGen1`|從層代1升級至第二代的物件大小 (以 kb 為單位)。|  
  
## <a name="remarks"></a>備註  
 [ICLRGCManager:: GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法需要`Flags`將`COR_GC_STATS`結構的欄位設定為[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉的一個或多個值, 以指定要設定的統計資料。  
  
 下表將此結構提供的統計資料對應至兩個[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉值`COR_GC_COUNTS`和`COR_GC_MEMORYUSAGE`。  
  
|由 COR_GC_COUNTS 指定|由 COR_GC_MEMORYUSAGE 指定|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 使用方式的範例如下:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [自動管理記憶體](../../../standard/automatic-memory-management.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
