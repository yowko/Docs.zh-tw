---
title: ICorProfilerInfo2::DoStackSnapshot 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
ms.openlocfilehash: 10cc9dedfa34cd5235df721d7010bbd928fbc3ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727233"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot 方法

引導堆疊上指定執行緒的 managed 框架，並透過回呼將資訊傳送至分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>參數  

 `thread`  
 在目標執行緒的識別碼。  
  
 傳遞 null 時 `thread` ，會產生目前線程的快照。 如果傳遞的是 `ThreadID` 不同的執行緒，則 common language runtime (CLR) 會暫停該執行緒、執行快照集，然後繼續進行。  
  
 `callback`  
 在 [StackSnapshotCallback](stacksnapshotcallback-function.md) 方法的執行指標，由 CLR 呼叫，以提供分析工具每個 managed 框架的資訊，以及每次執行非受控框架的相關資訊。  
  
 `StackSnapshotCallback`方法是由分析工具寫入器所執行。  
  
 `infoFlags`  
 在 [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) 列舉值，這個值會指定要針對每個框架傳回的資料量 `StackSnapshotCallback` 。  
  
 `clientData`  
 在用戶端資料的指標，會直接傳遞至 `StackSnapshotCallback` 回呼函數。  
  
 `context`  
 在Win32 結構的指標 `CONTEXT` ，用來植入堆疊的逐步解說。 Win32 `CONTEXT` 結構包含 cpu 暫存器的值，並代表特定時間點的 cpu 狀態。  
  
 如果堆疊的頂端是未受管理的 helper 程式碼，則種子可協助 CLR 判斷開始堆疊的位置：否則會忽略種子。 必須提供種子給非同步逐步解說。 如果您執行的是同步的逐步解說，則不需要任何種子。  
  
 `context`只有在參數中傳遞 COR_PRF_SNAPSHOT_CONTEXT 旗標時，參數才有效 `infoFlags` 。  
  
 `contextSize`  
 在 `CONTEXT` 參數所參考之結構的大小 `context` 。  
  
## <a name="remarks"></a>備註  

 傳遞 null 以 `thread` 產生目前線程的快照集。 只有在目標執行緒暫止時，才可以建立其他執行緒的快照集。  
  
 當分析工具想要引導堆疊時，它會呼叫 `DoStackSnapshot` 。 在 CLR 從該呼叫傳回之前，會呼叫您 `StackSnapshotCallback` 數次，每個 managed 框架 (或執行堆疊上) 非受控框架。 當遇到非受控框架時，您必須自行引導。  
  
 堆疊的進行順序，就是將框架推送至堆疊的方式：分葉 (最後推入) 框架，主要 (第一次推送) 框架。  
  
 如需如何設計程式碼剖析工具以逐步執行 managed 堆疊的詳細資訊，請參閱 [.NET Framework 2.0：基本版和更高範圍中的 Profiler 堆疊逐步](/previous-versions/dotnet/articles/bb264782(v=msdn.10))解說。  
  
 堆疊逐步解說可以是同步或非同步，如下列各節所述。  
  
## <a name="synchronous-stack-walk"></a>同步堆疊逐步解說  

 同步堆疊的逐步解說牽涉到目前線程的堆疊，以回應回呼。 它不需要植入或暫停。  
  
 當您呼叫其中一個分析工具的 ICorProfilerCallback (或[ICorProfilerCallback2](icorprofilercallback2-interface.md)) 方法時，您會呼叫以逐步執行目前線程的堆疊，以回應 CLR 呼叫其中一個 Profiler 的[ICorProfilerCallback](icorprofilercallback-interface.md) `DoStackSnapshot` 。 當您想要查看堆疊在 [ICorProfilerCallback：： ObjectAllocated](icorprofilercallback-objectallocated-method.md)之類的通知時，這會很有用。 您只需要在 `DoStackSnapshot` 方法中呼叫 `ICorProfilerCallback` ， `context` 並在和參數中傳遞 null `thread` 。  
  
## <a name="asynchronous-stack-walk"></a>非同步堆疊逐步解說  

 非同步堆疊的逐步解說需要離開不同執行緒的堆疊，或將目前線程的堆疊移至目前線程的堆疊，而不是回應回呼，但藉由劫持目前線程的指令指標。 如果堆疊的頂端是非受控程式碼，而不是平台叫用的一部分 (PInvoke) 或 COM 呼叫，但是 CLR 本身的 helper 程式碼，則非同步逐步解說需要種子。 例如，執行即時 (JIT) 編譯或垃圾收集的程式碼是 helper 程式碼。  
  
 您可以直接暫停目標執行緒，並自行進行堆疊來取得種子，直到您找到最上層的 managed 框架為止。 在目標執行緒暫止之後，取得目標執行緒的目前註冊內容。 接下來，藉由呼叫 [ICorProfilerInfo：： GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) ，判斷註冊內容是否指向非受控程式碼，如果它傳回 `FunctionID` 等於零，則框架為非受控碼。 現在，請先進入堆疊，直到到達第一個 managed 框架，然後根據該框架的註冊內容來計算種子內容。  
  
 `DoStackSnapshot`使用您的種子內容來呼叫，以開始非同步堆疊的逐步解說。 如果您未提供種子， `DoStackSnapshot` 可能會略過堆疊頂端的 managed 框架，因此會提供您不完整的堆疊逐步解說。 如果您提供種子，它必須指向 JIT 編譯或原生映射產生器 ( # A0) 產生的程式碼;否則，會傳回 `DoStackSnapshot` 失敗碼 CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。  
  
 除非您遵循下列指導方針，否則非同步堆疊的逐步解說很容易就會造成鎖死或存取違規：  
  
- 當您直接暫停執行緒時，請記住，只有從未執行 managed 程式碼的執行緒才能暫停另一個執行緒。  
  
- 一律在 [ICorProfilerCallback：： ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) 回呼中封鎖，直到該執行緒的堆疊逐步完成為止。  
  
- 當分析工具呼叫可觸發垃圾收集的 CLR 函式時，請勿保留鎖定。 也就是，如果主控執行緒可能進行呼叫來觸發垃圾收集，就不會保留鎖定。  
  
 如果您從分析工具所建立的執行緒呼叫， `DoStackSnapshot` 讓您可以逐步解說不同的目標執行緒，也會有鎖死的風險。 當您第一次建立的執行緒進入特定 `ICorProfilerInfo*` 方法 (包括 `DoStackSnapshot`) 時，clr 會在該執行緒上執行每個執行緒的 clr 特定初始化。 如果您的分析工具已暫止您嘗試進行堆疊的目標執行緒，而且如果該目標執行緒擁有執行此每個執行緒初始化所需的鎖定，就會發生鎖死。 若要避免這個鎖死，請從分析工具建立的執行緒進行初始呼叫 `DoStackSnapshot` ，以逐步執行個別的目標執行緒，但不要先暫停目標執行緒。 這個初始呼叫可確保每個執行緒的初始化都能在沒有鎖死的情況下完成。 如果 `DoStackSnapshot` 成功並報告至少一個框架，則在該時間點之後，該分析工具建立的執行緒將可安全地暫停任何目標執行緒，並呼叫 `DoStackSnapshot` 以取得該目標執行緒的堆疊。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
