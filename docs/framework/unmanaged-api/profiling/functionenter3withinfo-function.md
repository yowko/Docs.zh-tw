---
title: FunctionEnter3WithInfo 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: b511c5abe10ab6c0ec856a5686b082132ed4a5d9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722855"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo 函式

通知分析工具將控制權傳遞至函式，並提供可傳遞至 [ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md) 的控制碼，以取得堆疊框架和函式引數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>參數

- `functionIDOrClientID`

  \[in] 要傳遞控制項的函式識別碼。

- `eltInfo`

  \[in] 不透明的控制碼，表示指定之堆疊框架的相關資訊。 這個控制碼只有在傳遞的回呼期間有效。

## <a name="remarks"></a>備註  

 `FunctionEnter3WithInfo`回呼方法會在呼叫函式時通知分析工具，並讓 profiler 使用[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md)來檢查引數值。 若要存取引數資訊，必須 `COR_PRF_ENABLE_FUNCTION_ARGS` 設定旗標。 分析工具可以使用 [ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md) 來設定事件旗標，然後使用 [ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) 來註冊此函式的實作為。  
  
 `FunctionEnter3WithInfo`函數是回呼; 您必須加以執行。 實作為必須使用 `__declspec(naked)` 儲存類別屬性。  
  
 在呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。  
  
- 在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。  
  
 的執行 `FunctionEnter3WithInfo` 不應封鎖，因為它會延遲垃圾收集。 因為堆疊可能不是處於垃圾收集的狀態，所以不應該嘗試執行垃圾收集。 如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionEnter3WithInfo` 。  
  
 函式 `FunctionEnter3WithInfo` 不得以任何方式呼叫 managed 程式碼，或導致受控記憶體配置。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
