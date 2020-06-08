---
title: ICorProfilerCallback2::GarbageCollectionStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
ms.openlocfilehash: f025f4c0bc0ec8e11decddcdf64be50f68955266
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499801"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted 方法
通知程式碼分析工具已開始垃圾收集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>參數  
 `cGenerations`  
 在陣列中的專案總數 `generationCollected` 。  
  
 `generationCollected`  
 在布林值的陣列， `true` 如果此垃圾收集正在收集對應至陣列索引的層代，則為，否則為 `false` 。  
  
 陣列是以[COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md)列舉的值來編制索引，這表示產生。  
  
 `reason`  
 在[COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md)列舉的值，表示垃圾收集引發的原因。  
  
## <a name="remarks"></a>備註  
 在 `GarbageCollectionStarted` 回呼與對應的[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)回呼之間，將會發生與此垃圾收集相關的所有回呼。 這些回呼不需要在相同的執行緒上發生。  
  
 在回呼期間，分析工具可以安全地檢查其原始位置中的物件 `GarbageCollectionStarted` 。 在從傳回之後，垃圾收集行程會開始移動物件 `GarbageCollectionStarted` 。 在分析工具從此回呼傳回之後，分析工具應該將所有的物件識別碼視為無效，直到它收到 `ICorProfilerCallback2::GarbageCollectionFinished` 回呼為止。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
