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
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175131"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="057e8-102">ICorProfilerCallback::RemotingClientReceivingReply 方法</span><span class="sxs-lookup"><span data-stu-id="057e8-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="057e8-103">通知探測器，遠端呼叫的伺服器端部分已完成，用戶端正在接收並即將處理答覆。</span><span class="sxs-lookup"><span data-stu-id="057e8-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="057e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="057e8-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="057e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="057e8-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="057e8-106">[在]與[ICorProfiler 回撥](icorprofilercallback-remotingserversendingreply-method.md)中提供的值相對應的值：：在以下條件下重新發送伺服器：</span><span class="sxs-lookup"><span data-stu-id="057e8-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="057e8-107">正在啟動 GUID Cookie。</span><span class="sxs-lookup"><span data-stu-id="057e8-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="057e8-108">通道成功傳輸消息。</span><span class="sxs-lookup"><span data-stu-id="057e8-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="057e8-109">GUID Cookie 在伺服器端進程中處於活動狀態。</span><span class="sxs-lookup"><span data-stu-id="057e8-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="057e8-110">這允許輕鬆配對遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="057e8-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="057e8-111">[在]`true`如果調用是非同步，則為值;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="057e8-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="057e8-112">需求</span><span class="sxs-lookup"><span data-stu-id="057e8-112">Requirements</span></span>  
 <span data-ttu-id="057e8-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="057e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="057e8-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="057e8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="057e8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="057e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="057e8-116">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="057e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057e8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="057e8-117">See also</span></span>

- [<span data-ttu-id="057e8-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="057e8-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
