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
ms.openlocfilehash: d335a62545f06a66d4044b59aa9499d3f7ede515
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208471"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS 結構
提供 common language runtime (CLR) 記憶體回收機制的相關統計資料。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|描述|  
|------------|-----------------|  
|`Flags`|表示欄位值，應該會計算並傳回。|  
|`ExplicitGCCount`|指出所強制的外部要求記憶體回收數目。|  
|`GenCollectionsTaken`|表示執行每個層代的回收數目。|  
|`CommittedKBytes`|認可所有堆積中的 kb 總數。|  
|`ReservedKBytes`|保留所有堆積中的 kb 總數。|  
|`Gen0HeapSizeKBytes`|以 kb 為單位的層代 0 堆積大小。|  
|`Gen1HeapSizeKBytes`|以 kb 為單位，產生一個堆積的大小。|  
|`Gen2HeapSizeKBytes`|以 kb 為單位，產生兩個堆積的大小。|  
|`LargeObjectHeapSizeKBytes`|以 kb 為單位，大型物件堆積的大小。|  
|`KBytesPromotedFromGen0`|大小 （kb），從層代 0 提升至其中一個層代的物件。|  
|`KBytesPromotedFromGen1`|大小 （kb），從一個層代升級至兩個層代的物件。|  
  
## <a name="remarks"></a>備註  
 [Iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法需要`Flags`欄位`COR_GC_STATS`設為一或多個值的結構[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)来指定其列舉型別設定要統計資料。  
  
 下表對應至兩個這個結構所提供的統計資料[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉值`COR_GC_COUNTS`和`COR_GC_MEMORYUSAGE`。  
  
|指定 COR_GC_COUNTS|指定 COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 使用方式的範例如下所示：  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [自動管理記憶體](../../../../docs/standard/automatic-memory-management.md)
- [記憶體回收](../../../../docs/standard/garbage-collection/index.md)
