---
title: ICorProfilerCallback::RuntimeSuspendStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865879"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted 方法
通知分析工具，執行時間即將暫停所有運行時間表程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a>參數  
 `suspendReason`  
 在[COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md)列舉的值，表示暫停的原因。  
  
## <a name="remarks"></a>備註  
 在非受控碼中的所有運行時間表程，都可以繼續執行，直到它們嘗試重新進入執行時間為止。 在該時間點，它們也會暫停，直到執行時間繼續執行為止。 這也適用于輸入執行時間的新執行緒。 執行時間中的所有線程如果已經在可中斷的程式碼中，就會立即暫停，或在到達可中斷的程式碼時，要求他們暫停。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [RuntimeSuspendAborted 方法](icorprofilercallback-runtimesuspendaborted-method.md)
- [RuntimeSuspendFinished 方法](icorprofilercallback-runtimesuspendfinished-method.md)
