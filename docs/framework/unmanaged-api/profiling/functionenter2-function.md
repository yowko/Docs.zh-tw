---
title: FunctionEnter2 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 6cd35c180b8a322b3402b050c6d6840073010b1f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866979"
---
# <a name="functionenter2-function"></a>FunctionEnter2 函式
通知分析工具控制項正傳遞至函式，並提供堆疊框架和函式引數的相關資訊。 此函式會取代[FunctionEnter](functionenter-function.md)函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>參數

- `funcId`

  中的 \[]）傳遞控制項的函式識別碼。

- `clientData`

  \[in]）重新對應的函式識別碼，也就是先前使用[FunctionIDMapper](functionidmapper-function.md)函數指定的 profiler。
  
- `func`

  \[in]） `COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。
  
  分析工具應該將此視為不透明的控制碼，以便在[ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)方法中傳回給執行引擎。  
  
- `argumentInfo`

  \[in]） [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)結構的指標，指定函數引數的記憶體位置。

  若要存取引數資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_ARGS` 旗標。 分析工具可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。

## <a name="remarks"></a>備註  
 `FunctionEnter2` 函數傳回之後，`func` 和 `argumentInfo` 參數的值無效，因為這些值可能會變更或終結。  
  
 `FunctionEnter2` 函數是回呼;您必須加以執行。 此執行必須使用 `__declspec`（`naked`）儲存類別屬性。  
  
 在呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。  
  
- 結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。  
  
 `FunctionEnter2` 的執行不應該封鎖，因為它會延遲垃圾收集。 執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。 如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionEnter2` 傳回為止。  
  
 此外，`FunctionEnter2` 函式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [FunctionLeave2 函式](functionleave2-function.md)
- [FunctionTailcall2 函式](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
