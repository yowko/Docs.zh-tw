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
ms.openlocfilehash: 2d084ce0a785ba37c5b7dc937ed116cee74b7594
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720655"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences 方法

在垃圾收集之後，以根參考的相關語音總機 profiler。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>參數  

 `cRootRefs`  
 在陣列中的參考數目 `rootRefIds` 。  
  
 `rootRefIds`  
 在物件識別碼的陣列，參考靜態物件或堆疊上的物件。  
  
## <a name="remarks"></a>備註  

 `RootReferences`和[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)都會呼叫以通知分析工具。 分析工具通常會執行其中一項，但不能同時執行，因為傳入的資訊 `RootReferences2` 是傳入的超集合 `RootReferences` 。  
  
 `rootRefIds`陣列可能包含 null 物件。 例如，在堆疊上宣告的所有物件參考都會被垃圾收集行程視為根，而且一律會進行報告。  
  
 在 `RootReferences` 回呼本身期間，傳回的物件識別碼不是有效的，因為垃圾收集可能是在將物件從舊位址移至新位址的中間。 因此，分析工具不能在呼叫期間嘗試檢查物件 `RootReferences` 。 呼叫 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) 時，所有物件都已移至其新位置，而且可以安全地進行檢查。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
