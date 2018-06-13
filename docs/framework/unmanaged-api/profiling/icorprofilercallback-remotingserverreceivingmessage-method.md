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
ms.openlocfilehash: c1874b5bea465eb31bcaad2d912b90d35cfc711b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454097"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="be76d-102">ICorProfilerCallback::RemotingServerReceivingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="be76d-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="be76d-103">通知分析工具的處理序收到的遠端方法叫用或啟用要求。</span><span class="sxs-lookup"><span data-stu-id="be76d-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be76d-104">語法</span><span class="sxs-lookup"><span data-stu-id="be76d-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be76d-105">參數</span><span class="sxs-lookup"><span data-stu-id="be76d-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="be76d-106">[in]值，這個值會對應中提供的值與[icorprofilercallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)在這些情況下：</span><span class="sxs-lookup"><span data-stu-id="be76d-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="be76d-107">遠端處理 GUID cookie 是使用中。</span><span class="sxs-lookup"><span data-stu-id="be76d-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="be76d-108">成功的訊息傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="be76d-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="be76d-109">GUID cookie 會啟用用戶端處理程序。</span><span class="sxs-lookup"><span data-stu-id="be76d-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="be76d-110">這可讓您輕易地配對的遠端處理呼叫，以及邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="be76d-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="be76d-111">[in]值是`true`呼叫是非同步的; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="be76d-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be76d-112">備註</span><span class="sxs-lookup"><span data-stu-id="be76d-112">Remarks</span></span>  
 <span data-ttu-id="be76d-113">如果是非同步的訊息要求，要求可以處理任意執行緒。</span><span class="sxs-lookup"><span data-stu-id="be76d-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be76d-114">需求</span><span class="sxs-lookup"><span data-stu-id="be76d-114">Requirements</span></span>  
 <span data-ttu-id="be76d-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be76d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be76d-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be76d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be76d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be76d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be76d-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be76d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be76d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be76d-119">See Also</span></span>  
 [<span data-ttu-id="be76d-120">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="be76d-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
