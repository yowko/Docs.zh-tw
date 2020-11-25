---
title: ICorProfilerCallback::RemotingClientReceivingReply 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 058c66af85da6c902e3d628e1b1479bb88c4fa85
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704847"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="a0c0b-102">ICorProfilerCallback::RemotingClientReceivingReply 方法</span><span class="sxs-lookup"><span data-stu-id="a0c0b-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>

<span data-ttu-id="a0c0b-103">通知分析工具，遠端呼叫的伺服器端部分已完成，而且用戶端現在已在接收及處理回復。</span><span class="sxs-lookup"><span data-stu-id="a0c0b-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c0b-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0c0b-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="a0c0b-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0c0b-105">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="a0c0b-106">在在下列情況下，會與 [ICorProfilerCallback：： RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) 中提供的值對應的值：</span><span class="sxs-lookup"><span data-stu-id="a0c0b-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="a0c0b-107">遠端 GUID cookie 為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="a0c0b-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="a0c0b-108">通道會成功傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="a0c0b-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="a0c0b-109">GUID cookie 在伺服器端進程中為作用中。</span><span class="sxs-lookup"><span data-stu-id="a0c0b-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="a0c0b-110">這可讓您輕鬆配對遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a0c0b-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="a0c0b-111">在值， `true` 如果呼叫是非同步，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="a0c0b-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c0b-112">需求</span><span class="sxs-lookup"><span data-stu-id="a0c0b-112">Requirements</span></span>  

 <span data-ttu-id="a0c0b-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c0b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c0b-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0c0b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0c0b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0c0b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0c0b-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c0b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c0b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c0b-117">See also</span></span>

- [<span data-ttu-id="a0c0b-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a0c0b-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
