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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 313dd7526478377ca457d165de4b95e7e81d93f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599776"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="dfaed-102">ICorProfilerCallback::RemotingClientReceivingReply 方法</span><span class="sxs-lookup"><span data-stu-id="dfaed-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="dfaed-103">通知分析工具的遠端呼叫的伺服器端部分已完成，而且用戶端正在接收以及有關處理回覆。</span><span class="sxs-lookup"><span data-stu-id="dfaed-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfaed-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfaed-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfaed-105">參數</span><span class="sxs-lookup"><span data-stu-id="dfaed-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="dfaed-106">[in]值，這個值會對應中提供的價值[icorprofilercallback:: Remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)在這些情況下：</span><span class="sxs-lookup"><span data-stu-id="dfaed-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="dfaed-107">遠端處理 GUID cookie 在作用中。</span><span class="sxs-lookup"><span data-stu-id="dfaed-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="dfaed-108">成功的訊息傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="dfaed-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="dfaed-109">GUID cookie 上為作用中伺服器端處理序。</span><span class="sxs-lookup"><span data-stu-id="dfaed-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="dfaed-110">這可讓您輕易地配對的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="dfaed-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="dfaed-111">[in]值是`true`的呼叫是非同步，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="dfaed-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfaed-112">需求</span><span class="sxs-lookup"><span data-stu-id="dfaed-112">Requirements</span></span>  
 <span data-ttu-id="dfaed-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfaed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfaed-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dfaed-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dfaed-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfaed-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfaed-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfaed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfaed-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfaed-117">See also</span></span>
- [<span data-ttu-id="dfaed-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="dfaed-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
