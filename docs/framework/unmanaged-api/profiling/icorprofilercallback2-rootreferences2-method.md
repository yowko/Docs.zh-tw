---
title: "ICorProfilerCallback2::RootReferences2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.RootReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29a5a3051b75df18a08498369aa5707a53caf75f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 方法
在記憶體回收發生後，請通知根參考的相關程式碼剖析工具。 這個方法是延伸[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a>參數  
 `cRootRefs`  
 [in]中的項目數`rootRefIds`， `rootKinds`， `rootFlags`，和`rootIds`陣列。  
  
 `rootRefIds`  
 [in]陣列的物件識別碼，其中每個參考的靜態物件或物件在堆疊上。 中的項目`rootKinds`陣列提供資訊給分類中的對應元素`rootRefIds`陣列。  
  
 `rootKinds`  
 [in]陣列[COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)值，表示記憶體回收根目錄的類型。  
  
 `rootFlags`  
 [in]陣列[COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)描述記憶體回收根目錄屬性的值。  
  
 `rootIds`  
 [in]UINT_PTR 陣列值會指向包含記憶體回收根目錄，根據的值的其他資訊的整數`rootKinds`參數。  
  
 如果根型別是指堆疊，根 ID 就是包含變數的函式。 如果該根識別碼為 0，函式是 CLR 內部未命名函式。 如果根型別是控制代碼，根識別碼就是記憶體回收控制代碼。 對於其他根類型識別碼是不透明值，應予忽略。  
  
## <a name="remarks"></a>備註  
 `rootRefIds`， `rootKinds`， `rootFlags`，和`rootIds`是平行陣列。 也就是說， `rootRefIds[i]`， `rootKinds[i]`， `rootFlags[i]`，和`rootIds[i]`全都會考量位於相同的根目錄。  
  
 同時`RootReferences`和`RootReferences2`呼叫以通知分析工具。 分析工具將通常實作一種方法或另一個，但不可同時因為資訊傳入`RootReferences2`為傳入的超集`RootReferences`。  
  
 中的項目可能會`rootRefIds`成為零，表示對應的根參考為 null，且不是指受管理的堆積上的物件。  
  
 所傳回的物件識別碼`RootReferences2`不自行，回呼期間有效，因為記憶體回收可能正在將物件從舊位址移到新的位址。 因此，分析工具不應嘗試在 `RootReferences2` 呼叫期間檢查物件。 當[icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)是呼叫，所有物件都已移至其新位置並且可以安全地進行檢查。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
