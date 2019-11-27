---
title: FunctionLeave2 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446024"
---
# <a name="functionleave2-function"></a>FunctionLeave2 函式
通知分析工具，函式即將傳回給呼叫端，並提供堆疊框架和函數傳回值的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>參數  
 `funcId`  
 在傳回之函式的識別碼。  
  
 `clientData`  
 在重新對應的函式識別碼，分析工具先前透過[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函數指定。  
  
 `func`  
 在`COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。  
  
 分析工具應該將此視為不透明的控制碼，以便在[ICorProfilerInfo2：： GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法中傳回給執行引擎。  
  
 `retvalRange`  
 在[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構的指標，指定函式傳回值的記憶體位置。  
  
 為了存取傳回值資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_RETVAL` 旗標。 分析工具可以使用[ICorProfilerInfo：： SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。  
  
## <a name="remarks"></a>備註  
 `FunctionLeave2` 函數傳回之後，`func` 和 `retvalRange` 參數的值無效，因為這些值可能會變更或終結。  
  
 `FunctionLeave2` 函數是回呼;您必須加以執行。 此執行必須使用 `__declspec`（`naked`）儲存類別屬性。  
  
 在呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。  
  
- 結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。  
  
 `FunctionLeave2` 的執行不應該封鎖，因為它會延遲垃圾收集。 執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。 如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionLeave2` 傳回為止。  
  
 此外，`FunctionLeave2` 函式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
