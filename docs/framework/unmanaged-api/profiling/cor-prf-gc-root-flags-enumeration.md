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
ms.openlocfilehash: 6b4c71a099e1ddb03b8a5287b56b750f7119e34e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682350"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS 列舉

指出垃圾收集根的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|根會防止垃圾收集移動物件。|  
|`COR_PRF_GC_ROOT_WEAKREF`|根目錄不會防止垃圾收集。|  
|`COR_PRF_GC_ROOT_INTERIOR`|根目錄指的是物件的欄位，而不是物件本身。|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|如果物件的參考計數是特定的值，則根會防止垃圾收集。|  
  
## <a name="remarks"></a>備註  

 `COR_PRF_GC_ROOT_FLAGS` 這是一個位元遮罩，提供特殊根目錄的其他相關資訊。 不過，並非所有的根目錄都是特殊的。 例如，某些根目錄並非弱式參考、內部指標、釘選或參考計數。 針對這類根目錄，沒有可傳達的旗標。 因此，使用此列舉的方法（例如 [ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md) 方法）會傳送0作為旗標位元遮罩，表示所有旗標都已關閉。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
