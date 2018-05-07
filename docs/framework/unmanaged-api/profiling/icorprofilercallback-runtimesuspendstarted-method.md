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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1197f066332ee131e4ee18fee6487b78b36e5081
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted 方法
通知分析工具執行階段即將暫停執行階段的所有執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
#### <a name="parameters"></a>參數  
 `suspendReason`  
 [in]值為[COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)列舉，指出暫止的原因。  
  
## <a name="remarks"></a>備註  
 允許在 unmanaged 程式碼中的所有執行階段執行緒繼續執行，直到嘗試重新進入執行階段。 此時，它們也會被暫止直到執行階段繼續。 這也適用於新的執行緒進入執行階段。 執行階段中的所有執行緒都都在立即暫止都已中斷的程式碼，或者都會要求他們在到達可中斷的程式碼時暫停。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [RuntimeSuspendAborted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)  
 [RuntimeSuspendFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
