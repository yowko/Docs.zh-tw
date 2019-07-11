---
title: ICorProfilerCallback::RemotingClientSendingMessage 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4729a8d3ac2c6f7ec51a032a07ebfd1c2838cb9a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782899"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="c0c19-102">ICorProfilerCallback::RemotingClientSendingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="c0c19-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="c0c19-103">通知分析工具用戶端會將要求傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="c0c19-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c19-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0c19-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0c19-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0c19-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="c0c19-106">[in]值，這個值會對應中提供的價值[icorprofilercallback:: Remotingserverreceivingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)在這些情況下：</span><span class="sxs-lookup"><span data-stu-id="c0c19-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="c0c19-107">遠端處理 GUID cookie 在作用中。</span><span class="sxs-lookup"><span data-stu-id="c0c19-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="c0c19-108">成功的訊息傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="c0c19-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="c0c19-109">GUID cookie 上為作用中伺服器端處理序。</span><span class="sxs-lookup"><span data-stu-id="c0c19-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="c0c19-110">這可讓您輕易地配對的遠端呼叫，以及建立的邏輯呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="c0c19-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="c0c19-111">[in]值是`true`的呼叫是非同步，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="c0c19-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0c19-112">需求</span><span class="sxs-lookup"><span data-stu-id="c0c19-112">Requirements</span></span>  
 <span data-ttu-id="c0c19-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0c19-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0c19-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0c19-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0c19-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0c19-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0c19-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0c19-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c19-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0c19-117">See also</span></span>

- [<span data-ttu-id="c0c19-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c0c19-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
