---
title: "ICorProfilerInfo2::DoStackSnapshot 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.DoStackSnapshot
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type: apiref
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a210fc0c1984ee9bc77114ba30c3287ae43b169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot 方法
引導 managed 的框架，在指定之執行緒的堆疊上，並將資訊傳送給分析工具透過回呼。  
  
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
  
#### <a name="parameters"></a>參數  
 `thread`  
 [in]目標執行緒的識別碼。  
  
 傳遞 null 中`thread`會產生目前執行緒的快照集。 如果`ThreadID`的傳遞不同的執行緒時，common language runtime (CLR) 內暫止的執行緒、 執行快照集，並繼續。  
  
 `callback`  
 [in]指標的實作[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) CLR 分析工具提供有關每個 managed 的框架和未受管理的畫面格的每次執行所呼叫的方法。  
  
 `StackSnapshotCallback`方法藉由分析工具寫入器。  
  
 `infoFlags`  
 [in]值為[COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)列舉，指定要傳遞的每個畫面格的資料數量`StackSnapshotCallback`。  
  
 `clientData`  
 [in]透過直接傳遞至用戶端資料指標`StackSnapshotCallback`回呼函式。  
  
 `context`  
 [in]對 win32 指標`CONTEXT`結構，用來植入堆疊查核行程。 Win32`CONTEXT`結構 CPU 暫存器的值，表示 CPU 的狀態，在特定時間點。  
  
 種子可協助決定在何處開始堆疊查核行程，堆疊的頂端是未受管理的協助程式程式碼; 如果在 CLR否則，會忽略種子。 識別值種子必須提供給非同步查核行程。 如果您要同步的查核行程，任何初始值不是必要的。  
  
 `context`參數是傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，才有效`infoFlags`參數。  
  
 `contextSize`  
 [in]大小`CONTEXT`結構，也就由參考`context`參數。  
  
## <a name="remarks"></a>備註  
 傳遞 null`thread`會產生目前執行緒的快照集。 只有當目標執行緒暫止時，可以拍攝快照的其他執行緒。  
  
 當分析工具想要堆疊查核行程時，它會呼叫`DoStackSnapshot`。 CLR 會從該呼叫傳回之前，它會呼叫您`StackSnapshotCallback`數次，一次針對每個 managed 框架 （或執行未受管理的框架） 堆疊上。 當遇到未受管理的畫面格時，您必須引導他們自己。  
  
 堆疊查核行程中的順序是相反的框架已推送至堆疊的方式： 最後一個分葉 （最後一個推入） 第一次的主要 （第一個推入） 框架。  
  
 如需如何以程式設計的程式碼剖析工具，以查核 managed 的堆疊方式的詳細資訊，請參閱[分析工具堆疊查核行程.NET Framework 2.0： 基本概念和其他](http://go.microsoft.com/fwlink/?LinkId=73638)。  
  
 堆疊查核行程可以是同步或非同步，如下列各節所述。  
  
## <a name="synchronous-stack-walk"></a>同步的堆疊查核行程  
 同步的堆疊查核行程牽涉到目前執行緒的堆疊查核回呼回應。 它不需要執行或暫止。  
  
 您進行同步時，呼叫以呼叫您的分析工具的其中一個 CLR 回應[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (或[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) 方法，您可以呼叫`DoStackSnapshot`查核堆疊目前的執行緒。 這是很有用，當您想要查看堆疊的外觀通知在這類[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。 您只需要呼叫`DoStackSnapshot`從您`ICorProfilerCallback`方法，傳遞 null`context`和`thread`參數。  
  
## <a name="asynchronous-stack-walk"></a>非同步的堆疊查核行程  
 非同步堆疊查核行程需要在不同的執行緒的堆疊查核或目前的執行緒的堆疊查核不在回應回呼，但所攔截目前的執行緒指令指標。 非同步查核行程需要種子，如果堆疊的頂端是 unmanaged 程式碼不包含在為平台叫用 (PInvoke) 或 COM 呼叫，但本身在 CLR 中的協助程式程式碼。 例如，在 just-in-time (JIT) 編譯或記憶體回收集合程式碼是協助程式程式碼。  
  
 您透過直接暫停目標執行緒取得種子和其堆疊查核行程自行，直到您找到最上方 managed 框架。 執行緒暫止目標之後，會出現目標執行緒目前的暫存器內容。 接下來，判斷是否註冊內容指向 unmanaged 程式碼藉由呼叫[icorprofilerinfo:: Getfunctionfromip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — 如果它傳回`FunctionID`等於零的畫面格是 unmanaged 程式碼。 現在，堆疊查核行程直到到達第一個受管理的畫面格，然後計算種子內容根據該框架的暫存器內容。  
  
 呼叫`DoStackSnapshot`與種子內容開始非同步的堆疊查核行程。 如果您未提供為種子`DoStackSnapshot`可能會略過 managed 的堆疊的頂端框架，因此，可讓您完整堆疊查核行程。 如果您提供的種子，它必須指向 JIT 編譯或原生映像產生器 (Ngen.exe)-產生的程式碼;否則，`DoStackSnapshot`傳回失敗碼，CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。  
  
 非同步的堆疊查核行程可以輕鬆地會造成死結或存取違規，除非您依照這些指導方針：  
  
-   當您直接暫停執行緒時，請記住從未執行 managed 程式碼的執行緒可以暫停另一個執行緒。  
  
-   一律在封鎖您[icorprofilercallback:: Threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)該執行緒的堆疊查核行程直到完成回呼。  
  
-   分析工具可以觸發記憶體回收的 CLR 函式呼叫時，請勿保留鎖定。 也就是說，不需持有鎖定如果擁有資源的執行緒可能會觸發記憶體回收的呼叫。  
  
 另外還有死結的風險是如果您呼叫`DoStackSnapshot`從您的分析工具已建立，以便您可以將不同的目標執行緒的堆疊查核行程的執行緒。 第一次您建立的執行緒進入特定`ICorProfilerInfo*`方法 (包括`DoStackSnapshot`)，CLR 會執行每個執行緒，在該執行緒上的 CLR 特定初始化。 如果您的分析工具已暫停目標執行緒嘗試查核行程，其堆疊，而且擁有鎖定的必要執行這個每個執行緒的初始化發生該目標執行緒，則會發生死結。 若要避免這個死結，請至初始呼叫`DoStackSnapshot`從您程式碼剖析工具建立的執行緒，瀏覽個別目標執行緒，但並不會擱置目標執行緒第一次。 此第一次呼叫可確保每個執行緒初始化可以完成不包含死結。 如果`DoStackSnapshot`成功，而且至少一個框架時，會報告該點之後，將會暫停任何目標執行緒和呼叫該程式碼剖析工具建立的執行緒安全`DoStackSnapshot`到該目標執行緒的堆疊查核行程。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
