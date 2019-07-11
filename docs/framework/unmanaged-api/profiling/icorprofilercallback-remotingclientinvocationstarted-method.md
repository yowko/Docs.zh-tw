---
title: ICorProfilerCallback::RemotingClientInvocationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1f73b36fc1e3a464155f390c25e956f9d706a73
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782927"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="c5b2d-102">ICorProfilerCallback::RemotingClientInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="c5b2d-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="c5b2d-103">通知分析工具已啟動遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c5b2d-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5b2d-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c5b2d-105">備註</span><span class="sxs-lookup"><span data-stu-id="c5b2d-105">Remarks</span></span>  
 <span data-ttu-id="c5b2d-106">這個事件是相同的同步與非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="c5b2d-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="c5b2d-107">每個下列成對的回呼會在相同執行緒上發生：</span><span class="sxs-lookup"><span data-stu-id="c5b2d-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="c5b2d-108">`RemotingClientInvocationStarted` 和[icorprofilercallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="c5b2d-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="c5b2d-109">[Icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)和[icorprofilercallback:: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="c5b2d-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="c5b2d-110">[Icorprofilercallback:: Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)和[icorprofilercallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="c5b2d-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="c5b2d-111">您應該注意下列問題與遠端處理回呼：</span><span class="sxs-lookup"><span data-stu-id="c5b2d-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="c5b2d-112">遠端函式執行不會反映分析工具 API，因此不會正確接收通知之函式的呼叫從用戶端及伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="c5b2d-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="c5b2d-113">實際的引動過程會透過 proxy 物件;分析工具，它會顯示某些函式是 JIT 編譯，但從未使用。</span><span class="sxs-lookup"><span data-stu-id="c5b2d-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="c5b2d-114">分析工具不會收到非同步遠端處理事件的精確通知。</span><span class="sxs-lookup"><span data-stu-id="c5b2d-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5b2d-115">需求</span><span class="sxs-lookup"><span data-stu-id="c5b2d-115">Requirements</span></span>  
 <span data-ttu-id="c5b2d-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5b2d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5b2d-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5b2d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5b2d-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5b2d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5b2d-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5b2d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b2d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5b2d-120">See also</span></span>

- [<span data-ttu-id="c5b2d-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c5b2d-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
