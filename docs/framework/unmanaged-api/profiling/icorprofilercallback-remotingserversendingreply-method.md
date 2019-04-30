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
ms.openlocfilehash: 024b1f3f7e08dc21582789de7f3899e8e44d5e39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041830"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="056f6-102">ICorProfilerCallback::RemotingServerSendingReply 方法</span><span class="sxs-lookup"><span data-stu-id="056f6-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="056f6-103">通知分析工具，處理程序已完成處理遠端方法引動過程要求，並將要傳輸的回覆，透過的通道。</span><span class="sxs-lookup"><span data-stu-id="056f6-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="056f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="056f6-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="056f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="056f6-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="056f6-106">[in]中提供的值會對應至 GUID 的指標[icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)在這些情況下：</span><span class="sxs-lookup"><span data-stu-id="056f6-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="056f6-107">遠端處理 GUID cookie 在作用中。</span><span class="sxs-lookup"><span data-stu-id="056f6-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="056f6-108">成功的訊息傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="056f6-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="056f6-109">GUID cookie 上為作用中的用戶端程序。</span><span class="sxs-lookup"><span data-stu-id="056f6-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="056f6-110">這可讓您輕易地配對的遠端呼叫，以及建立的邏輯呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="056f6-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="056f6-111">[in]值是`true`的呼叫是非同步，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="056f6-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="056f6-112">需求</span><span class="sxs-lookup"><span data-stu-id="056f6-112">Requirements</span></span>  
 <span data-ttu-id="056f6-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="056f6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="056f6-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="056f6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="056f6-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="056f6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="056f6-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="056f6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056f6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="056f6-117">See also</span></span>

- [<span data-ttu-id="056f6-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="056f6-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
