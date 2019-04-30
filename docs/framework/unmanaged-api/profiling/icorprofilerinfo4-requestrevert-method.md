---
title: ICorProfilerInfo4::RequestRevert 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92137e1a5b0923bc34745513715934c483616700
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000489"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert 方法
將指定函式的所有執行個體還原成其原始版本。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>參數  
 `cFunctions`  
 [in] 要還原的函式數目。  
  
 `moduleIds`  
 [in] 指定 (`module`, `methodDef`) 組的 `moduleId` 部分，這個部分可識別要還原的函式。  
  
 `methodIds`  
 [in] 指定 (`module`, `methodDef`) 組的 `methodId` 部分，這個部分可識別要還原的函式。  
  
 `status`  
 [out] HRESULT 的陣列 (列於本主題稍後的＜狀態 HRESULT＞一節)。 每個 HRESULT 會指出嘗試還原平行陣列 `moduleIds` 和 `methodIds` 中所指定的每個函式是成功或失敗。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|嘗試還原所有要求；不過，必須檢查傳回的狀態陣列，以判斷哪些函式成功還原。|  
|CORPROF_E_CALLBACK4_REQUIRED|分析工具必須實作[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)都必須支援這個呼叫的介面。|  
|CORPROF_E_REJIT_NOT_ENABLED|尚未啟用 JIT 重新編譯。 您必須使用，以啟用 JIT 重新編譯，在初始化期間[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定`COR_PRF_ENABLE_REJIT`旗標。|  
|E_INVALIDARG|`cFunctions` 為 0，或者 `moduleIds` 或 `methodIds` 為 `NULL`。|  
|E_OUTOFMEMORY|CLR 無法完成要求，因為記憶體不足。|  
  
## <a name="status-hresults"></a>狀態 HRESULT  
  
|狀態陣列 HRESULT|描述|  
|--------------------------|-----------------|  
|S_OK|已成功還原對應的函式。|  
|E_INVALIDARG|`moduleID` 或 `methodDef` 參數為 `NULL`。|  
|CORPROF_E_DATAINCOMPLETE|這個模組未完全載入，或正在進行卸載。|  
|CORPROF_E_MODULE_IS_DYNAMIC|已動態產生指定的模組 (例如透過 `Reflection.Emit`)， 因此不受這個方法的支援。|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|CLR 無法還原指定的函式，因為找不到對應的作用中重新編譯要求。 從未要求重新編譯或已還原函式。|  
|其他|作業系統會傳回在 CLR 的控制項外發生的失敗。 例如，如果變更記憶體分頁之存取保護的系統呼叫失敗，則會顯示作業系統錯誤。|  
  
## <a name="remarks"></a>備註  
 下次呼叫已還原的任何函式執行個體時，便會執行函式的原始版本。 如果函式已在執行中，則會結束執行正在執行的版本。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
