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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 825da3a09f8b8013ffecaedfee0dce2362c8a7b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227804"
---
# <a name="functionenter2-function"></a>FunctionEnter2 函式
控制項已傳遞至函式，並提供資訊堆疊框架和函式的引數，請通知分析工具。 這個函數會取代[FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>參數  
 `funcId`  
 [in]控制權會傳遞函式的識別碼。  
  
 `clientData`  
 [in]重新對應的函式識別項，使用先前指定的程式碼剖析工具[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式。  
  
 `func`  
 [in]A`COR_PRF_FRAME_INFO`指向堆疊框架的相關資訊的值。  
  
 分析工具應該將這視為不透明的控制代碼可傳遞給在執行引擎[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。  
  
 `argumentInfo`  
 [in]指標[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)記憶體的函式的引數中指定位置的結構。  
  
 若要存取引數的詳細資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`旗標必須設定。 可以使用分析工具[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。  
  
## <a name="remarks"></a>備註  
 值`func`並`argumentInfo`參數都不是有效之後`FunctionEnter2`函式會傳回，因為可能會變更的值，或被終結。  
  
 `FunctionEnter2`函式是回呼; 您必須實作它。 的實作必須使用`__declspec`(`naked`) 儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
-   項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
-   結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionEnter2`應該不會封鎖，因為它將會延遲記憶體回收。 實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionEnter2`傳回。  
  
 此外，`FunctionEnter2`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
