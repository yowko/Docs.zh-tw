---
title: "ICorProfilerCallback4::SurvivingReferences2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.SurvivingReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ced8542d2e84b6c317e20d7ff440e6c159383bfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 方法
報告堆積中物件的配置做為非壓縮記憶體回收的結果。 如果分析工具已實作，會呼叫這個方法[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)介面。 此回呼會取代[icorprofilercallback2:: Survivingreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)方法，因為它會報告更大範圍的物件，其長度超過在 ULONG 中能表示。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>參數  
 `cSurvivingObjectIDRanges`  
 [in] 非壓縮記憶體回收後未被回收的連續物件區塊數目。 也就是說，`cSurvivingObjectIDRanges` 的值是 `objectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的大小，會為每個物件區塊分別存放 `ObjectID` 和長度。  
  
 `SurvivingReferences2` 的下兩個引數是平行陣列。 換句話說，`objectIDRangeStart` 和 `cObjectIDRangeLength` 會考量連續物件的相同區塊。  
  
 `objectIDRangeStart`  
 [in] `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊的開始位址。  
  
 `cObjectIDRangeLength`  
 [in] 整數的陣列，其中每一個都是記憶體中連續物件之未被回收區塊的大小。  
  
 已為 `objectIDRangeStart` 陣列中被參考的每個區塊指定大小。  
  
## <a name="remarks"></a>備註  
 `objectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的項目應解譯如下，以判斷物件是否未被記憶體回收。 假定 `ObjectID` 的值 (`ObjectID`) 位於下列範圍內：  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 針對任何位於下列範圍內的 `i` 之值，該物件尚未被記憶體回收：  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 非壓縮記憶體回收會回收「無作用」物件所佔用的記憶體，但是不會壓縮該釋放的空間。 因此，記憶體會傳回到堆積，但沒有移動「即時」物件。  
  
 針對非壓縮記憶體回收，Common Language Runtime (CLR) 會呼叫 `SurvivingReferences2`。 針對壓縮記憶體回收， [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)改為呼叫。 單一記憶體回收可以為了某個層代而壓縮，但另一個則不壓縮。 對於在任何特定層代的回收，分析工具將接收`SurvivingReferences2`回呼或[MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)回呼，但非兩者。  
  
 因為有限的內部緩衝區、伺服器記憶體回收期間的多重回呼和其他原因，在特定記憶體回收期間可能接收多重 `SurvivingReferences2` 回呼。 在記憶體回收期間多個回呼的情況下，資訊是累計的；在任何 `SurvivingReferences2` 回呼中被報告的所有參考不會被記憶體回收。  
  
 如果分析工具同時實作[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)和[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)介面`SurvivingReferences2`方法之前呼叫[ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)方法，但只有當`SurvivingReferences2`成功傳回。 分析工具可傳回 HRESULT，表示 `SurvivingReferences2` 方法中的失敗，以避免呼叫第二個方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
