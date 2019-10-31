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
ms.openlocfilehash: b0fbc462283ef1577de8100e60fd09caa53db539
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131919"
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
 此列舉會指定要由[ICLRGCManager：： GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法設定的[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構中的統計資料。  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`COR_GC_COUNTS`|記錄每個層代所執行的垃圾收集數目。|  
|`COR_GC_MEMORYUSAGE`|記錄記憶體使用量和垃圾收集大小統計資料。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl，GCHost。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [COR_GC_STATS 結構](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
