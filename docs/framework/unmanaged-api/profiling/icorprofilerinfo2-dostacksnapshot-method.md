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
ms.openlocfilehash: 5d90f414a945d346ca7721745ea7d86cb24a085c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936861"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot 方法
針對指定的執行緒，引導堆疊上的 managed 框架，並透過回呼將資訊傳送至分析工具。  
  
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
  
 在 `thread` 中傳遞 null 會產生目前線程的快照集。 如果傳遞了不同執行緒的 `ThreadID`，common language runtime （CLR）就會暫停該執行緒、執行快照集，然後繼續進行。  
  
 `callback`  
 在[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)方法的執行指標，由 CLR 呼叫，以提供分析工具有關每個 managed 框架的資訊，以及每次執行未受管理的框架。  
  
 `StackSnapshotCallback` 方法是由分析工具寫入器所執行。  
  
 `infoFlags`  
 在[COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)列舉的值，指定 `StackSnapshotCallback`的每個框架所要傳回的資料量。  
  
 `clientData`  
 在用戶端資料的指標，會直接傳遞至 `StackSnapshotCallback` 回呼函數。  
  
 `context`  
 在Win32 `CONTEXT` 結構的指標，用來植入堆疊的逐步解說。 Win32 `CONTEXT` 結構包含 CPU 暫存器的值，並代表特定時間點的 CPU 狀態。  
  
 如果堆疊的頂端是未受管理的 helper 程式碼，則種子可協助 CLR 判斷堆疊的開始位置：否則，會忽略種子。 必須提供種子給非同步逐步解說。 如果您要執行同步的逐步解說，則不需要任何種子。  
  
 只有在 `infoFlags` 參數中傳遞 COR_PRF_SNAPSHOT_CONTEXT 旗標時，`context` 參數才有效。  
  
 `contextSize`  
 在`context` 參數所參考的 `CONTEXT` 結構大小。  
  
## <a name="remarks"></a>備註  
 傳遞 null 做為 `thread` 會產生目前線程的快照集。 只有在目標執行緒于當時暫停時，才可以在其他執行緒中取用快照集。  
  
 當 profiler 想要逐步進行堆疊時，它會呼叫 `DoStackSnapshot`。 在 CLR 從該呼叫傳回之前，會呼叫您的 `StackSnapshotCallback` 數次，一次用於堆疊上的每個 managed 框架（或執行非受控框架）。 遇到未受管理的框架時，您必須自行進行引導。  
  
 堆疊的進入順序就是將畫面格推送至堆疊的方式反向：分葉（最後推送）框架 first、主要（第一次推送）框架最後。  
  
 如需如何編寫分析工具來逐步執行 managed 堆疊的詳細資訊，請參閱[.NET Framework 2.0：基本概念和其他專案中的 Profiler 堆疊流覽](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10))。  
  
 堆疊演練可以是同步或非同步，如下列各節所述。  
  
## <a name="synchronous-stack-walk"></a>同步堆疊逐步解說  
 同步堆疊的逐步解說牽涉到目前線程的堆疊，以回應回呼。 它不需要植入或暫停。  
  
 您會在回應呼叫其中一個分析工具的[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) （或[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)）方法的 CLR 時進行同步呼叫，您會呼叫 `DoStackSnapshot` 來逐步執行目前線程的堆疊。 當您想要查看堆疊在[ICorProfilerCallback：： ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)等通知時的樣子時，這會很有用。 您只需從 `ICorProfilerCallback` 方法內呼叫 `DoStackSnapshot`，並在 `context` 和 `thread` 參數中傳遞 null。  
  
## <a name="asynchronous-stack-walk"></a>非同步堆疊逐步解說  
 非同步堆疊的逐步解說牽涉到不同執行緒的堆疊，或流覽目前線程的堆疊，而不是回應回呼，但藉由劫持目前線程的指令指標。 如果堆疊的頂端不是平台叫用（PInvoke）或 COM 呼叫的非受控程式碼，而是 CLR 本身的 helper 程式碼，非同步逐步解說就需要種子。 例如，執行即時（JIT）編譯或垃圾收集的程式碼是 helper 程式碼。  
  
 您可以直接暫止目標執行緒並自行流覽其堆疊，以取得種子，直到您找到最上層的受控框架為止。 在目標執行緒暫停之後，取得目標執行緒目前的暫存器內容。 接下來，判斷暫存器內容是否藉由呼叫[ICorProfilerInfo：： GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)來指向非受控程式碼-如果它傳回的 `FunctionID` 等於零，則此框架為非受控碼。 現在，請將堆疊引導到第一個受管理的框架，然後根據該框架的註冊內容來計算種子內容。  
  
 使用您的種子內容呼叫 `DoStackSnapshot`，以開始非同步堆疊的逐步解說。 如果您未提供種子，`DoStackSnapshot` 可能會略過堆疊頂端的受控框架，因此，會提供您不完整的堆疊逐步解說。 如果您提供種子，它必須指向 JIT 編譯或原生映射產生器（Ngen.exe）產生的程式碼;否則，`DoStackSnapshot` 會傳回失敗碼，CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。  
  
 除非您遵循下列指導方針，否則非同步堆疊逐步解說很容易就會導致鎖死或存取違規：  
  
- 當您直接暫止執行緒時，請記住，只有從未執行過 managed 程式碼的執行緒才能暫停另一個執行緒。  
  
- 一律在[ICorProfilerCallback：： ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)回呼中封鎖，直到執行緒的堆疊演練完成為止。  
  
- 當您的分析工具呼叫可觸發垃圾收集的 CLR 函數時，請勿持有鎖定。 也就是說，如果擁有的執行緒可能會進行呼叫來觸發垃圾收集，請勿持有鎖定。  
  
 如果您從分析工具已建立的執行緒呼叫 `DoStackSnapshot`，讓您可以逐步解說個別目標執行緒的堆疊，也會有鎖死的風險。 第一次建立的執行緒進入特定 `ICorProfilerInfo*` 方法（包括 `DoStackSnapshot`）時，CLR 會在該執行緒上執行每個執行緒的 CLR 特定初始化。 如果您的分析工具已暫止您嘗試進行之堆疊的目標執行緒，而且該目標執行緒發生執行此每個執行緒初始化所需的鎖定，就會發生鎖死。 若要避免這個鎖死，請初始呼叫分析工具建立的執行緒中的 `DoStackSnapshot`，以引導個別的目標執行緒，但不要先暫停目標執行緒。 這個初始呼叫可確保每個執行緒的初始化都可以在沒有鎖死的情況下完成。 如果 `DoStackSnapshot` 成功並報告至少一個框架，在該時間點之後，就可以安全地讓分析工具建立的執行緒暫停任何目標執行緒，並呼叫 `DoStackSnapshot` 以引導該目標執行緒的堆疊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
