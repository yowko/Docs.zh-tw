---
title: ICorProfilerCallback::RemotingClientReceivingReply 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: e25cbfabc10da0c7b1095a956583bb5c7450dba9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445815"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="84613-102">ICorProfilerCallback::RemotingClientReceivingReply 方法</span><span class="sxs-lookup"><span data-stu-id="84613-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="84613-103">通知分析工具，遠端呼叫的伺服器端部分已完成，而且用戶端現在正在接收，且即將處理回復。</span><span class="sxs-lookup"><span data-stu-id="84613-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84613-104">語法</span><span class="sxs-lookup"><span data-stu-id="84613-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="84613-105">參數</span><span class="sxs-lookup"><span data-stu-id="84613-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="84613-106">在在下列情況下，將會對應至[ICorProfilerCallback：： RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)中所提供之值的值：</span><span class="sxs-lookup"><span data-stu-id="84613-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="84613-107">遠端 GUID cookie 為作用中。</span><span class="sxs-lookup"><span data-stu-id="84613-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="84613-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="84613-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="84613-109">GUID cookie 會在伺服器端進程上作用。</span><span class="sxs-lookup"><span data-stu-id="84613-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="84613-110">這讓遠端呼叫能夠輕鬆配對。</span><span class="sxs-lookup"><span data-stu-id="84613-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="84613-111">在如果呼叫是非同步，則為 `true` 的值;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="84613-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84613-112">需求</span><span class="sxs-lookup"><span data-stu-id="84613-112">Requirements</span></span>  
 <span data-ttu-id="84613-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84613-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84613-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84613-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84613-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84613-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84613-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84613-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84613-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84613-117">See also</span></span>

- [<span data-ttu-id="84613-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="84613-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
