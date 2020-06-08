---
title: COR_GC_STAT_TYPES 列舉
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: d7e78dfc4beba67cc376b221d0cd49f7200f5d23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501699"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES 列舉
指定要記錄以進行垃圾收集的統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>備註  
 此列舉會指定要由[ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法來設定[COR_GC_STATS](cor-gc-stats-structure.md)結構中的哪些統計資料。  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COR_GC_COUNTS`|記錄每個層代所執行的垃圾收集數目。|  
|`COR_GC_MEMORYUSAGE`|記錄記憶體使用量和垃圾收集大小統計資料。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl，GCHost。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [COR_GC_STATS 結構](cor-gc-stats-structure.md)
- [裝載列舉](hosting-enumerations.md)
