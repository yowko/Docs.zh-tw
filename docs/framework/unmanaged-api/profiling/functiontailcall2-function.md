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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e10b1a77586a09f8f5f7a59e811953fbede8773
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586887"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 函式
通知分析工具，目前正在執行的函式執行至另一個函式的 tail 呼叫，並提供有關堆疊框架資訊。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>參數  
 `funcId`  
 [in]目前正在執行時進行呼叫的結尾的函式的識別項。  
  
 `clientData`  
 [in]重新對應的函式識別項，透過先前指定的程式碼剖析工具[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)，進行呼叫的結尾是目前執行函式。  
  
 `func`  
 [in]A`COR_PRF_FRAME_INFO`指向堆疊框架的相關資訊的值。  
  
 分析工具應該將這視為不透明的控制代碼可傳遞給在執行引擎[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。  
  
## <a name="remarks"></a>備註  
 Tail 呼叫的目標函式會使用目前的堆疊框架，並會直接傳回呼叫端函式進行呼叫的結尾。 這表示[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)回呼不會發出為目標的 tail 呼叫的函式。  
  
 值`func`參數不是有效之後`FunctionTailcall2`函式會傳回，因為可能會變更的值，或被終結。  
  
 `FunctionTailcall2`函式是回呼; 您必須實作它。 的實作必須使用`__declspec`(`naked`) 儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
- 結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionTailcall2`應該不會封鎖，因為它將會延遲記憶體回收。 實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionTailcall2`傳回。  
  
 此外，`FunctionTailcall2`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
