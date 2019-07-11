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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fdfe33c5b488d8f464001a86233124d4e7df0ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779076"
---
# <a name="corgcstattypes-enumeration"></a>COR_GC_STAT_TYPES 列舉
指定要記錄的記憶體回收的統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>備註  
 此列舉會指定在哪些統計資料[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構是由設定[iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法。  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COR_GC_COUNTS`|記錄執行每個層代記憶體回收的數目。|  
|`COR_GC_MEMORYUSAGE`|記錄的記憶體使用量和記憶體回收集合大小統計資料。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl GCHost.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [COR_GC_STATS 結構](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
