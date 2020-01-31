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
ms.openlocfilehash: 8ae58344a7a17637bf08b9b5179abdba7e7060d6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866022"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="bed7c-102">ICorProfilerCallback::RemotingClientSendingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="bed7c-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="bed7c-103">通知分析工具用戶端正在將要求傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="bed7c-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bed7c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="bed7c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="bed7c-106">在在下列情況下，對應于[ICorProfilerCallback：： RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md)中所提供之值的值：</span><span class="sxs-lookup"><span data-stu-id="bed7c-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="bed7c-107">遠端 GUID cookie 為作用中。</span><span class="sxs-lookup"><span data-stu-id="bed7c-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="bed7c-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="bed7c-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="bed7c-109">GUID cookie 會在伺服器端進程上作用。</span><span class="sxs-lookup"><span data-stu-id="bed7c-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="bed7c-110">這可讓您輕鬆地配對遠端呼叫和邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="bed7c-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="bed7c-111">在如果呼叫是非同步，則為 `true` 的值;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="bed7c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed7c-112">需求</span><span class="sxs-lookup"><span data-stu-id="bed7c-112">Requirements</span></span>  
 <span data-ttu-id="bed7c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bed7c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed7c-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bed7c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bed7c-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bed7c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bed7c-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bed7c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed7c-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="bed7c-117">See also</span></span>

- [<span data-ttu-id="bed7c-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bed7c-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
