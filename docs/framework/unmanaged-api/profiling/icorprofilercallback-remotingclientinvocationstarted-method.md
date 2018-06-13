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
ms.openlocfilehash: 1dcb79c4130f6bd163cb807ff92b95db8360a185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461964"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="8d53e-102">ICorProfilerCallback::RemotingClientInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="8d53e-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="8d53e-103">通知分析工具已啟動遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8d53e-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d53e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d53e-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d53e-105">備註</span><span class="sxs-lookup"><span data-stu-id="8d53e-105">Remarks</span></span>  
 <span data-ttu-id="8d53e-106">此事件是相同的同步與非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="8d53e-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="8d53e-107">每個回呼的下列組會在相同執行緒上發生：</span><span class="sxs-lookup"><span data-stu-id="8d53e-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="8d53e-108">`RemotingClientInvocationStarted` 和[icorprofilercallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="8d53e-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="8d53e-109">[Icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)和[icorprofilercallback:: Remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="8d53e-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="8d53e-110">[Icorprofilercallback:: Remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)和[icorprofilercallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="8d53e-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="8d53e-111">您應該注意下列問題的遠端處理回呼：</span><span class="sxs-lookup"><span data-stu-id="8d53e-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="8d53e-112">執行遠端函式不會反映分析工具 API，因此不會適當接收通知的函式的呼叫從用戶端及伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="8d53e-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="8d53e-113">實際的引動過程是透過 proxy 物件。給分析工具，它會顯示某些函式的 JIT 編譯，但從未使用。</span><span class="sxs-lookup"><span data-stu-id="8d53e-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="8d53e-114">分析工具不會接收非同步遠端處理事件的精確通知。</span><span class="sxs-lookup"><span data-stu-id="8d53e-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d53e-115">需求</span><span class="sxs-lookup"><span data-stu-id="8d53e-115">Requirements</span></span>  
 <span data-ttu-id="8d53e-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d53e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d53e-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d53e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d53e-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d53e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d53e-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d53e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d53e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d53e-120">See Also</span></span>  
 [<span data-ttu-id="8d53e-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8d53e-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
