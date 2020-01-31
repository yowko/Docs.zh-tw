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
ms.openlocfilehash: 93bd1010374413f3f4ef7e1424ff8194dded8bb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866039"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="ddb1a-102">ICorProfilerCallback::RemotingClientInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="ddb1a-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="ddb1a-103">通知 profiler，遠端呼叫已啟動。</span><span class="sxs-lookup"><span data-stu-id="ddb1a-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb1a-104">語法</span><span class="sxs-lookup"><span data-stu-id="ddb1a-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ddb1a-105">備註</span><span class="sxs-lookup"><span data-stu-id="ddb1a-105">Remarks</span></span>  
 <span data-ttu-id="ddb1a-106">這個事件對同步和非同步呼叫都是相同的。</span><span class="sxs-lookup"><span data-stu-id="ddb1a-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="ddb1a-107">下列每一組回呼都會在同一個執行緒上執行：</span><span class="sxs-lookup"><span data-stu-id="ddb1a-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="ddb1a-108">`RemotingClientInvocationStarted` 和[ICorProfilerCallback：： RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="ddb1a-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="ddb1a-109">[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md)和[ICorProfilerCallback：： RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="ddb1a-109">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="ddb1a-110">[ICorProfilerCallback：： RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md)和[ICorProfilerCallback：： RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="ddb1a-110">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="ddb1a-111">您應該注意下列遠端回呼的問題：</span><span class="sxs-lookup"><span data-stu-id="ddb1a-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="ddb1a-112">分析工具 API 不會反映執行遠端函式，因此不會正確接收從用戶端呼叫並在伺服器上執行之函式的通知。</span><span class="sxs-lookup"><span data-stu-id="ddb1a-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="ddb1a-113">實際的調用會透過 proxy 物件進行;程式碼剖析工具會顯示某些函式已進行 JIT 編譯，但從未使用過。</span><span class="sxs-lookup"><span data-stu-id="ddb1a-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="ddb1a-114">分析工具不會收到非同步遠端處理事件的精確通知。</span><span class="sxs-lookup"><span data-stu-id="ddb1a-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb1a-115">需求</span><span class="sxs-lookup"><span data-stu-id="ddb1a-115">Requirements</span></span>  
 <span data-ttu-id="ddb1a-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb1a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb1a-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ddb1a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddb1a-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddb1a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddb1a-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb1a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb1a-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddb1a-120">See also</span></span>

- [<span data-ttu-id="ddb1a-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ddb1a-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
