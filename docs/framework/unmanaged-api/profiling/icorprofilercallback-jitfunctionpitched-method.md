---
title: ICorProfilerCallback::JITFunctionPitched 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf51d2a0e7381cd495da8f3846302ec806c34774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched 方法
通知分析工具，已在 just-in-time (JIT) 的函式的編譯已從記憶體移除。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]已移除的函式 ID。  
  
## <a name="remarks"></a>備註  
 如果移除的函式呼叫時，分析工具會收到新的 JIT 編譯事件時重新編譯函式。 目前，common language runtime (CLR) JIT 編譯器不會移除函式的記憶體，因此這個回呼目前未使用和分析工具將不會接收。  
  
 值`functionId`無效，直到重新編譯函式。 重新編譯函式時，相同`functionId`將使用的值。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
