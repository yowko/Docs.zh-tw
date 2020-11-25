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
ms.openlocfilehash: d41ccd30707eba269bbac7231e06792363615544
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719316"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="5c32c-102">ICorProfilerCallback::RemotingClientInvocationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="5c32c-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>

<span data-ttu-id="5c32c-103">通知分析工具，遠端呼叫已在用戶端上執行完成。</span><span class="sxs-lookup"><span data-stu-id="5c32c-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c32c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c32c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5c32c-105">備註</span><span class="sxs-lookup"><span data-stu-id="5c32c-105">Remarks</span></span>  

 <span data-ttu-id="5c32c-106">如果遠端呼叫是同步的，則它也會在伺服器上執行完成。</span><span class="sxs-lookup"><span data-stu-id="5c32c-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="5c32c-107">如果遠端呼叫是非同步，則在處理呼叫時，可能仍預期會有回復。</span><span class="sxs-lookup"><span data-stu-id="5c32c-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="5c32c-108">如果預期的是回復，則會在呼叫 [ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) 時進行，並以另一個呼叫來 `RemotingClientInvocationFinished` 指出非同步呼叫所需的次要處理。</span><span class="sxs-lookup"><span data-stu-id="5c32c-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="5c32c-109">下列每一組回呼都會在相同的執行緒上進行：</span><span class="sxs-lookup"><span data-stu-id="5c32c-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="5c32c-110">`RemotingClientInvocationStarted` 和 [ICorProfilerCallback：： RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="5c32c-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="5c32c-111">[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) 和 [ICorProfilerCallback：： RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="5c32c-111">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="5c32c-112">[ICorProfilerCallback：： RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) 和 [ICorProfilerCallback：： RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="5c32c-112">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="5c32c-113">您應該注意到下列遠端回呼的問題：</span><span class="sxs-lookup"><span data-stu-id="5c32c-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="5c32c-114">Profiler API 不會反映執行遠端函式，因此不會正確地接收從用戶端呼叫並在伺服器上執行之函式的通知。</span><span class="sxs-lookup"><span data-stu-id="5c32c-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="5c32c-115">實際的調用會透過 proxy 物件進行;分析工具會顯示某些函式已進行 JIT 編譯，但從未使用過。</span><span class="sxs-lookup"><span data-stu-id="5c32c-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="5c32c-116">分析工具不會收到非同步遠端處理事件的精確通知。</span><span class="sxs-lookup"><span data-stu-id="5c32c-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c32c-117">需求</span><span class="sxs-lookup"><span data-stu-id="5c32c-117">Requirements</span></span>  

 <span data-ttu-id="5c32c-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c32c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c32c-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c32c-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c32c-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c32c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c32c-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c32c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c32c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c32c-122">See also</span></span>

- [<span data-ttu-id="5c32c-123">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5c32c-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
