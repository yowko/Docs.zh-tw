---
title: ICorProfilerCallback::ModuleUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: fd35f47c004d1ffb235cefe1cd2a1eb2c1fffaef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503311"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a>ICorProfilerCallback::ModuleUnloadFinished 方法
通知 profiler 模組已完成卸載。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在已卸載之模組的識別碼。  
  
 `hrStatus`  
 在HRESULT，指出模組是否已成功卸載。  
  
## <a name="remarks"></a>備註  
 在 `moduleId` [ICorProfilerCallback：： ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md)方法傳回之後，的值對資訊要求而言是不正確。  
  
 卸載類別的某些部分可能會在回呼之後繼續進行 `ModuleUnloadFinished` 。 中的失敗 HRESULT `hrStatus` 表示失敗。 不過，中的成功 HRESULT `hrStatus` 只會指出卸載模組的第一個部分已成功。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
