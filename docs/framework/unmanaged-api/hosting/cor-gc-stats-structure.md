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
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176522"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS 結構
提供有關通用語言運行時 （CLR） 的垃圾回收機制的統計資訊。  
  
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
|`Flags`|指示應計算和返回哪些欄位值。|  
|`ExplicitGCCount`|指示外部請求強制進行的垃圾回收數。|  
|`GenCollectionsTaken`|指示每代執行的垃圾回收數。|  
|`CommittedKBytes`|所有堆中提交的千位元組的總數。|  
|`ReservedKBytes`|所有堆中保留的千位元組的總數。|  
|`Gen0HeapSizeKBytes`|生成零堆的大小（以千位元組為單位）。|  
|`Gen1HeapSizeKBytes`|第一代堆的大小（以千位元組為單位）。|  
|`Gen2HeapSizeKBytes`|第二代堆的大小（以千位元組為單位）。|  
|`LargeObjectHeapSizeKBytes`|大型物件堆的大小（以千位元組為單位）。|  
|`KBytesPromotedFromGen0`|從第 0 代提升到第一代的物件的大小（以千位元組為單位）。|  
|`KBytesPromotedFromGen1`|從第一代提升到第二代的物件的大小（以千位元組為單位）。|  
  
## <a name="remarks"></a>備註  
 [ICLRGCManager：GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法要求將`Flags``COR_GC_STATS`結構欄位設置為[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)枚舉的一個或多個值，以指定要設置的統計資訊。  
  
 下表將此結構提供的統計資訊映射到兩[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)枚舉值`COR_GC_COUNTS`和`COR_GC_MEMORYUSAGE`。  
  
|由COR_GC_COUNTS指定|由COR_GC_MEMORYUSAGE指定|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 使用的示例如下：  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** GCHost.idl  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [自動記憶體管理](../../../standard/automatic-memory-management.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
