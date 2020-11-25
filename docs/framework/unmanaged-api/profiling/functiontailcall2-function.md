---
title: FunctionTailcall2 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: e1cd3ef78d303aaa325699e1bcdec95f077fef21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703976"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 函式

通知分析工具，目前正在執行的函式即將執行另一個函式的 tail 呼叫，並提供堆疊框架的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>參數

- `funcId`

  \[in] 目前正在執行之函式的識別碼，即將進行 tail 呼叫。

- `clientData`

  \[在中，分析工具先前透過 [FunctionIDMapper](functionidmapper-function.md)指定的重新對應函式識別碼，目前正在執行的函式即將進行 tail 呼叫。
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。

  分析工具應該將它視為不透明的控制碼，可以傳回給 [ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) 方法中的執行引擎。

## <a name="remarks"></a>備註  

 Tail 呼叫的目標函式會使用目前的堆疊框架，並且會直接傳回給發出 tail 呼叫之函式的呼叫端。 這表示將不會對做為 tail 呼叫目標的函式發出 [FunctionLeave2](functionleave2-function.md) 回呼。  
  
 函數傳回之後，參數的值無效， `func` `FunctionTailcall2` 因為該值可能會變更或終結。  
  
 `FunctionTailcall2`函數是回呼; 您必須加以執行。 實作為必須使用 `__declspec` (`naked`) 儲存類別屬性。  
  
 在呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。  
  
- 在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。  
  
 的執行 `FunctionTailcall2` 不應封鎖，因為它會延遲垃圾收集。 執行不應嘗試垃圾收集，因為堆疊可能不是處於垃圾收集的易記狀態。 如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionTailcall2` 。  
  
 此外，此函式 `FunctionTailcall2` 不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter2 函式](functionenter2-function.md)
- [FunctionLeave2 函式](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
