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
ms.openlocfilehash: 70d43d7526376c40d0f8358ebd65e4a00a41b969
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701662"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass 方法

通知分析工具有關最近一次垃圾收集之後所建立之每個指定類別的實例數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>參數  

 `cClassCount`  
 在和陣列的大小 `classIds` `cObjects` 。  
  
 `classIds`  
 在類別識別碼的陣列，其中每個識別碼都會指定具有一或多個實例的類別。  
  
 `cObjects`  
 在整數陣列，其中每個整數會指定陣列中對應類別的實例數目 `classIds` 。  
  
## <a name="remarks"></a>備註  

 `classIds`和 `cObjects` 陣列是平行陣列。 例如， `classIds[i]` 和 `cObjects[i]` 參考相同的類別。 如果自上一次垃圾收集之後未建立類別的實例，則會省略類別。 `ObjectsAllocatedByClass`回呼不會報告大型物件堆積中所配置的物件。  
  
 所報告的數位 `ObjectsAllocatedByClass` 只會預估。 針對確切計數，請使用 [ICorProfilerCallback：： ObjectAllocated](icorprofilercallback-objectallocated-method.md)。  
  
 `classIds`如果對應的 `cObjects` 陣列具有正在卸載的型別，陣列可能會包含一個或多個 null 專案。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
