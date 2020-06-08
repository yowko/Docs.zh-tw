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
ms.openlocfilehash: 12a0792e8fafc73b480de6bacc86f98470dfedf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503285"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences 方法
通知分析工具有關指定物件所參考記憶體中的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>參數  
 `objectId`  
 在參考物件之物件的識別碼。  
  
 `classId`  
 在指定的物件為實例之類別的識別碼。  
  
 `cObjectRefs`  
 在指定物件所參考的物件數目（也就是陣列中的元素數目 `objectRefIds` ）。  
  
 `objectRefIds`  
 在由所參考之物件的識別碼陣列 `objectId` 。  
  
## <a name="remarks"></a>備註  
 在 `ObjectReferences` 完成垃圾收集之後，會針對堆積中剩餘的每個物件呼叫方法。 如果 profiler 從這個回呼傳回錯誤，分析服務將會停止叫用此回呼，直到下一次垃圾收集為止。  
  
 `ObjectReferences`回呼可以與[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)回呼搭配使用，以建立執行時間的完整物件參考圖形。 Common language runtime （CLR）可確保每個物件參考只會被方法報告一次 `ObjectReferences` 。  
  
 在回呼本身期間，所傳回的物件識別碼 `ObjectReferences` 無效，因為垃圾收集可能是在移動物件的中間。 因此，分析工具不得嘗試在呼叫期間檢查物件 `ObjectReferences` 。 呼叫[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)時，垃圾收集會完成，而且可以安全地執行檢查。  
  
 Null `ClassId` 表示 `objectId` 具有正在卸載的類型。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
