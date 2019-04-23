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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f5d2c08abbcab6bc1a6d0569b8e70d7c919def
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195861"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass 方法
通知分析工具有關的每個指定的類別已自最新的回收之後建立的執行個體數目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>參數  
 `cClassCount`  
 [in]大小`classIds`和`cObjects`陣列。  
  
 `classIds`  
 [in]類別識別碼，其中每個識別碼指定的類別與一或多個執行個體的陣列。  
  
 `cObjects`  
 [in]整數，指定每個整數中的對應類別的執行個體數目的陣列`classIds`陣列。  
  
## <a name="remarks"></a>備註  
 `classIds`和`cObjects`陣列是平行陣列。 例如，`classIds[i]`和`cObjects[i]`參考相同的類別。 如果自上一個記憶體回收之後建立的類別執行個體之後，即會省略的類別。 `ObjectsAllocatedByClass`回呼將不會報告在大型物件堆積中配置的物件。  
  
 所報告的數字`ObjectsAllocatedByClass`是只是估計值。 確切的計數，請使用[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。  
  
 `classIds`陣列可能包含一或多個 null 的項目，如果對應`cObjects`陣列有要卸載的類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
