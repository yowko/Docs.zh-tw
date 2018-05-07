---
title: FunctionEnter 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77de59de8fcf3797237245ce42c7f0eaa96d3d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="functionenter-function"></a>FunctionEnter 函式
通知分析工具控制會傳遞至函數。  
  
> [!NOTE]
>  `FunctionEnter`函式已被取代，在.NET Framework 2.0 版中，並使用它將會產生對效能帶來負面影響。 使用[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `funcID`  
 [in]控制權會傳遞函式的識別項。  
  
## <a name="remarks"></a>備註  
 `FunctionEnter`函式是回呼，您必須實作它。 實作必須使用`__declspec`(`naked`) 儲存類別屬性。  
  
 執行引擎不會呼叫此函數之前儲存任何暫存器。  
  
-   進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。  
  
-   結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。  
  
 實作`FunctionEnter`不應該封鎖，因為它將會延遲記憶體回收。 實作不應嘗試在記憶體回收，因為堆疊可能不在記憶體回收方便集合的狀態。 如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionEnter`傳回。  
  
 此外，`FunctionEnter`函式不可以呼叫至 managed 程式碼或任何方式發生原因的 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1、 1.0  
  
## <a name="see-also"></a>另請參閱  
 [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
