---
title: COR_GC_THREAD_STATS_TYPES 列舉
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a984e8645bec0f58d8a31965b762e0a3a190ba59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768026"
---
# <a name="corgcthreadstatstypes-enumeration"></a>COR_GC_THREAD_STATS_TYPES 列舉
表示執行緒的記憶體回收集合統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|執行緒已升級最新的記憶體回收集合中的位元組。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl GCHost.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
