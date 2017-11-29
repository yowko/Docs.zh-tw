---
title: "ICorProfilerCallback::RemotingServerSendingReply 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerSendingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b99b2de235634b715a6f5ba9fee9ee49ab34063a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="ec77c-102">ICorProfilerCallback::RemotingServerSendingReply 方法</span><span class="sxs-lookup"><span data-stu-id="ec77c-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="ec77c-103">通知分析工具，處理程序已完成處理遠端方法叫用要求，而且即將傳送回覆，透過的通道。</span><span class="sxs-lookup"><span data-stu-id="ec77c-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec77c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec77c-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec77c-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec77c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="ec77c-106">[in]與中提供的值將對應的 GUID 指標[icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)在這些情況下：</span><span class="sxs-lookup"><span data-stu-id="ec77c-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="ec77c-107">遠端處理 GUID cookie 是使用中。</span><span class="sxs-lookup"><span data-stu-id="ec77c-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="ec77c-108">成功的訊息傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="ec77c-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="ec77c-109">GUID cookie 會啟用用戶端處理程序。</span><span class="sxs-lookup"><span data-stu-id="ec77c-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="ec77c-110">這可讓您輕易地配對的遠端處理呼叫，以及邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="ec77c-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="ec77c-111">[in]值是`true`呼叫是非同步的; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="ec77c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec77c-112">需求</span><span class="sxs-lookup"><span data-stu-id="ec77c-112">Requirements</span></span>  
 <span data-ttu-id="ec77c-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec77c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec77c-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec77c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec77c-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec77c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec77c-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec77c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec77c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec77c-117">See Also</span></span>  
 [<span data-ttu-id="ec77c-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ec77c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
