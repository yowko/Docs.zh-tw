---
title: COR_PRF_GC_GENERATION 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15bd3ed8f1642e44ecf9c4df49feebd72eeac8c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590129"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION 列舉
識別記憶體回收層代。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|此物件會儲存成層代 0。|  
|`COR_PRF_GC_GEN_1`|物件會儲存為第 1 代。|  
|`COR_PRF_GC_GEN_2`|此物件會儲存為第 2 代。|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|此物件會儲存大型物件堆積中。|  
  
## <a name="remarks"></a>備註  
 記憶體回收行程會提高成根據年齡層代將物件的記憶體管理效能。 記憶體回收行程目前使用三個層代，編號 0、 1 和 2，以及用於大型物件堆積的特殊區段。 其大小大於特定值的物件會儲存在大型物件堆積。 其他已配置的物件屬於層代 0 開始。 發生在層代 0 記憶體回收後存在的所有物件會都提升至層代 1。 存在之後發生在第 1 代記憶體回收的物件將移至第 2 代。  
  
 層代的使用，表示記憶體回收行程必須一次使用的配置的物件子集。  
  
 `COR_PRF_GC_GENERATION`列舉由[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
