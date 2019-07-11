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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c04b7862363b441ab35d6dd364c4dffaf7464153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769223"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished 方法
通知分析工具已完成載入的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 [in]已完成載入的模組識別碼。  
  
 `hrStatus`  
 [in]HRESULT，指出是否已成功載入的模組。  
  
## <a name="remarks"></a>備註  
 值`moduleId`不是有效資訊要求直到`ModuleLoadFinished`呼叫方法。  
  
 載入模組的某些部分可能會繼續之後`ModuleLoadFinished`回呼。 失敗 HRESULT 中`hrStatus`表示失敗。 不過，成功的 HRESULT 中`hrStatus`僅會指示已成功載入模組的第一個部分。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ModuleLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
