---
title: "ICorProfilerCallback::ObjectsAllocatedByClass 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectsAllocatedByClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4adeda7ac884b37bcfc2b0c9599dd8e36c469747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass 方法
通知分析工具有關的每個指定的類別已建立最新的記憶體回收回收後的執行個體數目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a>參數  
 `cClassCount`  
 [in]大小`classIds`和`cObjects`陣列。  
  
 `classIds`  
 [in]陣列的類別識別碼，其中每個識別碼與一或多個執行個體中指定的類別。  
  
 `cObjects`  
 [in]整數，指定每個整數的中的對應類別執行個體數目的陣列`classIds`陣列。  
  
## <a name="remarks"></a>備註  
 `classIds`和`cObjects`是平行陣列。 例如，`classIds[i]`和`cObjects[i]`參考相同的類別。 自上一個記憶體回收之後建立的類別執行個體之後，如果省略，則此類別。 `ObjectsAllocatedByClass`回呼不會報告在大型物件堆積中配置的物件。  
  
 所報告的數字`ObjectsAllocatedByClass`都只是估計值。 確切計數，使用[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。  
  
 `classIds`陣列可能包含一或多個 null 項目，如果對應`cObjects`陣列有要卸載的類型。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
