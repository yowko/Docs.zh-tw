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
ms.openlocfilehash: be144ac8250adf803ddb1f20ea55be09cb3e81d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687384"
---
# <a name="functionenter-function"></a>FunctionEnter 函式
通知分析工具的控制項傳遞至函式。  
  
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
 [in]控制權會傳遞函式的識別碼。  
  
## <a name="remarks"></a>備註  
 `FunctionEnter`函式是回呼; 您必須實作它。 的實作必須使用`__declspec`(`naked`) 儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
-   項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
-   結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionEnter`應該不會封鎖，因為它將會延遲記憶體回收。 實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionEnter`傳回。  
  
 此外，`FunctionEnter`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1, 1.0  
  
## <a name="see-also"></a>另請參閱
- [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
