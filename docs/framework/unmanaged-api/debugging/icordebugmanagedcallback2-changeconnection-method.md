---
title: "ICorDebugManagedCallback2::ChangeConnection 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ba7e84c11f2fc8619b7046e222a742ee3298554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="b1376-102">ICorDebugManagedCallback2::ChangeConnection 方法</span><span class="sxs-lookup"><span data-stu-id="b1376-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="b1376-103">告知偵錯工具使用指定的連接相關聯的工作集，已變更。</span><span class="sxs-lookup"><span data-stu-id="b1376-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1376-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1376-104">Syntax</span></span>  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1376-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1376-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="b1376-106">[in]代表程序包含變更的連接 」 ICorDebugProcess 」 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="b1376-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="b1376-107">[in]變更連線的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b1376-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1376-108">備註</span><span class="sxs-lookup"><span data-stu-id="b1376-108">Remarks</span></span>  
 <span data-ttu-id="b1376-109">A`ChangeConnection`回呼將會引發在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="b1376-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="b1376-110">當偵錯工具附加至處理序，包含連線。</span><span class="sxs-lookup"><span data-stu-id="b1376-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="b1376-111">在此情況下，執行階段將會產生並分派[icordebugmanagedcallback2:: Createconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)事件和`ChangeConnection`程序中每個連接的事件。</span><span class="sxs-lookup"><span data-stu-id="b1376-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="b1376-112">A`ChangeConnection`的每個現有的連接，不論是否已變更該連線的工作集建立後會產生事件。</span><span class="sxs-lookup"><span data-stu-id="b1376-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
-   <span data-ttu-id="b1376-113">當主機呼叫[iclrdebugmanager:: Setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)中[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b1376-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="b1376-114">偵錯工具應該掃描取得最新變更的程序中的所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="b1376-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1376-115">需求</span><span class="sxs-lookup"><span data-stu-id="b1376-115">Requirements</span></span>  
 <span data-ttu-id="b1376-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1376-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1376-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1376-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1376-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1376-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1376-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1376-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1376-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1376-120">See Also</span></span>  
 [<span data-ttu-id="b1376-121">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="b1376-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="b1376-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b1376-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
