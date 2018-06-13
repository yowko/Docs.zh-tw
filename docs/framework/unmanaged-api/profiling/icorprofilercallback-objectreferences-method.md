---
title: ICorProfilerCallback::ObjectReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e64eeff8ef80aa264c9c49bd12a0cc45e0da18a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461883"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences 方法
通知分析工具有關記憶體中所指定的物件所參考的物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a>參數  
 `objectId`  
 [in]參考物件的物件識別碼。  
  
 `classId`  
 [in]類別的指定的物件的執行個體識別碼。  
  
 `cObjectRefs`  
 [in]所指定的物件參考的物件數目 (亦即中的元素數目`objectRefIds`陣列)。  
  
 `objectRefIds`  
 [in]所參考的物件識別碼的陣列`objectId`。  
  
## <a name="remarks"></a>備註  
 `ObjectReferences`方法針對每個物件在堆積中剩餘的記憶體回收完成之後呼叫。 如果分析工具從此回呼傳回錯誤，程式碼剖析服務將中止直到下一個記憶體回收叫用這個回呼。  
  
 `ObjectReferences`回呼可以用於搭配[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)回呼，以建立完整的物件參考圖形，執行階段。 Common language runtime (CLR) 可確保每個物件參考由一次報告`ObjectReferences`方法。  
  
 所傳回的物件識別碼`ObjectReferences`不自行，回呼期間有效，因為記憶體回收可能正在將物件移。 因此，分析工具必須不嘗試期間檢查物件`ObjectReferences`呼叫。 當[icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)呼叫時，記憶體回收集合已完成，而且可以安全地進行檢查。  
  
 Null`ClassId`表示`objectId`正在卸載的類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
