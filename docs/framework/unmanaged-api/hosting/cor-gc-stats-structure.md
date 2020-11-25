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
ms.openlocfilehash: 53a70c53a06ac55a2dab7c646018d63189ee0b36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726219"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS 結構

提供 common language runtime (CLR) 之垃圾收集機制的相關統計資料。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`Flags`|指出應該計算和傳回的域值。|  
|`ExplicitGCCount`|指出外部要求強制執行的垃圾收集數目。|  
|`GenCollectionsTaken`|指出針對每個層代執行的垃圾收集數目。|  
|`CommittedKBytes`|所有堆積中認可的 kb 總數。|  
|`ReservedKBytes`|所有堆積中保留的 kb 總數。|  
|`Gen0HeapSizeKBytes`|層代零堆積的大小（以 kb 為單位）。|  
|`Gen1HeapSizeKBytes`|第一個堆積的大小（以 kb 為單位）。|  
|`Gen2HeapSizeKBytes`|第2代堆積的大小（以 kb 為單位）。|  
|`LargeObjectHeapSizeKBytes`|大型物件堆積的大小（以 kb 為單位）。|  
|`KBytesPromotedFromGen0`|從層代零升級到層代1的物件大小（以 kb 為單位）。|  
|`KBytesPromotedFromGen1`|從層代1提升至層代二的物件大小（以 kb 為單位）。|  
  
## <a name="remarks"></a>備註  

 [ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法需要將 `Flags` 結構的欄位 `COR_GC_STATS` 設定為[COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md)列舉的一或多個值，以指定要設定的統計資料。  
  
 下表將此結構提供的統計資料對應至兩個 [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 列舉值 `COR_GC_COUNTS` 和 `COR_GC_MEMORYUSAGE` 。  
  
|由 COR_GC_COUNTS 指定|由 COR_GC_MEMORYUSAGE 指定|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 使用方式的範例如下：  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](hosting-structures.md)
- [自動記憶體管理](../../../standard/automatic-memory-management.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
