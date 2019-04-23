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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30015cc6cae935c43cdbfec1a6eeae5c703ef9f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103203"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="f0f77-102">ICorProfilerCallback::RemotingServerReceivingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="f0f77-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="f0f77-103">通知分析工具處理序已收到的遠端方法叫用或啟用要求。</span><span class="sxs-lookup"><span data-stu-id="f0f77-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f77-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0f77-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0f77-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0f77-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="f0f77-106">[in]值，這個值會對應中提供的價值[icorprofilercallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)在這些情況下：</span><span class="sxs-lookup"><span data-stu-id="f0f77-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="f0f77-107">遠端處理 GUID cookie 在作用中。</span><span class="sxs-lookup"><span data-stu-id="f0f77-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="f0f77-108">成功的訊息傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="f0f77-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="f0f77-109">GUID cookie 上為作用中的用戶端程序。</span><span class="sxs-lookup"><span data-stu-id="f0f77-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="f0f77-110">這可讓您輕易地配對的遠端呼叫，以及建立的邏輯呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="f0f77-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f0f77-111">[in]值是`true`的呼叫是非同步，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="f0f77-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0f77-112">備註</span><span class="sxs-lookup"><span data-stu-id="f0f77-112">Remarks</span></span>  
 <span data-ttu-id="f0f77-113">如果是非同步的訊息要求，要求可以處理任何任意的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f0f77-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0f77-114">需求</span><span class="sxs-lookup"><span data-stu-id="f0f77-114">Requirements</span></span>  
 <span data-ttu-id="f0f77-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f77-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0f77-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0f77-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0f77-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0f77-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0f77-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0f77-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f77-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0f77-119">See also</span></span>

- [<span data-ttu-id="f0f77-120">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f0f77-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
