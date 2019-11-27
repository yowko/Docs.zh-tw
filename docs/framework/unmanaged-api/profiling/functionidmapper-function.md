---
title: FunctionIDMapper 函式
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440698"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 函式
通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於該函式的[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)回呼。 `FunctionIDMapper` 也可以讓分析工具指出它是否想要接收該函式的回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>參數  
 `funcId`  
 [in] 要重新對應的函式識別項。  
  
 `pbHookFunction`  
 脫銷值的指標，如果它想要接收 `FunctionEnter2`、`FunctionLeave2`和 `FunctionTailcall2` 回呼，則會將它設定為 `true`。否則，它會將此值設定為 `false`。  
  
## <a name="return-value"></a>傳回值  
 分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。 傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。 否則，null 傳回值會產生無法預測的結果，包括可能會停止進程。  
  
## <a name="remarks"></a>備註  
 `FunctionIDMapper` 函數是回呼。 分析工具會執行此程式碼剖析工具，將函式識別碼重新對應至其他對分析工具更有用的識別碼。 `FunctionIDMapper` 會傳回要用於任何指定函數的替代識別碼。 然後執行引擎會接受分析工具的要求，方法是將此替代識別碼（除了傳統的函式識別碼）傳回到 `FunctionEnter2`、`FunctionLeave2`和 `FunctionTailcall2` 勾點之 `clientData` 參數中的分析工具，以識別要呼叫其攔截器的函式。  
  
 您可以使用[ICorProfilerInfo：： SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)方法來指定 `FunctionIDMapper` 函數的執行。 您只能呼叫 `ICorProfilerInfo::SetFunctionIDMapper` 方法一次，因此建議您在[ICorProfilerCallback：： Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼中執行此動作。  
  
 根據預設，假設分析工具會使用[ICorProfilerInfo：： SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)設定 COR_PRF_MONITOR_ENTERLEAVE 旗標，並透過[ICorProfilerInfo：： SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)或[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)設定勾點，應該會收到每個函數的 `FunctionEnter2`、`FunctionLeave2`和 `FunctionTailcall2` 回呼。 不過，分析工具可能 `FunctionIDMapper` 會將 `pbHookFunction` 設定為 `false`，藉以選擇性地避免收到特定函式的這些回呼。  
  
 分析工具應可容忍已剖析應用程式的多個執行緒同時呼叫相同方法/函式的情況。 在這種情況下，分析工具可能會收到相同 `FunctionID`的多個 `FunctionIDMapper` 回呼。 當使用相同的 `FunctionID`多次呼叫分析工具時，應該一定要從這個回呼傳回相同的值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [SetFunctionIDMapper 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
