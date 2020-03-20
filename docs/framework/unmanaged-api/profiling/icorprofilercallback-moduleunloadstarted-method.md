---
title: ICorProfilerCallback::ModuleUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: fcfdddbd5316c098754ea7b0d4714b050c64fe55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175144"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a>ICorProfilerCallback::ModuleUnloadStarted 方法
通知探測器正在卸載模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 [在]正在卸載的模組的 ID。  
  
## <a name="remarks"></a>備註  
 返回`ModuleUnloadStarted`後，`moduleId`值對資訊請求無效 - 這是探測器獲取有關此模組資訊的最後機會。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ModuleUnloadFinished 方法](icorprofilercallback-moduleunloadfinished-method.md)
