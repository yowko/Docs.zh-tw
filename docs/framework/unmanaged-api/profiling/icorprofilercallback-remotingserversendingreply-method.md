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
ms.openlocfilehash: bf59d4e418223fd177bc5e19b173674b78e1f2ba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499918"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="9997f-102">ICorProfilerCallback::RemotingServerSendingReply 方法</span><span class="sxs-lookup"><span data-stu-id="9997f-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="9997f-103">通知分析工具，進程已完成處理遠端方法調用要求，而且即將透過通道傳送回復。</span><span class="sxs-lookup"><span data-stu-id="9997f-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9997f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9997f-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9997f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9997f-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="9997f-106">在GUID 的指標，在下列情況下會對應至[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md)中提供的值：</span><span class="sxs-lookup"><span data-stu-id="9997f-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="9997f-107">遠端 GUID cookie 為作用中。</span><span class="sxs-lookup"><span data-stu-id="9997f-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="9997f-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="9997f-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="9997f-109">GUID cookie 會在用戶端進程上作用。</span><span class="sxs-lookup"><span data-stu-id="9997f-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="9997f-110">這可讓您輕鬆地配對遠端呼叫和邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="9997f-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="9997f-111">在`true`如果呼叫是非同步，則值為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9997f-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9997f-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="9997f-112">Requirements</span></span>  
 <span data-ttu-id="9997f-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9997f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9997f-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9997f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9997f-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9997f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9997f-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9997f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9997f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9997f-117">See also</span></span>

- [<span data-ttu-id="9997f-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9997f-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
