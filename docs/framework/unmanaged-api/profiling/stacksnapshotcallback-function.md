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
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493977"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback 函式
提供程式碼剖析工具，其中包含每個 managed 框架的相關資訊，以及堆疊階段期間每次在堆疊上執行的非受控框架，這是由[ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法起始。  
  
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
 在`COR_PRF_FRAME_INFO`值，參考堆疊框架的相關資訊。 此值僅適用于在此回呼期間使用。  
  
 `contextSize`  
 在結構的大小 `CONTEXT` ，由參數所參考 `context` 。  
  
 `context`  
 在Win32 結構的指標 `CONTEXT` ，表示此框架的 CPU 狀態。  
  
 `context`只有在傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，參數才有效 `ICorProfilerInfo2::DoStackSnapshot` 。  
  
 `clientData`  
 在用戶端資料的指標，直接從傳遞 `ICorProfilerInfo2::DoStackSnapshot` 。  
  
## <a name="remarks"></a>備註  
 函式是由分析工具寫入器所 `StackSnapshotCallback` 執行。 您必須限制在中完成之工作的複雜度 `StackSnapshotCallback` 。 例如，當 `ICorProfilerInfo2::DoStackSnapshot` 以非同步方式使用時，目標執行緒可能會持有鎖定。 如果內的程式碼 `StackSnapshotCallback` 需要相同的鎖定，可能會控制發生鎖死。  
  
 `ICorProfilerInfo2::DoStackSnapshot`方法會 `StackSnapshotCallback` 針對每個 managed 框架呼叫函式一次，或每次執行未受管理的框架。 如果 `StackSnapshotCallback` 針對非受控框架的執行呼叫，分析工具可能會使用暫存器內容（由參數所參考 `context` ）來執行自己的非受控堆疊引導。 在此情況下，Win32 `CONTEXT` 結構代表執行非受控框架內最近推送之框架的 CPU 狀態。 雖然 Win32 `CONTEXT` 結構包含所有暫存器的值，但您應該只依賴堆疊指標暫存器、框架指標暫存器、指令指標暫存器，以及非靜態（也就是保留的）整數暫存器的值。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [DoStackSnapshot 方法](icorprofilerinfo2-dostacksnapshot-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
