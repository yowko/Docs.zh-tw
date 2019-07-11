---
title: FunctionTailcall3 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aec2304e00d5328fcf55adbf5521c08865c05c56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763299"
---
# <a name="functiontailcall3-function"></a>FunctionTailcall3 函式
通知分析工具目前正在執行的函式即將執行的另一個函式的 tail 呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a>參數  
 `functionOrRemappedID`  
 [in]目前正在執行時進行呼叫的結尾的函式的識別項。  
  
## <a name="remarks"></a>備註  
 `FunctionTailcall3`回呼函式會通知分析工具，為所呼叫的函式。 使用[ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)註冊您的實作，此函式。  
  
 `FunctionTailcall3`函式是回呼; 您必須實作它。 的實作必須使用`__declspec(naked)`儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
- 結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionTailcall3`不應封鎖，因為它將會延遲記憶體回收。 實作不應嘗試回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionTailcall3`傳回。  
  
 `FunctionTailcall3`函式不能呼叫 managed 程式碼或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
