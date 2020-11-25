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
ms.openlocfilehash: 17396d3038578c16b74c3717174dc0fa4dc17631
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722839"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 函式

通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於該函式的 [FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和 [FunctionTailcall2](functiontailcall2-function.md) 回呼中。 `FunctionIDMapper` 也可讓分析工具指出它是否要接收該函式的回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>參數

- `funcId`

  \[in] 要重新對應的函數識別碼。

- `pbHookFunction`

  \[out：當分析工具 `true` 想要接收、和回呼時，所設定的值 `FunctionEnter2` 指標 `FunctionLeave2` `FunctionTailcall2` ; 否則，它會將此值設定為 `false` 。

## <a name="return-value"></a>傳回值  

 分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。 傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。 否則，null 傳回值會產生無法預測的結果，包括可能會停止進程。  
  
## <a name="remarks"></a>備註  

 `FunctionIDMapper`函數是回呼。 程式碼剖析工具會執行它，以將函式識別碼重新對應至其他對分析工具更有用的識別碼。 `FunctionIDMapper`會傳回要用於任何指定函數的替代識別碼。 然後，執行引擎會藉由將此替代識別碼（除了傳統的函式識別碼）傳遞回分析工具的要求， `clientData` `FunctionEnter2` `FunctionLeave2` 以識別要呼叫攔截器的函式 `FunctionTailcall2` 。  
  
 您可以使用 [ICorProfilerInfo：： SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) 方法來指定函式的實作為 `FunctionIDMapper` 。 您 `ICorProfilerInfo::SetFunctionIDMapper` 只能呼叫一次此方法，我們建議您在 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 回呼中這樣做。  
  
 根據預設，假設分析工具會使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)來設定 COR_PRF_MONITOR_ENTERLEAVE 旗標，並透過 [ICorProfilerInfo：： SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) 或 [ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)設定勾點，則應該接收 `FunctionEnter2` `FunctionLeave2` 每個函數的、和 `FunctionTailcall2` 回呼。 不過，分析工具可能會藉 `FunctionIDMapper` 由將設定為，以選擇性地避免針對某些函數接收這些回呼 `pbHookFunction` `false` 。  
  
 分析工具應可容忍程式碼剖析應用程式的多個執行緒同時呼叫相同方法/函式的情況。 在這種情況下，分析工具可能會收到相同的多個 `FunctionIDMapper` 回呼 `FunctionID` 。 當使用相同的多次呼叫此回呼時，分析工具應該會傳回相同的值 `FunctionID` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [SetFunctionIDMapper 方法](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 函式](functionidmapper2-function.md)
- [FunctionEnter2 函式](functionenter2-function.md)
- [FunctionLeave2 函式](functionleave2-function.md)
- [FunctionTailcall2 函式](functiontailcall2-function.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
