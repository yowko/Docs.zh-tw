---
title: ICorProfilerCallback::RemotingServerSendingReply 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98563c175f12ad1ff25e1f578270fe1099175487
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453772"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="97e7a-102">ICorProfilerCallback::RemotingServerSendingReply 方法</span><span class="sxs-lookup"><span data-stu-id="97e7a-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="97e7a-103">通知分析工具，處理程序已完成處理遠端方法叫用要求，而且即將傳送回覆，透過的通道。</span><span class="sxs-lookup"><span data-stu-id="97e7a-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="97e7a-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97e7a-105">參數</span><span class="sxs-lookup"><span data-stu-id="97e7a-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="97e7a-106">[in]與中提供的值將對應的 GUID 指標[icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)在這些情況下：</span><span class="sxs-lookup"><span data-stu-id="97e7a-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="97e7a-107">遠端處理 GUID cookie 是使用中。</span><span class="sxs-lookup"><span data-stu-id="97e7a-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="97e7a-108">成功的訊息傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="97e7a-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="97e7a-109">GUID cookie 會啟用用戶端處理程序。</span><span class="sxs-lookup"><span data-stu-id="97e7a-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="97e7a-110">這可讓您輕易地配對的遠端處理呼叫，以及邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="97e7a-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="97e7a-111">[in]值是`true`呼叫是非同步的; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="97e7a-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e7a-112">需求</span><span class="sxs-lookup"><span data-stu-id="97e7a-112">Requirements</span></span>  
 <span data-ttu-id="97e7a-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97e7a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e7a-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97e7a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97e7a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97e7a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97e7a-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97e7a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e7a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97e7a-117">See Also</span></span>  
 [<span data-ttu-id="97e7a-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="97e7a-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
