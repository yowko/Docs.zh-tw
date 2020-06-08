---
title: ICorProfilerCallback::RuntimeThreadSuspended 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: 54f7dae511c8bf25dc96451e6477acf26655430a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503194"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended 方法
通知分析工具，指定的執行緒已暫止或即將暫止。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>參數  
 `threadId`  
 在已暫止之執行緒的識別碼。  
  
## <a name="remarks"></a>備註  
 `RuntimeThreadSuspended`通知可以在[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)和相關聯的[ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md)回呼之間的任何時間發生。 在[ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)之間發生的通知， `RuntimeResumeStarted` 適用于已在非受控程式碼中執行，並在進入執行時間時暫停的執行緒。  
  
 一般來說，這個回呼會線上程暫停之後發生。 不過，如果目前執行中的執行緒（呼叫此回呼的執行緒）是要暫止的執行緒，此回呼會線上程暫停之前發生。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [RuntimeThreadResumed 方法](icorprofilercallback-runtimethreadresumed-method.md)
