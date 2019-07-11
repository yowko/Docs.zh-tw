---
title: ICorDebugManagedCallback2::CreateConnection 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d0fc0c65d6c479ee4bf7bf527ee33615d53084
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761174"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="396ef-102">ICorDebugManagedCallback2::CreateConnection 方法</span><span class="sxs-lookup"><span data-stu-id="396ef-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="396ef-103">告知偵錯工具已建立的新的連線。</span><span class="sxs-lookup"><span data-stu-id="396ef-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="396ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="396ef-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="396ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="396ef-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="396ef-106">[in]代表程序的連接原先建立"ICorDebugProcess 」 物件的指標</span><span class="sxs-lookup"><span data-stu-id="396ef-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="396ef-107">[in]新的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="396ef-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="396ef-108">[in]新的連接名稱指標。</span><span class="sxs-lookup"><span data-stu-id="396ef-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="396ef-109">備註</span><span class="sxs-lookup"><span data-stu-id="396ef-109">Remarks</span></span>  
 <span data-ttu-id="396ef-110">A`CreateConnection`回呼會在下列情況下引發：</span><span class="sxs-lookup"><span data-stu-id="396ef-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="396ef-111">當偵錯工具附加至包含連線的處理序。</span><span class="sxs-lookup"><span data-stu-id="396ef-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="396ef-112">在此情況下，執行階段會產生，並分派`CreateConnection`事件和[ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)程序中每個連接的事件。</span><span class="sxs-lookup"><span data-stu-id="396ef-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="396ef-113">當主機呼叫[iclrdebugmanager:: Beginconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)中[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="396ef-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="396ef-114">需求</span><span class="sxs-lookup"><span data-stu-id="396ef-114">Requirements</span></span>  
 <span data-ttu-id="396ef-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="396ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="396ef-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="396ef-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="396ef-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="396ef-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="396ef-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="396ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396ef-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="396ef-119">See also</span></span>

- [<span data-ttu-id="396ef-120">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="396ef-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="396ef-121">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="396ef-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
