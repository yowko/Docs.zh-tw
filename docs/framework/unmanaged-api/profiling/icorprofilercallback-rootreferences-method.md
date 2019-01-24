---
title: ICorProfilerCallback::RootReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94b736a8e3250f4d208d4a9a46a022140b676318
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631345"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences 方法
通知分析工具，但記憶體回收之後根參考的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>參數  
 `cRootRefs`  
 [in]中的參考數目`rootRefIds`陣列。  
  
 `rootRefIds`  
 [in]參考靜態物件或物件在堆疊上的物件識別碼的陣列。  
  
## <a name="remarks"></a>備註  
 兩者`RootReferences`並[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)呼叫以通知分析工具。 分析工具通常會實作，其中一種，但非兩者皆是，因為傳入的資訊`RootReferences2`傳入的超集`RootReferences`。  
  
 可能會`rootRefIds`包含 null 物件的陣列。 比方說，在堆疊上宣告的所有物件參考會被視為由記憶體回收行程的根目錄，並將報告。  
  
 所傳回的物件識別碼`RootReferences`不本身的回呼期間有效，因為記憶體回收可能正在將物件從舊位址移到新的位址。 因此，程式碼剖析工具不得嘗試期間檢查物件`RootReferences`呼叫。 當[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)是呼叫，所有物件都已移至其新位置和可以安全地進行檢查。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
