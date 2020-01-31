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
ms.openlocfilehash: f77901623ef4df7b43276c18a910cf62fcc4451d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865970"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="35c13-102">ICorProfilerCallback::RemotingServerSendingReply 方法</span><span class="sxs-lookup"><span data-stu-id="35c13-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="35c13-103">通知分析工具，進程已完成處理遠端方法調用要求，而且即將透過通道傳送回復。</span><span class="sxs-lookup"><span data-stu-id="35c13-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c13-104">語法</span><span class="sxs-lookup"><span data-stu-id="35c13-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35c13-105">參數</span><span class="sxs-lookup"><span data-stu-id="35c13-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="35c13-106">在GUID 的指標，在下列情況下會對應至[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md)中提供的值：</span><span class="sxs-lookup"><span data-stu-id="35c13-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="35c13-107">遠端 GUID cookie 為作用中。</span><span class="sxs-lookup"><span data-stu-id="35c13-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="35c13-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="35c13-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="35c13-109">GUID cookie 會在用戶端進程上作用。</span><span class="sxs-lookup"><span data-stu-id="35c13-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="35c13-110">這可讓您輕鬆地配對遠端呼叫和邏輯呼叫堆疊的建立。</span><span class="sxs-lookup"><span data-stu-id="35c13-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="35c13-111">在如果呼叫是非同步，則為 `true` 的值;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="35c13-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35c13-112">需求</span><span class="sxs-lookup"><span data-stu-id="35c13-112">Requirements</span></span>  
 <span data-ttu-id="35c13-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35c13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35c13-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35c13-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35c13-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35c13-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35c13-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35c13-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c13-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="35c13-117">See also</span></span>

- [<span data-ttu-id="35c13-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="35c13-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
