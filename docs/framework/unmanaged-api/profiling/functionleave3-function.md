---
title: FunctionLeave3 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14f4f16a73c50de2d23804f77bca180f4e9827b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="functionleave3-function"></a>FunctionLeave3 函式
通知分析工具會從函式傳回控制項。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a>參數  
 `functionOrRemappedID`  
 [in]控制項會傳回函式的識別項。  
  
## <a name="remarks"></a>備註  
 `FunctionLeave3`回呼函式會通知分析工具函式呼叫，但不支援傳回值檢查。 使用[icorprofilerinfo3:: Setenterleavefunctionhooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)註冊您的實作，此函式。  
  
 `FunctionLeave3`函式是回呼，您必須實作它。 實作必須使用`__declspec(naked)`儲存類別屬性。  
  
 執行引擎不會呼叫此函數之前儲存任何暫存器。  
  
-   進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。  
  
-   結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。  
  
 實作`FunctionLeave3`不應該封鎖，因為它將會延遲記憶體回收。 實作不應嘗試回收，因為堆疊可能不在記憶體回收方便集合的狀態。 如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionLeave3`傳回。  
  
 `FunctionLeave3`函式不能呼叫 managed 程式碼或以任何方式導致受管理的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
