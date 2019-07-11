---
title: FunctionEnter3WithInfo 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf16563e6d5fef3a743e802166173004a857dd0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745828"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo 函式
通知分析工具的控制項傳遞至函式，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionEnter3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)來擷取堆疊框架和函式引數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>參數  
 `functionIDOrClientID`  
 [in]控制權會傳遞函式的識別碼。  
  
 `eltInfo`  
 [in] 代表特定堆疊框架之資訊的不透明控制代碼。 這個控制代碼傳遞到回呼期間，只是有效的。  
  
## <a name="remarks"></a>備註  
 `FunctionEnter3WithInfo`函式呼叫時，以及讓分析工具使用，回呼方法會通知分析工具[ICorProfilerInfo3::GetFunctionEnter3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)檢查引數的值。 若要存取引數的詳細資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`旗標的設定。 可以使用分析工具[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件的旗標，然後使用[ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)註冊您此函式的實作。  
  
 `FunctionEnter3WithInfo`函式是回呼; 您必須實作它。 的實作必須使用`__declspec(naked)`儲存類別屬性。  
  
 呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。  
  
- 結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。  
  
 實作`FunctionEnter3WithInfo`不應封鎖，因為它將會延遲記憶體回收。 實作不應嘗試回收，因為堆疊可能無法在記憶體回收方便集合的狀態。 如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionEnter3WithInfo`傳回。  
  
 `FunctionEnter3WithInfo`函式不能呼叫 managed 程式碼或以任何方式造成 managed 的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
