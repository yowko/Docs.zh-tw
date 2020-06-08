---
title: ICorProfilerInfo2::GetObjectGeneration 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: 1263202c1fe524c924a88b9356e5ab9116cea553
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502856"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration 方法
取得堆積的區段，其中包含指定的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a>參數  
 `objectId`  
 在物件的識別碼。  
  
 `range`  
 脫銷[COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)結構的指標，描述正在進行垃圾收集的層代內的記憶體範圍（也就是區塊）。 此範圍包含指定的物件。  
  
## <a name="remarks"></a>備註  
 `GetObjectGeneration`如果垃圾收集不在進行中，則可以從任何 profiler 回呼呼叫方法。 也就是說，除了在[ICorProfilerCallback2：： GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)和[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)之間發生的回呼以外，它可能會從任何回撥呼叫。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
