---
title: "COR_GC_STATS 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STATS
helpviewer_keywords: COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02a775be4976760b354a492e7252a67ef04eace9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstats-structure"></a>COR_GC_STATS 結構
提供有關 common language runtime (CLR) 記憶體回收機制統計資料。  
  
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
|`Flags`|表示要計算及傳回的欄位值。|  
|`ExplicitGCCount`|指出所強制的外部要求的記憶體回收數目。|  
|`GenCollectionsTaken`|表示執行每個層代的回收次數。|  
|`CommittedKBytes`|認可所有堆積中的 kb 總數。|  
|`ReservedKBytes`|保留所有堆積中的 kb 總數。|  
|`Gen0HeapSizeKBytes`|以 kb 為單位，層代 0 堆積的大小。|  
|`Gen1HeapSizeKBytes`|以 kb 為單位，產生一個堆積的大小。|  
|`Gen2HeapSizeKBytes`|以 kb 為單位，產生兩個堆積的大小。|  
|`LargeObjectHeapSizeKBytes`|以 kb 為單位，在大型物件堆積的大小。|  
|`KBytesPromotedFromGen0`|大小，以 kb 為單位，從層代 0 提升至其中一個層代的物件。|  
|`KBytesPromotedFromGen1`|大小，以 kb 為單位，從一個層代升級至兩個層代的物件。|  
  
## <a name="remarks"></a>備註  
 [Iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法需要`Flags`欄位`COR_GC_STATS`結構來設定的一或多個值[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)以指定的列舉設定為統計資料。  
  
 下表將對應到兩個此結構所提供的統計資料[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉值`COR_GC_COUNTS`和`COR_GC_MEMORYUSAGE`。  
  
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
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [自動管理記憶體](../../../../docs/standard/automatic-memory-management.md)  
 [記憶體回收](../../../../docs/standard/garbage-collection/index.md)
