---
title: ICorDebugManagedCallback2::ChangeConnection 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 4558074bc23334bd697461a00ccb31db3e3fe397
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130603"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="19ac5-102">ICorDebugManagedCallback2::ChangeConnection 方法</span><span class="sxs-lookup"><span data-stu-id="19ac5-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="19ac5-103">通知偵錯工具與指定的連接相關聯的工作集已變更。</span><span class="sxs-lookup"><span data-stu-id="19ac5-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ac5-104">語法</span><span class="sxs-lookup"><span data-stu-id="19ac5-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19ac5-105">參數</span><span class="sxs-lookup"><span data-stu-id="19ac5-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="19ac5-106">在"ICorDebugProcess" 物件的指標，表示包含已變更之連接的進程。</span><span class="sxs-lookup"><span data-stu-id="19ac5-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="19ac5-107">在已變更之連接的識別碼。</span><span class="sxs-lookup"><span data-stu-id="19ac5-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19ac5-108">備註</span><span class="sxs-lookup"><span data-stu-id="19ac5-108">Remarks</span></span>  
 <span data-ttu-id="19ac5-109">在下列任一情況下，將會引發 `ChangeConnection` 回呼：</span><span class="sxs-lookup"><span data-stu-id="19ac5-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="19ac5-110">當偵錯工具附加至包含連接的進程時。</span><span class="sxs-lookup"><span data-stu-id="19ac5-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="19ac5-111">在此情況下，執行時間會針對進程中的每個連接產生並分派[ICorDebugManagedCallback2：： CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)事件和 `ChangeConnection` 事件。</span><span class="sxs-lookup"><span data-stu-id="19ac5-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="19ac5-112">會針對每個現有的連接產生 `ChangeConnection` 事件，而不論該連線的工作集是在建立後是否已變更。</span><span class="sxs-lookup"><span data-stu-id="19ac5-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="19ac5-113">當主機在[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)中呼叫[ICLRDebugManager：： SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)時。</span><span class="sxs-lookup"><span data-stu-id="19ac5-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="19ac5-114">偵錯工具應該掃描進程中的所有線程，以挑選新的變更。</span><span class="sxs-lookup"><span data-stu-id="19ac5-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19ac5-115">需求</span><span class="sxs-lookup"><span data-stu-id="19ac5-115">Requirements</span></span>  
 <span data-ttu-id="19ac5-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19ac5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19ac5-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19ac5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19ac5-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19ac5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19ac5-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19ac5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ac5-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="19ac5-120">See also</span></span>

- [<span data-ttu-id="19ac5-121">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="19ac5-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="19ac5-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="19ac5-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
