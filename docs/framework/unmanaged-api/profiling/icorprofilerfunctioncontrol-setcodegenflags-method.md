---
title: ICorProfilerFunctionControl::SetCodegenFlags 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 286d8494990c528e810f20f3fe5bfb986fdd267a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487679"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags 方法
設定從一或多個旗標[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉來控制產生程式碼在 just-in-time (JIT) 編譯函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>參數  
 `flags`  
 [in]從一或多個旗標[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉型別。  
  
## <a name="remarks"></a>備註  
 分析工具取得透過這個介面的執行個體[ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)回呼。 `SetCodegenFlags` 可讓分析工具，來控制重新編譯的函式的程式碼產生。 如同其他所有的 JIT 重新編譯參數，程式碼產生旗標適用於函式的所有執行個體。  
  
 JIT 編譯器會考慮這些編譯旗標，以及編譯函式時，由其他來源中，指定其他旗標。  其他來源包括偵錯工具、 全域旗標設定在所啟動的分析工具使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法 (具有值`COR_PRF_DISABLE_INLINING`並`COR_PRF_DISABLE_OPTIMIZATIONS`)，和分析工具的[Icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼。  JIT 編譯器會提供要求最少的最佳化來源的優先順序。  例如，如果指定的程式碼剖析工具`COR_PRF_DISABLE_INLINING`在啟動時，但未指定`COR_PRF_CODEGEN_DISABLE_INLINING`中[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)回呼中，內嵌仍然停用。  同樣地，如果未指定分析工具`COR_PRF_CODEGEN_DISABLE_INLINING`中`SetCodegenFlags`，然後停用內嵌使用，但[icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼中，內嵌已停用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerFunctionControl 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
