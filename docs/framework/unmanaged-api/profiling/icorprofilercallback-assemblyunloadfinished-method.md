---
title: ICorProfilerCallback::AssemblyUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a75d31f0a2c844895363bb4693dbcb5aba4cce1f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775502"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished 方法
通知分析工具已卸載組件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>參數  
 `assemblyId`  
 [in]識別正在卸載組件。  
  
 `hrStatus`  
 [in]HRESULT，表示組件是否已卸載成功。  
  
## <a name="remarks"></a>備註  
 值`assemblyId`不是有效資訊要求之後[icorprofilercallback:: Assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)方法會傳回。  
  
 卸載組件的某些部分可能會繼續之後`AssemblyUnloadFinished`回呼。 失敗 HRESULT 中`hrStatus`表示失敗。 不過，成功的 HRESULT 中`hrStatus`僅會指示已成功卸載組件的第一個部分。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
