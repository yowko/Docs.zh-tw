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
ms.openlocfilehash: 157e6bc6cb9603fa9558ad6d39f0b086849fc7b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499892"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="caf0a-102">ICorProfilerCallback::RemotingServerReceivingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="caf0a-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="caf0a-103">通知分析工具，進程已收到遠端方法調用或啟用要求。</span><span class="sxs-lookup"><span data-stu-id="caf0a-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caf0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="caf0a-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caf0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="caf0a-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="caf0a-106">在在下列情況下，將會對應至[ICorProfilerCallback：： RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)中所提供之值的值：</span><span class="sxs-lookup"><span data-stu-id="caf0a-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="caf0a-107">遠端 GUID cookie 為作用中。</span><span class="sxs-lookup"><span data-stu-id="caf0a-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="caf0a-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="caf0a-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="caf0a-109">GUID cookie 會在用戶端進程上作用。</span><span class="sxs-lookup"><span data-stu-id="caf0a-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="caf0a-110">這可讓您輕鬆地配對遠端呼叫和邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="caf0a-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="caf0a-111">在`true`如果呼叫是非同步，則值為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="caf0a-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="caf0a-112">備註</span><span class="sxs-lookup"><span data-stu-id="caf0a-112">Remarks</span></span>  
 <span data-ttu-id="caf0a-113">如果訊息要求是非同步，則要求可由任何任意執行緒服務。</span><span class="sxs-lookup"><span data-stu-id="caf0a-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caf0a-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="caf0a-114">Requirements</span></span>  
 <span data-ttu-id="caf0a-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="caf0a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caf0a-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="caf0a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="caf0a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caf0a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caf0a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caf0a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf0a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caf0a-119">See also</span></span>

- [<span data-ttu-id="caf0a-120">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="caf0a-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
