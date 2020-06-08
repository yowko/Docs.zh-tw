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
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497448"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法
指定要在「輸入」、「離開」和 managed 函式的「tailcall」攔截器上呼叫的分析工具所實函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>參數  
 `pFuncEnter`  
 在要當做[FunctionEnter](functionenter-function.md)回呼使用的實作為指標。  
  
 `pFuncLeave`  
 在要當做[FunctionLeave](functionleave-function.md)回呼使用的實作為指標。  
  
 `pFuncTailcall`  
 在要當做[FunctionTailcall](functiontailcall-function.md)回呼使用的實作為指標。  
  
## <a name="remarks"></a>備註  
 在 .NET Framework 版本1.0 中，每個函式指標都可以是 null，以停用該對應的回呼。  
  
 一次只能使用一組回呼。 因此，如果 profiler 同時呼叫 `SetEnterLeaveFunctionHooks` 和[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，則 `SetEnterLeaveFunctionHooks2` 會優先使用。  
  
 只能 `SetEnterLeaveFunctionHooks` 從分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼呼叫方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
