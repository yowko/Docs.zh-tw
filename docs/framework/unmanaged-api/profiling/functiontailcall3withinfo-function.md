---
title: FunctionTailcall3WithInfo 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4352d006c95a5b85341625220e6c7e62a86b482a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598762"
---
# <a name="functiontailcall3withinfo-function"></a>FunctionTailcall3WithInfo 函式
通知分析工具目前正在執行的函式即將執行結尾呼叫另一個函式，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionTailcall3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)擷取堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>參數  
 `functionIDOrClientID`  
 [in]目前正在執行時進行呼叫的結尾的函式的識別項。  
  
 `eltInfo`  
 [in] 代表特定堆疊框架之資訊的不透明控制代碼。 這個控制代碼傳遞到回呼期間，只是有效的。  
  
## <a name="remarks"></a>備註  
 `FunctionTailcall3WithInfo`回呼方法會通知分析工具，因為函式呼叫時，並允許使用分析工具[ICorProfilerInfo3::GetFunctionTailcall3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)檢查堆疊框架。 若要存取堆疊框架資訊，`COR_PRF_ENABLE_FRAME_INFO`旗標的設定。 可以使用分析工具[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件的旗標，然後使用[ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)註冊您此函式的實作。  
  
 `FunctionTailcall3WithInfo`函式是回呼; 您必須實作它。 的實作必須使用`__declspec(naked)`儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
- 結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionTailcall3WithInfo`不應封鎖，因為它將會延遲記憶體回收。 實作不應嘗試回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionTailcall3WithInfo`傳回。  
  
 此外，FunctionTailcall3WithInfo 函式必須不呼叫 managed 程式碼，或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
