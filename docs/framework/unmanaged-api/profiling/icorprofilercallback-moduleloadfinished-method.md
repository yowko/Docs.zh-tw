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
ms.openlocfilehash: 481fc2c40331e31f6a018d012fb2b2543d4fd9b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503363"
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
 在 `moduleId` 呼叫方法之前，的值對資訊要求而言是不正確 `ModuleLoadFinished` 。  
  
 載入模組的某些部分可能會在回呼之後繼續進行 `ModuleLoadFinished` 。 中的失敗 HRESULT `hrStatus` 表示失敗。 不過，中的成功 HRESULT `hrStatus` 只會指出載入模組的第一個部分已成功。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ModuleLoadStarted 方法](icorprofilercallback-moduleloadstarted-method.md)
