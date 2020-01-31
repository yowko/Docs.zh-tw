---
title: ICorProfilerCallback::ObjectsAllocatedByClass 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 028207486f43e35086ed2e515eb3ae6bca304491
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866068"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass 方法
通知分析工具關於最近一次垃圾收集之後所建立之每個指定類別的實例數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>參數  
 `cClassCount`  
 在`classIds` 和 `cObjects` 陣列的大小。  
  
 `classIds`  
 在類別識別碼的陣列，其中的每個識別碼會指定具有一或多個實例的類別。  
  
 `cObjects`  
 在整數的陣列，其中每個整數會指定 `classIds` 陣列中對應類別的實例數目。  
  
## <a name="remarks"></a>備註  
 `classIds` 和 `cObjects` 陣列是平行陣列。 例如，`classIds[i]` 和 `cObjects[i]` 參考相同的類別。 如果自從上一次垃圾收集之後，尚未建立類別的實例，則會省略類別。 `ObjectsAllocatedByClass` 回呼不會報告在大型物件堆積中所配置的物件。  
  
 `ObjectsAllocatedByClass` 回報的數位僅供估計。 如需確切計數，請使用[ICorProfilerCallback：： ObjectAllocated](icorprofilercallback-objectallocated-method.md)。  
  
 如果對應的 `cObjects` 陣列具有正在卸載的類型，`classIds` 陣列可能會包含一或多個 null 專案。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
