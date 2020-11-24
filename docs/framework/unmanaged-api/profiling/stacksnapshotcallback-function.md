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
ms.openlocfilehash: 2d6ca18ce48f69d8c94b465efac2b9fe0e10f070
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685301"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback 函式

提供分析工具，其中包含每個 managed 框架的相關資訊，以及堆疊逐步解說（由 [ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) 方法所起始）堆疊中每次執行的非受控框架。  
  
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
 在框架中原生程式碼指令指標的值。  
  
 `frameInfo`  
 在 `COR_PRF_FRAME_INFO` 值，參考堆疊框架的相關資訊。 此值僅適用于在此回呼期間使用。  
  
 `contextSize`  
 在 `CONTEXT` 參數所參考之結構的大小 `context` 。  
  
 `context`  
 在Win32 結構的指標 `CONTEXT` ，表示此框架的 CPU 狀態。  
  
 `context`只有在傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，參數才有效 `ICorProfilerInfo2::DoStackSnapshot` 。  
  
 `clientData`  
 在用戶端資料的指標，從直接傳遞至 `ICorProfilerInfo2::DoStackSnapshot` 。  
  
## <a name="remarks"></a>備註  

 函式是由分析工具寫入器所 `StackSnapshotCallback` 執行。 您必須限制在中完成工作的複雜度 `StackSnapshotCallback` 。 例如， `ICorProfilerInfo2::DoStackSnapshot` 以非同步方式使用時，目標執行緒可能會持有鎖定。 如果內的程式碼 `StackSnapshotCallback` 需要相同的鎖定，可能會災難接踵而至鎖死。  
  
 `ICorProfilerInfo2::DoStackSnapshot`方法會 `StackSnapshotCallback` 針對每個 managed 框架呼叫函式一次，或針對每次執行非受控框架呼叫一次函數。 如果 `StackSnapshotCallback` 呼叫以執行非受控框架，分析工具可能會使用參數所參考的登錄內容 (`context`) 來執行它自己的非受控堆疊逐步解說。 在此情況下，Win32 `CONTEXT` 結構代表未受管理的框架執行內最近推入框架的 CPU 狀態。 雖然 Win32 `CONTEXT` 結構包含所有暫存器的值，但您應該只依賴堆疊指標暫存器、框架指標暫存器、指令指標暫存器的值，以及靜態 (，也就是保留) 整數暫存器。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [DoStackSnapshot 方法](icorprofilerinfo2-dostacksnapshot-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
