---
title: COR_GC_THREAD_STATS 結構
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 25a90965dc5466b7cf1a07140705424cf2ba4cd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699231"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS 結構

包含與垃圾收集相關的每個執行緒統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`PerThreadAllocation`|在與目前實例相關聯的執行緒上配置的記憶體位元組數目 `COR_GC_THREAD_STATS` 。 每次發生層代零垃圾收集時，這個數位就會清除為零。|  
|`Flags`|在最近的垃圾收集上提升為較高世代的位元組數目。|  
  
## <a name="remarks"></a>備註  

 [ICLRTask：： GetMemStats](iclrtask-getmemstats-method.md) 接受型別為的 output 參數 `COR_GC_THREAD_STATS` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](hosting-structures.md)
- [IHostTask 介面](ihosttask-interface.md)
