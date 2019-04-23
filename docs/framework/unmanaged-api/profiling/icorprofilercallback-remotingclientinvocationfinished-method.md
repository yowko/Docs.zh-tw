---
title: ICorProfilerCallback::RemotingClientInvocationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2722497db5622dee4adcfd9381837477b89a8f63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206573"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="b04aa-102">ICorProfilerCallback::RemotingClientInvocationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="b04aa-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="b04aa-103">通知分析工具在遠端呼叫已在用戶端上執行到完成為止。</span><span class="sxs-lookup"><span data-stu-id="b04aa-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="b04aa-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b04aa-105">備註</span><span class="sxs-lookup"><span data-stu-id="b04aa-105">Remarks</span></span>  
 <span data-ttu-id="b04aa-106">如果遠端呼叫是同步的它具有也完成在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="b04aa-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="b04aa-107">非同步遠端呼叫時，可能仍在處理呼叫時中預期回覆。</span><span class="sxs-lookup"><span data-stu-id="b04aa-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="b04aa-108">如果預期回覆，它就會發生與呼叫[icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)和 額外的呼叫`RemotingClientInvocationFinished`表示必要的次要處理的非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="b04aa-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="b04aa-109">每個下列成對的回呼會在相同執行緒上發生：</span><span class="sxs-lookup"><span data-stu-id="b04aa-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="b04aa-110">`RemotingClientInvocationStarted` 和[icorprofilercallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="b04aa-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="b04aa-111">[Icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)和[icorprofilercallback:: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="b04aa-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="b04aa-112">[Icorprofilercallback:: Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)和[icorprofilercallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="b04aa-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="b04aa-113">您應該注意下列問題與遠端處理回呼：</span><span class="sxs-lookup"><span data-stu-id="b04aa-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="b04aa-114">遠端函式執行不會反映分析工具 API，因此不會正確接收通知之函式的呼叫從用戶端及伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="b04aa-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="b04aa-115">實際的引動過程會透過 proxy 物件;分析工具，它會顯示某些函式是 JIT 編譯，但從未使用。</span><span class="sxs-lookup"><span data-stu-id="b04aa-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="b04aa-116">分析工具不會收到非同步遠端處理事件的精確通知。</span><span class="sxs-lookup"><span data-stu-id="b04aa-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04aa-117">需求</span><span class="sxs-lookup"><span data-stu-id="b04aa-117">Requirements</span></span>  
 <span data-ttu-id="b04aa-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b04aa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04aa-119">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b04aa-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b04aa-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b04aa-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b04aa-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04aa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04aa-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b04aa-122">See also</span></span>

- [<span data-ttu-id="b04aa-123">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b04aa-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
