---
title: FunctionLeave3WithInfo 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: f7a945fb7ef10f995be2d779a88b98bbce2fdfb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866839"
---
# <a name="functionleave3withinfo-function"></a>FunctionLeave3WithInfo 函式
通知分析工具，控制項是從函式傳回，並提供可傳遞至[ICorProfilerInfo3：： GetFunctionLeave3Info 方法](icorprofilerinfo3-getfunctionleave3info-method.md)的控制碼，以取得堆疊框架和傳回值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>參數

- `functionIDOrClientID`

  \[in] 從其傳回控制項的函式識別碼。

- `eltInfo`

  \[in]）不透明的控制碼，代表指定之堆疊框架的相關資訊。 這個控制碼只有在傳遞它的回呼期間才有效。

## <a name="remarks"></a>備註  
 `FunctionLeave3WithInfo` 回呼方法會在呼叫函式時通知分析工具，並允許分析工具使用[ICorProfilerInfo3：： GetFunctionLeave3Info 方法](icorprofilerinfo3-getfunctionleave3info-method.md)來檢查傳回值。 若要存取傳回值資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_RETVAL` 旗標。 分析工具可以使用[ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)來設定事件旗標，然後使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)來註冊此函式的實作為。  
  
 `FunctionLeave3WithInfo` 函數是回呼;您必須加以執行。 此執行必須使用 `__declspec(naked)` 儲存類別屬性。  
  
 在呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。  
  
- 結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。  
  
 `FunctionLeave3WithInfo` 的執行不應該封鎖，因為它會延遲垃圾收集。 執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。 如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionLeave3WithInfo` 傳回為止。  
  
 `FunctionLeave3WithInfo` 函式不得呼叫 managed 程式碼，或以任何方式造成 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
