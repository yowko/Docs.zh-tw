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
ms.openlocfilehash: c14e27b67fc600e2684f8c967af30bb9a5cee126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716734"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES 列舉

指定要記錄的垃圾收集統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>備註  

 此列舉會指定[ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法要設定[COR_GC_STATS](cor-gc-stats-structure.md)結構中的統計資料。  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`COR_GC_COUNTS`|記錄針對每個層代執行的垃圾收集數目。|  
|`COR_GC_MEMORYUSAGE`|記錄記憶體使用量和垃圾收集大小統計資料。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl、GCHost。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [COR_GC_STATS 結構](cor-gc-stats-structure.md)
- [裝載列舉](hosting-enumerations.md)
