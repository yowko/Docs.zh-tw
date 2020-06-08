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
ms.openlocfilehash: b7a068efcf20b2028e9c193567d15b59e582febf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500919"
---
# <a name="cor_prf_gc_generation-enumeration"></a>COR_PRF_GC_GENERATION 列舉
識別垃圾收集的產生。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|物件會儲存為層代0。|  
|`COR_PRF_GC_GEN_1`|物件會儲存為第1代。|  
|`COR_PRF_GC_GEN_2`|物件會儲存為層代2。|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|物件會儲存在大型物件堆積中。|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|物件會儲存在釘選的物件堆積中。|  
  
## <a name="remarks"></a>備註  
 垃圾收集行程藉由將物件根據年齡分割成層代，來改善記憶體管理效能。 垃圾收集行程目前使用三個層代，編號為0、1和2，以及兩個特殊堆積區段，一個用於大型物件，一個用於釘選的物件。
  
 其大小大於臨界值的物件會儲存在大型物件堆積中。 釘選的物件可以配置到釘選的物件堆積，以避免在一般堆積上配置它們的效能成本。 其他已配置的物件會從屬於層代0開始。 在層代0中進行垃圾收集之後存在的所有物件都會升級至層代1。 在層代1中進行垃圾收集後存在的物件會移至層代2。  
  
 使用世代表示垃圾收集行程在任何時候都只能處理已設定物件的子集。  
  
 `COR_PRF_GC_GENERATION` [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)結構會使用列舉型別。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
