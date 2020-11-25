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
ms.openlocfilehash: 3593b07759b4d6feee239042e5aabaf0876fdd1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716300"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags 方法

從 [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) 列舉設定一或多個旗標，以控制及時 (JIT) 重新編譯函式的程式碼產生。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>參數  

 `flags`  
 在 [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) 列舉中的一或多個旗標。  
  
## <a name="remarks"></a>備註  

 Profiler 會透過 [ICorProfilerCallback4：： GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) 回呼取得這個介面的實例。 `SetCodegenFlags` 允許 profiler 控制重新編譯函式的程式碼產生。 如同所有其他 JIT 重新編譯參數，程式碼產生旗標適用于函式的所有實例。  
  
 編譯函式時，JIT 編譯程式會考慮這些編譯旗標以及其他來源所指定的其他旗標。  其他來源包括偵錯工具、使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md) 方法在啟動時設定的全域旗標 (與值 `COR_PRF_DISABLE_INLINING` 和 `COR_PRF_DISABLE_OPTIMIZATIONS`) ，以及分析工具的 [ICorProfilerCallback：： JITInlining](icorprofilercallback-jitinlining-method.md) 回呼。  JIT 編譯程式優先于要求最少量優化的來源。  例如，如果分析工具 `COR_PRF_DISABLE_INLINING` 在啟動時指定，但是未 `COR_PRF_CODEGEN_DISABLE_INLINING` 在 [ICorProfilerFunctionControl：： SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) 回呼中指定，則仍會停用內嵌。  同樣地，如果分析工具未 `COR_PRF_CODEGEN_DISABLE_INLINING` 在中指定 `SetCodegenFlags` ，但接著使用 [ICorProfilerCallback：： JITInlining](icorprofilercallback-jitinlining-method.md) 回呼停用內嵌，則會停用內嵌。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerFunctionControl 介面](icorprofilerfunctioncontrol-interface.md)
