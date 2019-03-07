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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9985b5a5547097c0474eb3a5797388d1444083e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471581"
---
# <a name="functionleave2-function"></a>FunctionLeave2 函式
函式傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊，請通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>參數  
 `funcId`  
 [in]函式傳回的識別項。  
  
 `clientData`  
 [in]重新對應的函式識別項，透過先前指定的程式碼剖析工具[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式。  
  
 `func`  
 [in]A`COR_PRF_FRAME_INFO`指向堆疊框架的相關資訊的值。  
  
 分析工具應該將這視為不透明的控制代碼可傳遞給在執行引擎[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。  
  
 `retvalRange`  
 [in]指標[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構，指定函式的傳回值的記憶體位置。  
  
 若要存取傳回值的詳細資訊，`COR_PRF_ENABLE_FUNCTION_RETVAL`旗標必須設定。 可以使用分析工具[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。  
  
## <a name="remarks"></a>備註  
 值`func`並`retvalRange`參數都不是有效之後`FunctionLeave2`函式會傳回，因為可能會變更的值，或被終結。  
  
 `FunctionLeave2`函式是回呼; 您必須實作它。 的實作必須使用`__declspec`(`naked`) 儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
-   項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
-   結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionLeave2`應該不會封鎖，因為它將會延遲記憶體回收。 實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionLeave2`傳回。  
  
 此外，`FunctionLeave2`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
