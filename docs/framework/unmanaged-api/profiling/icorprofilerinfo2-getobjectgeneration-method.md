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
ms.openlocfilehash: 4ba404692bef84c0522a799c61f07eac341eaab4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703840"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration 方法

取得包含指定物件之堆積的區段。  
  
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
 擴展 [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) 結構的指標，其描述範圍 (也就是在產生中進行垃圾收集的區塊) 記憶體。 此範圍包含指定的物件。  
  
## <a name="remarks"></a>備註  

 `GetObjectGeneration`如果垃圾收集不在進行中，則可以從任何分析工具回呼呼叫方法。 也就是說，它可以從任何回呼呼叫，除了 [ICorProfilerCallback2：： GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) 和 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)之間發生的回呼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
