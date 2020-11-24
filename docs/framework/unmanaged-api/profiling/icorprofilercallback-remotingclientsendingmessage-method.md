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
ms.openlocfilehash: 2ef8f066831df1437bd0b6a6f155dd459cae1eb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676838"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="c7744-102">ICorProfilerCallback::RemotingClientSendingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="c7744-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>

<span data-ttu-id="c7744-103">通知分析工具用戶端正在將要求傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="c7744-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7744-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7744-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7744-105">參數</span><span class="sxs-lookup"><span data-stu-id="c7744-105">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="c7744-106">在在下列情況下，對應于 [ICorProfilerCallback：： RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) 中所提供值的值：</span><span class="sxs-lookup"><span data-stu-id="c7744-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="c7744-107">遠端 GUID cookie 為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="c7744-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="c7744-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="c7744-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="c7744-109">GUID cookie 在伺服器端進程中為作用中。</span><span class="sxs-lookup"><span data-stu-id="c7744-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="c7744-110">這可讓您輕鬆配對遠端呼叫和建立邏輯呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="c7744-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="c7744-111">在值， `true` 如果呼叫是非同步，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c7744-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7744-112">需求</span><span class="sxs-lookup"><span data-stu-id="c7744-112">Requirements</span></span>  

 <span data-ttu-id="c7744-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7744-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7744-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7744-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7744-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7744-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7744-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7744-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7744-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7744-117">See also</span></span>

- [<span data-ttu-id="c7744-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c7744-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
