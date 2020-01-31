---
title: ICorProfilerCallback2::RootReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: a9ce9a7a56847efcadf09924ffc56c41f20a1c58
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865723"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 方法
在垃圾收集發生後，通知分析工具關於根參考。 這個方法是[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)方法的延伸。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>參數  
 `cRootRefs`  
 在`rootRefIds`、`rootKinds`、`rootFlags`和 `rootIds` 陣列中的元素數目。  
  
 `rootRefIds`  
 在物件識別碼的陣列，其中每一個都會參考堆疊上的靜態物件或物件。 `rootKinds` 陣列中的元素會提供資訊來分類 `rootRefIds` 陣列中的對應元素。  
  
 `rootKinds`  
 在[COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md)值的陣列，表示垃圾收集根目錄的類型。  
  
 `rootFlags`  
 在[COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md)值的陣列，描述垃圾收集根目錄的屬性。  
  
 `rootIds`  
 在UINT_PTR 值的陣列，這些值會指向包含垃圾收集根目錄之其他資訊的整數，視 `rootKinds` 參數的值而定。  
  
 如果根的類型是堆疊，則根識別碼適用于包含變數的函式。 如果該根識別碼為0，則函式是 CLR 內部的未命名函數。 如果根的類型是控制碼，則根識別碼是用於垃圾收集控制碼。 對於其他根類型，識別碼是不透明的值，應該予以忽略。  
  
## <a name="remarks"></a>備註  
 `rootRefIds`、`rootKinds`、`rootFlags`和 `rootIds` 陣列都是平行陣列。 也就是說，`rootRefIds[i]`、`rootKinds[i]`、`rootFlags[i]`和 `rootIds[i]` 全都關心相同的根。  
  
 `RootReferences` 和 `RootReferences2` 都會呼叫來通知分析工具。 分析工具通常會實作為一個方法，但不能同時執行兩者，因為傳入的資訊 `RootReferences2` 是傳入 `RootReferences`的超集合。  
  
 `rootRefIds` 中的專案可能是零，這表示對應的根參考是 null，而且不會參考 managed 堆積上的物件。  
  
 在回呼本身期間，`RootReferences2` 傳回的物件識別碼無效，因為垃圾收集可能正在將物件從舊位址移至新位址。 因此，分析工具不應嘗試在 `RootReferences2` 呼叫期間檢查物件。 呼叫[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)時，所有物件都已移至其新位置，而且可以安全地進行檢查。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
