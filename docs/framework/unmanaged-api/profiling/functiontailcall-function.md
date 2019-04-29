---
title: FunctionTailcall 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 656f2498c7dd9ba165ab6759d8ca3b26e0d7c93f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598775"
---
# <a name="functiontailcall-function"></a>FunctionTailcall 函式
通知分析工具目前正在執行的函式即將執行的另一個函式的 tail 呼叫。  
  
> [!NOTE]
>  `FunctionTailcall`函式在.NET Framework 2.0 版中已被取代。 它會繼續運作，但會對效能帶來負面影響。 使用[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>參數  
 `funcID`  
 [in]目前正在執行時進行呼叫的結尾的函式的識別項。  
  
## <a name="remarks"></a>備註  
 Tail 呼叫的目標函式會使用目前的堆疊框架，並會直接傳回呼叫端函式進行呼叫的結尾。 這表示[FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)回呼不會發出為目標的 tail 呼叫的函式。  
  
 `FunctionTailcall`函式是回呼; 您必須實作它。 的實作必須使用`__declspec`(`naked`) 儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
- 結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionTailcall`應該不會封鎖，因為它將會延遲記憶體回收。 實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionTailcall`傳回。  
  
 此外，`FunctionTailcall`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** 1.1, 1.0  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
