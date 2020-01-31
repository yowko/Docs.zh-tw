---
title: COR_PRF_GC_ROOT_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 0210aca5698cd9c86979c13afd1e622b50d194df
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867176"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS 列舉
表示垃圾收集根目錄的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|根會防止垃圾收集移動物件。|  
|`COR_PRF_GC_ROOT_WEAKREF`|根不會防止垃圾收集。|  
|`COR_PRF_GC_ROOT_INTERIOR`|根是指物件的欄位，而不是物件本身。|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|如果物件的參考計數是特定值，則根目錄會防止垃圾收集。|  
  
## <a name="remarks"></a>備註  
 `COR_PRF_GC_ROOT_FLAGS` 是一個位元遮罩，可提供特殊根的其他相關資訊。 不過，並非所有的根都是特殊的。 例如，某些根不是弱式參考、內部指標、固定或參考計數。 對於這類根，沒有可傳達的旗標。 因此，使用這個列舉的方法（例如[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)方法）會傳送0做為旗標位元遮罩，表示所有旗標都已關閉。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析列舉](profiling-enumerations.md)
