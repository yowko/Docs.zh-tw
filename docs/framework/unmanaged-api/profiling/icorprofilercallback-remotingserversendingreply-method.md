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
ms.openlocfilehash: 1d876644ae35d13a481b01d9e0e5ff0d0764ca18
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713947"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="ada82-102">ICorProfilerCallback::RemotingServerSendingReply 方法</span><span class="sxs-lookup"><span data-stu-id="ada82-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>

<span data-ttu-id="ada82-103">通知分析工具進程已完成遠端方法調用要求的處理，而且即將透過通道傳送回復。</span><span class="sxs-lookup"><span data-stu-id="ada82-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada82-104">語法</span><span class="sxs-lookup"><span data-stu-id="ada82-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ada82-105">參數</span><span class="sxs-lookup"><span data-stu-id="ada82-105">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="ada82-106">在GUID 的指標，會對應到下列條件下， [ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) 中提供的值：</span><span class="sxs-lookup"><span data-stu-id="ada82-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="ada82-107">遠端 GUID cookie 為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="ada82-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="ada82-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="ada82-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="ada82-109">GUID cookie 在用戶端進程中為作用中。</span><span class="sxs-lookup"><span data-stu-id="ada82-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="ada82-110">這可讓您輕鬆配對遠端呼叫和建立邏輯呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="ada82-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="ada82-111">在值， `true` 如果呼叫是非同步，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ada82-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada82-112">需求</span><span class="sxs-lookup"><span data-stu-id="ada82-112">Requirements</span></span>  

 <span data-ttu-id="ada82-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ada82-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada82-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ada82-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ada82-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ada82-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ada82-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada82-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada82-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ada82-117">See also</span></span>

- [<span data-ttu-id="ada82-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ada82-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
