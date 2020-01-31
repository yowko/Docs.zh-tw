---
title: ICorProfilerCallback::ModuleLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 661229e5fbd5d106662f0e823a1753bd76c33311
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866165"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished 方法
通知 profiler 模組已完成載入。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在已完成載入之模組的識別碼。  
  
 `hrStatus`  
 在HRESULT，指出模組是否已成功載入。  
  
## <a name="remarks"></a>備註  
 在呼叫 `ModuleLoadFinished` 方法之前，`moduleId` 的值對資訊要求而言是不正確。  
  
 載入模組的某些部分可能會在 `ModuleLoadFinished` 回呼之後繼續進行。 `hrStatus` 中的失敗 HRESULT 表示失敗。 不過，`hrStatus` 中的成功 HRESULT 只會指出載入模組的第一個部分已成功。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ModuleLoadStarted 方法](icorprofilercallback-moduleloadstarted-method.md)
