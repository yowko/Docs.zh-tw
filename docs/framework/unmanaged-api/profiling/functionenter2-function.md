---
title: "FunctionEnter2 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter2
helpviewer_keywords: FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0aa1d98021dcbfc38721d7f30ad305065dced605
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter2-function"></a>FunctionEnter2 函式
控制項傳遞至函式，並提供堆疊的相關資訊框架和函式的引數，請通知分析工具。 這個函數會取代[FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `funcId`  
 [in]控制權會傳遞函式的識別項。  
  
 `clientData`  
 [in]重新對應的函式識別項，利用先前指定的程式碼剖析工具[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式。  
  
 `func`  
 [in]A`COR_PRF_FRAME_INFO`指向堆疊框架的相關資訊的值。  
  
 程式碼剖析工具應該將此視為不透明控制代碼可傳遞回執行引擎中[icorprofilerinfo2:: Getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。  
  
 `argumentInfo`  
 [in]指標[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)結構，在記憶體中的函式的引數指定的位置。  
  
 若要存取引數的詳細資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`旗標必須設定。 分析工具可以使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。  
  
## <a name="remarks"></a>備註  
 值`func`和`argumentInfo`參數都不是有效之後`FunctionEnter2`函式傳回，因為可能會變更的值，或被終結。  
  
 `FunctionEnter2`函式是回呼，您必須實作它。 實作必須使用`__declspec`(`naked`) 儲存類別屬性。  
  
 執行引擎不會呼叫此函數之前儲存任何暫存器。  
  
-   進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。  
  
-   結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。  
  
 實作`FunctionEnter2`不應該封鎖，因為它將會延遲記憶體回收。 實作不應嘗試在記憶體回收，因為堆疊可能不在記憶體回收方便集合的狀態。 如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionEnter2`傳回。  
  
 此外，`FunctionEnter2`函式不可以呼叫至 managed 程式碼或任何方式發生原因的 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
