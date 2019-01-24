---
title: ICorProfilerCallback::ObjectAllocated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1c777a2512306c41413377530576fbe8ad8e7ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582264"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated 方法
通知分析工具已配置的記憶體中堆積物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a>參數  
 `objectId`  
 [in]配置記憶體的物件識別碼。  
  
 `classId`  
 [in]類別物件的執行個體的識別碼。  
  
## <a name="remarks"></a>備註  
 `ObjectedAllocated`不會從堆疊或未受管理的記憶體配置呼叫方法。 `classId`參數可以參考尚未載入的 managed 程式碼中的類別。 分析工具將會收到該類別的類別載入回呼之後立即`ObjectAllocated`回呼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
