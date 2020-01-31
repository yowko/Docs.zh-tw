---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: 4fe18b4f07e6f282571b13faff5ce51b66ce416b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868482"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法
指定將在 managed 函式的[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)勾點上呼叫的分析工具所執行的函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>參數  
 `pFuncEnter3`  
 在要當做 `FunctionEnter3WithInfo` 回呼使用的實作為指標。  
  
 `pFuncLeave3`  
 在要當做 `FunctionLeave3WithInfo` 回呼使用的實作為指標。  
  
 `pFuncTailcall3`  
 在要當做 `FunctionTailcall3WithInfo` 回呼使用的實作為指標。  
  
## <a name="remarks"></a>備註  
 [FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)勾點提供了堆疊框架和引數檢查。 若要存取該資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_ARGS`、`COR_PRF_ENABLE_FUNCTION_RETVAL`和/或 `COR_PRF_ENABLE_FRAME_INFO` 旗標。 分析工具可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標，然後使用 `SetEnterLeaveFunctionHooks3WithInfo` 方法來註冊此函式的實作為。  
  
 一次只能有一組回呼處於作用中狀態，而最新的版本會優先使用。 因此，如果 profiler 同時呼叫[SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)和 `SetEnterLeaveFunctionHooks3WithInfo`，就會使用 `SetEnterLeaveFunctionHooks3WithInfo`。  
  
 只能從分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼呼叫 `SetEnterLeaveFunctionHooks3WithInfo` 方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
