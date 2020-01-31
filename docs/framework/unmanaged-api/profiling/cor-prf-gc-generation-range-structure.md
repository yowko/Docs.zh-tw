---
title: COR_PRF_GC_GENERATION_RANGE 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: 682aac9729519e0861ae6e6f60df78a30063c278
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867201"
---
# <a name="cor_prf_gc_generation_range-structure"></a>COR_PRF_GC_GENERATION_RANGE 結構
說明正在進行記憶體回收的記憶體範圍 (亦即區塊)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`generation`|[COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md)列舉的值，指定記憶體區塊所屬的世代。|  
|`rangeStart`|物件的識別碼，指定記憶體區塊的開始位置。|  
|`rangeLength`|整數的指標，指定記憶體區塊所使用部分的大小（也就是區塊中使用的記憶體數量）。|  
|`rangeLengthReserved`|整數的指標，指定記憶體區塊的大小（也就是為區塊保留的記憶體數量）。|  
  
## <a name="remarks"></a>備註  
 只有在從[ICorProfilerCallback2：： GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)或[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)方法呼叫[ICorProfilerInfo2：： GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md)或[ICorProfilerInfo2：： GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md)（兩者都使用 `COR_PRF_GC_GENERATION_RANGE` 結構）時，`rangeLength` 值才保證是正確的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析結構](profiling-structures.md)
