---
title: ICorProfilerCallback::RootReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865957"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences 方法
在垃圾收集之後，使用根參考的相關資訊來通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>參數  
 `cRootRefs`  
 在`rootRefIds` 陣列中的參考數目。  
  
 `rootRefIds`  
 在物件識別碼的陣列，參考堆疊上的靜態物件或物件。  
  
## <a name="remarks"></a>備註  
 `RootReferences` 和[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)都會呼叫來通知分析工具。 分析工具通常會實作為其中之一，但不會同時執行這兩個，因為傳入的資訊 `RootReferences2` 是傳入 `RootReferences`的超集合。  
  
 `rootRefIds` 陣列可以包含 null 物件。 例如，在堆疊上宣告的所有物件參考都會被垃圾收集行程視為根，而且一律會報告。  
  
 在回呼本身期間，`RootReferences` 傳回的物件識別碼無效，因為垃圾收集可能正在將物件從舊位址移至新位址。 因此，分析工具不得嘗試在 `RootReferences` 呼叫期間檢查物件。 呼叫[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)時，所有物件都已移至其新位置，而且可以安全地進行檢查。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
