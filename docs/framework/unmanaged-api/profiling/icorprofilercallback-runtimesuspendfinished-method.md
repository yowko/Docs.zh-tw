---
title: ICorProfilerCallback::RuntimeSuspendFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07e2ebe8afe6002dee6c45f56fa1f11a4083d6bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145596"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a>ICorProfilerCallback::RuntimeSuspendFinished 方法
通知分析工具執行階段已完成的執行階段的所有執行緒暫停。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a>備註  
 Unmanaged 程式碼中的所有執行階段執行緒才能繼續執行，直到他們試著重新進入執行階段。 此時，它們也會擱置直到執行階段繼續。 這也適用於新的執行緒進入執行階段。 在執行階段中的所有執行緒都都在立即暫止，如果他們都已在可中斷的程式碼，或要求他們到達可中斷的程式碼時暫停。  
  
 `RuntimeSuspendFinished`保證在相同的執行緒上進行回呼[icorprofilercallback:: Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)回呼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [RuntimeSuspendAborted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
