---
title: ICorProfilerCallback4::MovedReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 79e54cde8757bbe690f9b7c4344a2a3cb19cf627
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499378"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 方法
呼叫以報告壓縮記憶體回收造成的堆積中物件的新配置。 如果分析工具已實[ICorProfilerCallback4](icorprofilercallback4-interface.md)介面，則會呼叫這個方法。 此回呼會取代[ICorProfilerCallback：： MovedReferences](icorprofilercallback-movedreferences-method.md)方法，因為它可以報告較大範圍的物件，其長度超過可在 ULONG 中表示的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>參數  
 `cMovedObjectIDRanges`  
 [in] 壓縮記憶體回收造成移動的連續物件區塊數目。 也就是 `cMovedObjectIDRanges` 的值是 `oldObjectIDRangeStart`、`newObjectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的總大小。  
  
 下面 `MovedReferences2` 的三個引數是平行陣列。 換句話說，`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]` 和 `cObjectIDRangeLength[i]` 全都會考量連續物件的單一區塊。  
  
 `oldObjectIDRangeStart`  
 [in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊舊的 (記憶體回收前) 開始位址。  
  
 `newObjectIDRangeStart`  
 [in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊新的 (記憶體回收後) 開始位址。  
  
 `cObjectIDRangeLength`  
 [in] 一個整數的陣列，其中每一個都是記憶體中連續物件區塊的大小。  
  
 已指定大小給 `oldObjectIDRangeStart` 和 `newObjectIDRangeStart` 陣列中被參考的每個區塊。  
  
## <a name="remarks"></a>備註  
 壓縮記憶體回收行程會回收無作用物件所佔用的記憶體，且會壓縮釋放的空間。 如此一來，即時物件可能在堆積中移動，且先前通知所散發 `ObjectID` 的值可能會變更。  
  
 假定現有 `ObjectID` 的值 (`oldObjectID`) 位於下列範圍內：  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 在此情況下，從範圍開頭到物件開頭的位移如下所示：  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 對於位於下列範圍內的任何 `i` 值：  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 您可以計算新的 `ObjectID`，如下所示：  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ （ `oldObjectID` – `oldObjectIDRangeStart[i]` ）  
  
 `MovedReferences2` 方法在回呼自己期間所傳遞的 `ObjectID` 值都無效，因為記憶體回收行程可能正在將物件從舊位置移至新位置。 因此，分析工具不應嘗試在 `MovedReferences2` 呼叫期間檢查物件。 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)回呼表示所有物件都已移至其新位置，而且可以執行檢查。  
  
 如果分析工具同時執行[ICorProfilerCallback](icorprofilercallback-interface.md)和[ICorProfilerCallback4](icorprofilercallback4-interface.md)介面，則會在 `MovedReferences2` [ICorProfilerCallback：： MovedReferences](icorprofilercallback-movedreferences-method.md)方法之前呼叫方法，但只有在方法成功傳回時才會呼叫 `MovedReferences2` 。 分析工具可傳回 HRESULT，表示 `MovedReferences2` 方法中的失敗，以避免呼叫第二個方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [MovedReferences 方法](icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
