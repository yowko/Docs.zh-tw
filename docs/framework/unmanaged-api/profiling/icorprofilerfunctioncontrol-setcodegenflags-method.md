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
ms.openlocfilehash: 88c9f552b73af69ea4e1f64b75ed74ea762dcdfb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429934"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags 方法
設定[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉中的一或多個旗標，以控制即時（JIT）重新編譯函式的程式碼產生。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>參數  
 `flags`  
 在來自[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉的一或多個旗標。  
  
## <a name="remarks"></a>備註  
 分析工具會透過[ICorProfilerCallback4：： GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)回呼來取得此介面的實例。 `SetCodegenFlags` 可讓 profiler 控制重新編譯函式的程式碼產生。 如同所有其他 JIT 重新編譯參數，程式碼產生旗標適用于函式的所有實例。  
  
 在編譯函式時，JIT 編譯程式會考慮這些編譯旗標以及其他來源所指定的其他旗標。  其他來源包括偵錯工具、在啟動時使用[ICorProfilerInfo：： SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法（加上值 `COR_PRF_DISABLE_INLINING` 和 `COR_PRF_DISABLE_OPTIMIZATIONS`）和分析工具的[ICorProfilerCallback：： JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼所設定的全域旗標。  JIT 編譯程式會優先于要求最少量優化的來源。  例如，如果分析工具在啟動時指定 `COR_PRF_DISABLE_INLINING`，但未在[ICorProfilerFunctionControl：： SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)回呼中指定 `COR_PRF_CODEGEN_DISABLE_INLINING`，則仍會停用內嵌功能。  同樣地，如果分析工具未在 `SetCodegenFlags`中指定 `COR_PRF_CODEGEN_DISABLE_INLINING`，然後使用[ICorProfilerCallback：： JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼來停用內嵌，則會停用內嵌功能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerFunctionControl 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
