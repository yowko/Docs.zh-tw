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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4ce8fb8d9d941544982c8da852260b8018788a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680738"
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS 列舉
指出記憶體回收根目錄的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|根目錄會防止記憶體回收移動物件。|  
|`COR_PRF_GC_ROOT_WEAKREF`|根目錄不會防止記憶體回收。|  
|`COR_PRF_GC_ROOT_INTERIOR`|根參考的物件，而不是物件本身的欄位。|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|根物件的參考計數是否為某個值，可防止記憶體回收。|  
  
## <a name="remarks"></a>備註  
 `COR_PRF_GC_ROOT_FLAGS` 會提供特殊的根憑證的其他資訊的位元遮罩。 不過，並非所有的根是特殊的。 比方說，有些根不是弱式參考，釘選，或參考計數的內部指標。 這類的根目錄中，有要傳達的任何旗標。 因此，使用這個列舉型別，例如的方法[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)方法，傳送 0 為旗標位元遮罩，指出所有旗標為關閉狀態。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
