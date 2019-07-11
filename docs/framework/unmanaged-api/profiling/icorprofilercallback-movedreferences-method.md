---
title: ICorProfilerCallback::MovedReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c037f2509aaa0a5e4c3f7a844614742b6f21bec3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769133"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences 方法
呼叫以報告壓縮記憶體回收造成的堆積中物件的新配置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>參數  
 `cMovedObjectIDRanges`  
 [in] 壓縮記憶體回收造成移動的連續物件區塊數目。 也就是 `cMovedObjectIDRanges` 的值是 `oldObjectIDRangeStart`、`newObjectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的總大小。  
  
 下面 `MovedReferences` 的三個引數是平行陣列。 換句話說，`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]` 和 `cObjectIDRangeLength[i]` 全都會考量連續物件的單一區塊。  
  
 `oldObjectIDRangeStart`  
 [in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊舊的 (記憶體回收前) 開始位址。  
  
 `newObjectIDRangeStart`  
 [in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊新的 (記憶體回收後) 開始位址。  
  
 `cObjectIDRangeLength`  
 [in] 一個整數的陣列，其中每一個都是記憶體中連續物件區塊的大小。  
  
 已指定大小給 `oldObjectIDRangeStart` 和 `newObjectIDRangeStart` 陣列中被參考的每個區塊。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  對於在 64 位元平台上大於 4 GB 的物件，這個方法會報告大小為 `MAX_ULONG`。 若要取得大於 4 GB 的物件的大小，請使用[ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)方法改為。  
  
 壓縮記憶體回收行程會回收無作用物件所佔用的記憶體，且會壓縮釋放的空間。 如此一來，即時物件可能在堆積中移動，且先前通知所散發 `ObjectID` 的值可能會變更。  
  
 假定現有 `ObjectID` 的值 (`oldObjectID`) 位於下列範圍內：  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 在此情況下，從範圍開頭到物件開頭的位移如下所示：  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 對於位於下列範圍內的任何 `i` 值：  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 您可以計算新的 `ObjectID`，如下所示：  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
           `MovedReferences` 方法在自行回呼期間所傳遞的 `ObjectID` 值都無效，因為記憶體回收可能正在將物件從舊位置移至新位置。 因此，分析工具不應嘗試在 `MovedReferences` 呼叫期間檢查物件。 A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)回呼表示所有物件都已都移至其新位置，而且可以執行檢查。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
