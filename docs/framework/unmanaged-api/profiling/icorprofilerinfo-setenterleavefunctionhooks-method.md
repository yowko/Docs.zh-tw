---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 18aed5c5314fc1057767b599c538952a1d4d6b57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722228"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法

指定要在 managed 函式的 "enter"、"leave" 和 "tailcall" 攔截上呼叫的程式碼剖析工具所執行的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>參數  

 `pFuncEnter`  
 在要當做 [FunctionEnter](functionenter-function.md) 回呼使用的實作為指標。  
  
 `pFuncLeave`  
 在要當做 [FunctionLeave](functionleave-function.md) 回呼使用的實作為指標。  
  
 `pFuncTailcall`  
 在要當做 [FunctionTailcall](functiontailcall-function.md) 回呼使用的實作為指標。  
  
## <a name="remarks"></a>備註  

 在 .NET Framework 1.0 版中，每個函式指標都可以是 null，以停用該對應的回呼。  
  
 一次只能有一組回呼處於作用中。 因此，如果 profiler 同時呼叫 `SetEnterLeaveFunctionHooks` 和 [ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，則 `SetEnterLeaveFunctionHooks2` 會優先使用。  
  
 您 `SetEnterLeaveFunctionHooks` 只能從分析工具的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 回呼呼叫此方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
