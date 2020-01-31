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
ms.openlocfilehash: c90c790c519cc0c422657e6e2d8040a365fbf48c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865775"
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
 在`generationCollected` 陣列中的專案總數。  
  
 `generationCollected`  
 在布林值的陣列，如果對應至陣列索引的產生是由此垃圾收集所收集，則為 `true`。否則，`false`。  
  
 陣列是以[COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md)列舉的值來編制索引，這表示產生。  
  
 `reason`  
 在[COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md)列舉的值，表示垃圾收集引發的原因。  
  
## <a name="remarks"></a>備註  
 與此垃圾收集相關的所有回呼都會在 `GarbageCollectionStarted` 回呼與對應的[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)回呼之間發生。 這些回呼不需要在相同的執行緒上發生。  
  
 在 `GarbageCollectionStarted` 回呼期間，分析工具可以安全地檢查其原始位置中的物件。 垃圾收集行程會在從 `GarbageCollectionStarted`返回後開始移動物件。 在分析工具從此回呼傳回之後，分析工具應該將所有的物件識別碼視為無效，直到收到 `ICorProfilerCallback2::GarbageCollectionFinished` 回呼為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
