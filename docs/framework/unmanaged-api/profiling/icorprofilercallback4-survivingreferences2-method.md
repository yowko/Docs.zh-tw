---
title: ICorProfilerCallback4::SurvivingReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad96224daf79b17d3902217af061173580f1478a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597190"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 方法
報告非壓縮記憶體回收造成的堆積中物件配置。 如果分析工具已實作，會呼叫這個方法[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)介面。 此回呼會取代[ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)方法，因為它會報告更大範圍的物件，其長度超過在 ULONG 中能表示。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>參數  
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
  
 針對非壓縮記憶體回收，Common Language Runtime (CLR) 會呼叫 `SurvivingReferences2`。 針對壓縮記憶體回收， [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)改為呼叫。 單一記憶體回收可以為了某個層代而壓縮，但另一個則不壓縮。 在任何特定層代記憶體回收，分析工具會接收`SurvivingReferences2`回呼或[MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)回呼，但非兩者。  
  
 因為有限的內部緩衝區、伺服器記憶體回收期間的多重回呼和其他原因，在特定記憶體回收期間可能接收多重 `SurvivingReferences2` 回呼。 在記憶體回收期間多個回呼的情況下，資訊是累計的；在任何 `SurvivingReferences2` 回呼中被報告的所有參考不會被記憶體回收。  
  
 如果分析工具同時實作[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)並[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)介面`SurvivingReferences2`方法之前呼叫[ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)方法，但只有當`SurvivingReferences2`成功傳回。 分析工具可傳回 HRESULT，表示 `SurvivingReferences2` 方法中的失敗，以避免呼叫第二個方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
