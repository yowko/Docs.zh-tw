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
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866087"
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
 在指定物件所參考的物件數目（也就是 `objectRefIds` 陣列中的元素數目）。  
  
 `objectRefIds`  
 在`objectId`所參考之物件的識別碼陣列。  
  
## <a name="remarks"></a>備註  
 在完成垃圾收集之後，會針對堆積中剩餘的每個物件呼叫 `ObjectReferences` 方法。 如果 profiler 從這個回呼傳回錯誤，分析服務將會停止叫用此回呼，直到下一次垃圾收集為止。  
  
 `ObjectReferences` 回呼可以與[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)回呼搭配使用，以建立執行時間的完整物件參考圖形。 Common language runtime （CLR）可確保每個物件參考只會由 `ObjectReferences` 方法回報一次。  
  
 在回呼本身期間，`ObjectReferences` 傳回的物件識別碼無效，因為垃圾收集可能是在移動物件的中間。 因此，分析工具不得嘗試在 `ObjectReferences` 呼叫期間檢查物件。 呼叫[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)時，垃圾收集會完成，而且可以安全地執行檢查。  
  
 Null `ClassId` 表示 `objectId` 具有正在卸載的類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
