---
title: ICorProfilerInfo4::RequestReJIT 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be7184e07815ebe222b8ff8736c26fd3879c8777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT 方法
要求指定函式的所有執行個體進行 JIT 重新編譯。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a>參數  
 `cFunctions`  
 [in] 要重新編譯的函式數目。  
  
 `moduleIds`  
 [in] 指定 (`module`, `methodDef`) 組的 `moduleId` 部分，這個部分可識別所要重新編譯的函式。  
  
 `methodIds`  
 [in] 指定 (`module`, `methodDef`) 組的 `methodId` 部分，這個部分可識別所要重新編譯的函式。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已嘗試將所有方法標示為要進行 JIT 重新編譯。 分析工具必須實作[icorprofilercallback4:: Rejiterror](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)方法來判斷哪些方法已成功標示為進行 JIT 重新編譯。|  
|CORPROF_E_CALLBACK4_REQUIRED|分析工具必須實作[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)必須支援這個呼叫的介面。|  
|CORPROF_E_REJIT_NOT_ENABLED|尚未啟用 JIT 重新編譯。 您必須使用，以啟用 JIT 重新編譯期間初始化[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法，以設定`COR_PRF_ENABLE_REJIT`旗標。|  
|E_INVALIDARG|`cFunctions` 為 0，或者 `moduleIds` 或 `methodIds` 為 `NULL`。|  
|||  
|E_OUTOFMEMORY|CLR 無法完成要求，因為記憶體不足。|  
  
## <a name="remarks"></a>備註  
 呼叫 `RequestReJIT`，讓執行階段重新編譯所指定的一組函式。 然後可以使用程式碼分析工具[ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)介面，以調整重新編譯函式時所產生的程式碼。 這不會影響目前正在執行的函式，只會影響未來的函式叫用。 如果所指定的任何函式先前已進行過 JIT 重新編譯，要求重新編譯就等於還原並重新編譯函式。 為了保留可反轉性，當 JIT 編譯器編譯函式的原始版本時，只會考慮其被呼叫端的原始版本來進行內嵌決策。 當 JIT 編譯器重新編譯函式時，它會考慮其被呼叫端的目前版本 (已重新編譯或原始) 來進行內嵌。  
  
 分析工具通常會呼叫 `RequestReJIT`，以回應要求分析工具檢測一或多個方法的使用者輸入。 `RequestReJIT` 通常會暫停執行階段，以執行某些工作，而且可能會觸發記憶體回收。 因此，分析工具應該從其先前建立的執行緒來呼叫 `RequestReJIT`，而不是從目前正在執行分析工具回呼的 CLR 建立的執行緒。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
