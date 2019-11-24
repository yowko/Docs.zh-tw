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
ms.openlocfilehash: 2c2eb7d0dc04d813b1ce91fb1acf4b171f244592
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445756"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="cf724-102">ICorProfilerCallback::RemotingServerReceivingMessage 方法</span><span class="sxs-lookup"><span data-stu-id="cf724-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="cf724-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span><span class="sxs-lookup"><span data-stu-id="cf724-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf724-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf724-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf724-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf724-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="cf724-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span><span class="sxs-lookup"><span data-stu-id="cf724-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="cf724-107">Remoting GUID cookies are active.</span><span class="sxs-lookup"><span data-stu-id="cf724-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="cf724-108">The channel succeeds in transmitting the message.</span><span class="sxs-lookup"><span data-stu-id="cf724-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="cf724-109">GUID cookies are active on the client-side process.</span><span class="sxs-lookup"><span data-stu-id="cf724-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="cf724-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span><span class="sxs-lookup"><span data-stu-id="cf724-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="cf724-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="cf724-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf724-112">備註</span><span class="sxs-lookup"><span data-stu-id="cf724-112">Remarks</span></span>  
 <span data-ttu-id="cf724-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span><span class="sxs-lookup"><span data-stu-id="cf724-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf724-114">需求</span><span class="sxs-lookup"><span data-stu-id="cf724-114">Requirements</span></span>  
 <span data-ttu-id="cf724-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf724-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf724-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf724-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf724-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf724-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf724-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf724-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf724-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf724-119">See also</span></span>

- [<span data-ttu-id="cf724-120">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cf724-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
