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
ms.openlocfilehash: 5fa6ffff3cdb64a7471568e1f6e76fea9194c5a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722280"
---
# <a name="functionleave2-function"></a>FunctionLeave2 函式

通知分析工具，函式即將傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊。  
  
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

- `funcId`

  \[in] 傳回之函式的識別碼。

- `clientData`

  \[in] 重新對應的函式識別碼，分析工具先前透過 [FunctionIDMapper](functionidmapper-function.md) 函式指定。

- `func`

  \[in] `COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。

  分析工具應該將它視為不透明的控制碼，可以傳回給 [ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) 方法中的執行引擎。  
  
- `retvalRange`

  \[in] [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) 結構的指標，指定函式傳回值的記憶體位置。

  為了存取傳回值資訊， `COR_PRF_ENABLE_FUNCTION_RETVAL` 必須設定旗標。 分析工具可以使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md) 方法來設定事件旗標。

## <a name="remarks"></a>備註  

 當函式傳回 `func` 時，和參數的值無效， `retvalRange` `FunctionLeave2` 因為這些值可能會變更或損毀。  
  
 `FunctionLeave2`函數是回呼; 您必須加以執行。 實作為必須使用 `__declspec` (`naked`) 儲存類別屬性。  
  
 在呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。  
  
- 在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。  
  
 的執行 `FunctionLeave2` 不應封鎖，因為它會延遲垃圾收集。 執行不應嘗試垃圾收集，因為堆疊可能不是處於垃圾收集的易記狀態。 如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionLeave2` 。  
  
 此外，此函式 `FunctionLeave2` 不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter2 函式](functionenter2-function.md)
- [FunctionTailcall2 函式](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
