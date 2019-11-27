---
title: ICorProfilerCallback::RemotingServerReceivingMessage 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 2c2eb7d0dc04d813b1ce91fb1acf4b171f244592
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445756"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="df5cb-102">ICorProfilerCallback::RemotingServerReceivingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="df5cb-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="df5cb-103">通知分析工具，進程已收到遠端方法調用或啟用要求。</span><span class="sxs-lookup"><span data-stu-id="df5cb-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df5cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="df5cb-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df5cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="df5cb-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="df5cb-106">在在下列情況下，將會對應至[ICorProfilerCallback：： RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)中所提供之值的值：</span><span class="sxs-lookup"><span data-stu-id="df5cb-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="df5cb-107">遠端 GUID cookie 為作用中。</span><span class="sxs-lookup"><span data-stu-id="df5cb-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="df5cb-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="df5cb-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="df5cb-109">GUID cookie 會在用戶端進程上作用。</span><span class="sxs-lookup"><span data-stu-id="df5cb-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="df5cb-110">這可讓您輕鬆地配對遠端呼叫和邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="df5cb-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="df5cb-111">在如果呼叫是非同步，則為 `true` 的值;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="df5cb-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df5cb-112">備註</span><span class="sxs-lookup"><span data-stu-id="df5cb-112">Remarks</span></span>  
 <span data-ttu-id="df5cb-113">如果訊息要求是非同步，則要求可由任何任意執行緒服務。</span><span class="sxs-lookup"><span data-stu-id="df5cb-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df5cb-114">需求</span><span class="sxs-lookup"><span data-stu-id="df5cb-114">Requirements</span></span>  
 <span data-ttu-id="df5cb-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df5cb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df5cb-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df5cb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df5cb-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df5cb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df5cb-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df5cb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df5cb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df5cb-119">See also</span></span>

- [<span data-ttu-id="df5cb-120">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="df5cb-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
