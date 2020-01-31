---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868573"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法
指定要在 managed 函式之 "enter"、"leave" 和 "tailcall" 勾點的更新版本上呼叫的分析工具所執行的函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>參數  
 `pFuncEnter`  
 在要當做[FunctionEnter2](functionenter2-function.md)回呼使用的實作為指標。  
  
 `pFuncLeave`  
 在要當做[FunctionLeave2](functionleave2-function.md)回呼使用的實作為指標。  
  
 `pFuncTailcall`  
 在要當做[FunctionTailcall2](functiontailcall2-function.md)回呼使用的實作為指標。  
  
## <a name="remarks"></a>備註  
 `SetEnterLeaveFunctionHooks2` 方法類似于[ICorProfilerInfo：： SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md)方法。 使用前者來指定要當做較新版本的進入/離開/tailcall 回呼使用的函式，而後者則用來指定要當做較舊版本的進入/離開/tailcall 回呼使用的函數。  
  
 一次只能有一組回呼處於作用中狀態。 因此，如果 profiler 同時呼叫 `ICorProfilerInfo::SetEnterLeaveFunctionHooks` 和 `SetEnterLeaveFunctionHooks2`，則會使用 `SetEnterLeaveFunctionHooks2`。  
  
 只能從分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼呼叫 `SetEnterLeaveFunctionHooks2` 方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
