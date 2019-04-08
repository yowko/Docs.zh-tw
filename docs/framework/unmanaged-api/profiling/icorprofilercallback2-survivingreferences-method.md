---
title: ICorProfilerCallback2::SurvivingReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da06ce49415317393b3489c2b8f97afc58f7c83b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191298"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences 方法
報告非壓縮記憶體回收造成的堆積中物件配置。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>參數  
 `cSurvivingObjectIDRanges`  
 [in] 非壓縮記憶體回收後未被回收的連續物件區塊數目。 也就是說，`cSurvivingObjectIDRanges` 的值是 `objectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的大小，會為每個物件區塊分別存放 `ObjectID` 和長度。  
  
 `SurvivingReferences` 的下兩個引數是平行陣列。 換句話說，`objectIDRangeStart` 和 `cObjectIDRangeLength` 會考量連續物件的相同區塊。  
  
 `objectIDRangeStart`  
 [in] `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊的開始位址。  
  
 `cObjectIDRangeLength`  
 [in] 整數的陣列，其中每一個都是記憶體中連續物件之未被回收區塊的大小。  
  
 已為 `objectIDRangeStart` 陣列中被參考的每個區塊指定大小。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  對於在 64 位元平台上大於 4 GB 的物件，這個方法會報告大小為 `MAX_ULONG`。 對於大於 4 GB 的物件，使用[ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)方法改為。  
  
 `objectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的項目應解譯如下，以判斷物件是否未被記憶體回收。 假定 `ObjectID` 的值 (`ObjectID`) 位於下列範圍內：  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 針對任何位於下列範圍內的 `i` 之值，該物件尚未被記憶體回收：  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 非壓縮記憶體回收會回收「無作用」物件所佔用的記憶體，但是不會壓縮該釋放的空間。 因此，記憶體會傳回到堆積，但沒有移動「即時」物件。  
  
 針對非壓縮記憶體回收，Common Language Runtime (CLR) 會呼叫 `SurvivingReferences`。 針對壓縮記憶體回收， [icorprofilercallback:: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)改為呼叫。 單一記憶體回收可以為了某個層代而壓縮，但另一個則不壓縮。 對於在任何特定層代上的記憶體回收，分析工具將接收 `SurvivingReferences` 回呼或 `MovedReferences` 回呼，但不可同時接收。  
  
 因為有限的內部緩衝區、在伺服器記憶體回收期間以及其他原因的多重執行緒報告，在特定記憶體回收期間可能接收多重 `SurvivingReferences` 回呼。 在記憶體回收期間多個回呼的情況下，資訊是累計的；在任何 `SurvivingReferences` 回呼中被報告的所有參考不會被記憶體回收。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [SurvivingReferences2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
