---
title: ICorProfilerCallback::ThreadDestroyed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 07041d06668d474a3d30968fb623854a24ebf0eb
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865814"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a>ICorProfilerCallback::ThreadDestroyed 方法
通知分析工具，執行緒已遭終結。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>參數  
 `threadId`  
 在已終結之執行緒的識別碼。  
  
## <a name="remarks"></a>備註  
 此呼叫時，`threadId` 值已不再有效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ThreadCreated 方法](icorprofilercallback-threadcreated-method.md)
