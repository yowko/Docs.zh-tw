---
title: "ICorProfilerCallback::RemotingClientInvocationFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f0ae2be95b559074ca9dacde493a98008608b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="5087c-102">ICorProfilerCallback::RemotingClientInvocationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="5087c-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="5087c-103">通知分析工具的遠端呼叫已在用戶端上執行到完成。</span><span class="sxs-lookup"><span data-stu-id="5087c-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5087c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5087c-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5087c-105">備註</span><span class="sxs-lookup"><span data-stu-id="5087c-105">Remarks</span></span>  
 <span data-ttu-id="5087c-106">如果遠端呼叫是同步的它也執行完成在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="5087c-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="5087c-107">如果遠端呼叫是非同步，請呼叫處理時，可能仍然要有回覆。</span><span class="sxs-lookup"><span data-stu-id="5087c-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="5087c-108">如果預期回覆，它就會發生與呼叫[icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)和額外的呼叫`RemotingClientInvocationFinished`表示必要次要處理的非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="5087c-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="5087c-109">每個回呼的下列組會在相同執行緒上發生：</span><span class="sxs-lookup"><span data-stu-id="5087c-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="5087c-110">`RemotingClientInvocationStarted`和[icorprofilercallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="5087c-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="5087c-111">[Icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)和[icorprofilercallback:: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="5087c-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="5087c-112">[Icorprofilercallback:: Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)和[icorprofilercallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="5087c-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="5087c-113">您應該注意下列問題的遠端處理回呼：</span><span class="sxs-lookup"><span data-stu-id="5087c-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="5087c-114">執行遠端函式不會反映分析工具 API，因此不會適當接收通知的函式的呼叫從用戶端及伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="5087c-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="5087c-115">實際的引動過程是透過 proxy 物件。給分析工具，它會顯示某些函式的 JIT 編譯，但從未使用。</span><span class="sxs-lookup"><span data-stu-id="5087c-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="5087c-116">分析工具不會接收非同步遠端處理事件的精確通知。</span><span class="sxs-lookup"><span data-stu-id="5087c-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5087c-117">需求</span><span class="sxs-lookup"><span data-stu-id="5087c-117">Requirements</span></span>  
 <span data-ttu-id="5087c-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5087c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5087c-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5087c-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5087c-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5087c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5087c-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5087c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5087c-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="5087c-122">See Also</span></span>  
 [<span data-ttu-id="5087c-123">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5087c-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
