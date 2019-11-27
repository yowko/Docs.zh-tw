---
title: StackSnapshotCallback 函式
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427074"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback 函式
提供程式碼剖析工具，其中包含每個 managed 框架的相關資訊，以及堆疊階段期間每次在堆疊上執行的非受控框架，這是由[ICorProfilerInfo2：:D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法起始。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a>參數  
 `funcId`  
 在如果此值為零，則此回呼適用于執行非受控框架;否則，它是 managed 函式的識別碼，而此回呼適用于受控框架。  
  
 `ip`  
 在框架中機器碼指令指標的值。  
  
 `frameInfo`  
 在參考有關堆疊框架之資訊的 `COR_PRF_FRAME_INFO` 值。 此值僅適用于在此回呼期間使用。  
  
 `contextSize`  
 在`context` 參數所參考的 `CONTEXT` 結構大小。  
  
 `context`  
 在Win32 `CONTEXT` 結構的指標，表示此框架的 CPU 狀態。  
  
 只有在 `ICorProfilerInfo2::DoStackSnapshot`中傳遞 COR_PRF_SNAPSHOT_CONTEXT 旗標時，`context` 參數才有效。  
  
 `clientData`  
 在用戶端資料的指標，直接從 `ICorProfilerInfo2::DoStackSnapshot`傳遞。  
  
## <a name="remarks"></a>備註  
 `StackSnapshotCallback` 函式是由 profiler 寫入器所執行。 您必須限制在 `StackSnapshotCallback`中完成之工作的複雜度。 例如，以非同步方式使用 `ICorProfilerInfo2::DoStackSnapshot` 時，目標執行緒可能會持有鎖定。 如果 `StackSnapshotCallback` 內的程式碼需要相同的鎖定，可能會控制發生鎖死。  
  
 `ICorProfilerInfo2::DoStackSnapshot` 方法會針對每個 managed 框架呼叫 `StackSnapshotCallback` 函式一次，或每次執行未受管理的框架。 如果在執行非受控框架時呼叫 `StackSnapshotCallback`，分析工具可能會使用暫存器內容（由 `context` 參數所參考）來執行自己的非受控堆疊逐步解說。 在此情況下，Win32 `CONTEXT` 結構代表執行非受控框架內最近推送之框架的 CPU 狀態。 雖然 Win32 `CONTEXT` 結構包含所有暫存器的值，但您應該只依賴堆疊指標暫存器、框架指標暫存器、指令指標暫存器，以及非靜態（也就是保留的）整數暫存器的值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [DoStackSnapshot 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
