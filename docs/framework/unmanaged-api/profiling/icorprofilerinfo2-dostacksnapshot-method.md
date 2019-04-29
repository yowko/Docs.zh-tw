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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ef215253ca02048a5a3fc2c7c682823233929f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779811"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot 方法
引導指定的執行緒的堆疊上的 managed 的框架，並將資訊傳送到透過回呼程式碼剖析工具。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]目標執行緒識別碼。  
  
 傳遞 null`thread`會產生目前執行緒的快照集。 如果`ThreadID`的傳遞不同的執行緒，common language runtime (CLR) 該執行緒會暫止、 執行快照集，並繼續。  
  
 `callback`  
 [in]實作的指標[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)方法，由 CLR 分析工具提供有關每個 managed 的框架和未受管理的畫面格的每次執行所呼叫。  
  
 `StackSnapshotCallback`方法藉由分析工具寫入器。  
  
 `infoFlags`  
 [in]值為[COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)列舉，指定要傳遞回每個框架的資料數量`StackSnapshotCallback`。  
  
 `clientData`  
 [in]用戶端資料指標，直接傳遞至`StackSnapshotCallback`回呼函式。  
  
 `context`  
 [in]Win32 指標`CONTEXT`結構，用來植入堆疊查核行程。 Win32`CONTEXT`結構包含 CPU 暫存器的值，而且在特定時間點表示 CPU 的狀態。  
  
 之種子可協助決定在何處開始堆疊查核行程，堆疊的頂端時未受管理的協助程式程式碼; CLR否則會忽略種子。 識別值種子必須提供給非同步查核行程。 如果您要進行同步的查核行程，任何初始值不是必要的。  
  
 `context`參數是傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，才有效`infoFlags`參數。  
  
 `contextSize`  
 [in]大小`CONTEXT`結構，也就由參考`context`參數。  
  
## <a name="remarks"></a>備註  
 傳遞 null`thread`會產生目前執行緒的快照集。 只有當目標執行緒會暫停時，可以建立快照的其他執行緒。  
  
 當分析工具想要堆疊查核行程時，它會呼叫`DoStackSnapshot`。 CLR 會從該呼叫傳回之前，它會呼叫您`StackSnapshotCallback`好幾次，一次針對每個 managed 框架 （或執行未受管理的畫面格數） 堆疊上。 當遇到未受管理的畫面格時，您必須逐步教他們自己。  
  
 堆疊查核行程中的順序就是畫面格已推送至堆疊的方式相反︰ 上次分葉 （最後一個推入） 的畫面格第一次的主要 （第一個推入） 框架。  
  
 如需如何進行程式設計以查核 managed 的堆疊的詳細資訊，請參閱[Profiler 堆疊查核行程.NET Framework 2.0 中：基礎與進階](https://go.microsoft.com/fwlink/?LinkId=73638)。  
  
 堆疊查核行程可以是同步或非同步，如下列各節所述。  
  
## <a name="synchronous-stack-walk"></a>同步的堆疊查核行程  
 同步的堆疊查核行程牽涉到目前執行緒的堆疊查核回呼回應。 它不需要執行或暫止。  
  
 您進行同步時，呼叫以回應呼叫您的分析工具的其中一個 CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (或[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) 方法，您可以呼叫`DoStackSnapshot`至的堆疊查核行程目前的執行緒。 這是很有用，當您想要查看堆疊樣貌通知在這類[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。 您只需要呼叫`DoStackSnapshot`內您`ICorProfilerCallback`方法，傳遞 null`context`和`thread`參數。  
  
## <a name="asynchronous-stack-walk"></a>非同步的堆疊查核行程  
 的非同步堆疊查核行程需要不同的執行緒的堆疊查核或目前執行緒的堆疊查核不在回應回呼，而是由攔截目前執行緒的指令指標。 非同步查核行程要求的種子，如果堆疊的頂端是不是平台一部分的 unmanaged 程式碼叫用 (PInvoke) 或 COM 呼叫，但 CLR 本身中的協助程式程式碼。 比方說，在 just-in-time (JIT) 編譯或記憶體回收收集的程式碼是協助程式程式碼。  
  
 您取得種子透過直接暫停目標執行緒，並逐一查看其堆疊自行，直到您找到的最上層 managed 框架。 目標執行緒暫止之後，取得目標執行緒目前的暫存器內容。 接下來，判斷是否註冊內容指向 unmanaged 程式碼藉由呼叫[icorprofilerinfo:: Getfunctionfromip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — 如果它傳回`FunctionID`等於零，框架的 unmanaged 程式碼。 現在，查看堆疊，直到到達第一個 managed 的框架，然後計算該範圍內的暫存器內容為基礎的識別值種子內容。  
  
 呼叫`DoStackSnapshot`與您的識別值種子內容，開始非同步的堆疊查核行程。 如果您未提供的種子，`DoStackSnapshot`可能略過的受控的框架在堆疊的頂端，並因此，所得到的不完整的堆疊查核行程。 如果您提供的種子，它必須指向 JIT 編譯或原生映像產生器 (Ngen.exe)-產生的程式碼;否則，`DoStackSnapshot`傳回失敗碼，而 CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。  
  
 非同步的堆疊查核行程可以輕易地會造成死結 （deadlock），或存取違規，除非您遵循這些指導方針：  
  
- 當您直接暫停執行緒時，請記得從未執行 managed 程式碼的執行緒可以暫停另一個執行緒。  
  
- 會一直封鎖您[icorprofilercallback:: Threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)回呼，直到該執行緒的堆疊查核行程完成為止。  
  
- 請勿保留鎖定，而您的程式碼剖析工具呼叫可以觸發記憶體回收的 CLR 函式。 也就是說，如果擁有的執行緒可能會觸發記憶體回收的呼叫請勿保留鎖定。  
  
 另外還有死結的風險。 如果您呼叫`DoStackSnapshot`從您的程式碼剖析工具，讓您可以將個別的目標執行緒的堆疊查核行程，已建立的執行緒。 第一次在您建立的執行緒進入特定`ICorProfilerInfo*`方法 (包括`DoStackSnapshot`)，CLR 會執行每個執行緒，在該執行緒上的 CLR 特定的初始化。 如果您的分析工具已暫止的目標執行緒嘗試查核行程的堆疊，而且該目標執行緒發生擁有鎖定所需執行這項每個執行緒初始化，則會發生死結。 若要避免這個死結，讓初始呼叫`DoStackSnapshot`個別目標執行緒，但並不會擱置目標執行緒先從引導您程式碼剖析工具建立的執行緒。 此初始呼叫可確保每個執行緒初始化可以完成不包含死結。 如果`DoStackSnapshot`成功，而且至少一個框架時，會報告該動作之後，將會暫止任何目標執行緒和呼叫該程式碼剖析工具建立執行緒安全`DoStackSnapshot`到該目標執行緒的堆疊查核行程。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
