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
ms.openlocfilehash: 9e53e7bcecd900bb6c71d0a822e9b63ff6726e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729508"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 方法

在垃圾收集發生之後，通知分析工具有關根參考。 這個方法是 [ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md) 方法的延伸。  
  
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
 在 `rootRefIds`、 `rootKinds` 、 `rootFlags` 和陣列中的元素數目 `rootIds` 。  
  
 `rootRefIds`  
 在物件識別碼的陣列，每個物件都會參考靜態物件或堆疊上的物件。 陣列中的專案會 `rootKinds` 提供資訊，以分類陣列中的對應元素 `rootRefIds` 。  
  
 `rootKinds`  
 在 [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) 值的陣列，表示垃圾收集根目錄的型別。  
  
 `rootFlags`  
 在 [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) 值的陣列，這些值會描述垃圾收集根目錄的屬性。  
  
 `rootIds`  
 在UINT_PTR 值的陣列，這些值會根據參數的值，指向包含垃圾收集根目錄之其他資訊的整數 `rootKinds` 。  
  
 如果根的型別是堆疊，則根識別碼適用于包含變數的函式。 如果該根識別碼為0，則函式是 CLR 內部的未命名函數。 如果根的型別是控制碼，則根識別碼是用於垃圾收集控制碼。 如果是其他根類型，則識別碼是不透明的值，應予以忽略。  
  
## <a name="remarks"></a>備註  

 `rootRefIds`、、 `rootKinds` `rootFlags` 和 `rootIds` 陣列是平行陣列。 也就是說，、 `rootRefIds[i]` 、 `rootKinds[i]` `rootFlags[i]` 和 `rootIds[i]` 全都關注相同的根。  
  
 `RootReferences`和 `RootReferences2` 都被呼叫，以通知分析工具。 分析工具通常會實作為一種方法，但不會同時執行兩者，因為傳入的資訊 `RootReferences2` 是傳入的超集合 `RootReferences` 。  
  
 中的專案可能是 `rootRefIds` 零，這表示對應的根參考為 null，且未參考 managed 堆積上的物件。  
  
 在 `RootReferences2` 回呼本身期間，傳回的物件識別碼不是有效的，因為垃圾收集可能是在將物件從舊位址移至新位址的中間。 因此，分析工具不應嘗試在 `RootReferences2` 呼叫期間檢查物件。 呼叫 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) 時，所有物件都已移至其新位置，而且可以安全地進行檢查。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
