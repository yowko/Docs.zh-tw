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
ms.openlocfilehash: 4ba04b1a4815587b40d03819fdac795dcc7f2c4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697268"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="9483d-102">ICorDebugManagedCallback2::ChangeConnection 方法</span><span class="sxs-lookup"><span data-stu-id="9483d-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>

<span data-ttu-id="9483d-103">通知偵錯工具，與指定之連接相關聯的工作集已變更。</span><span class="sxs-lookup"><span data-stu-id="9483d-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9483d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9483d-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9483d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9483d-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="9483d-106">在"ICorDebugProcess" 物件的指標，代表包含變更之連接的進程。</span><span class="sxs-lookup"><span data-stu-id="9483d-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="9483d-107">在變更之連接的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9483d-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9483d-108">備註</span><span class="sxs-lookup"><span data-stu-id="9483d-108">Remarks</span></span>  

 <span data-ttu-id="9483d-109">`ChangeConnection`回呼將會在下列其中一個情況下引發：</span><span class="sxs-lookup"><span data-stu-id="9483d-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="9483d-110">當偵錯工具附加至包含連接的進程時。</span><span class="sxs-lookup"><span data-stu-id="9483d-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="9483d-111">在此情況下，執行時間會為進程中的每個連接產生並分派 [ICorDebugManagedCallback2：： CreateConnection](icordebugmanagedcallback2-createconnection-method.md) 事件和 `ChangeConnection` 事件。</span><span class="sxs-lookup"><span data-stu-id="9483d-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="9483d-112">`ChangeConnection`每個現有的連接都會產生一個事件，不論連接的工作集自從建立之後是否已變更。</span><span class="sxs-lookup"><span data-stu-id="9483d-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="9483d-113">當主機在[裝載 API](../hosting/index.md)中呼叫[ICLRDebugManager：： SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md)時。</span><span class="sxs-lookup"><span data-stu-id="9483d-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
 <span data-ttu-id="9483d-114">偵錯工具應該掃描進程中的所有線程，以挑選新的變更。</span><span class="sxs-lookup"><span data-stu-id="9483d-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9483d-115">需求</span><span class="sxs-lookup"><span data-stu-id="9483d-115">Requirements</span></span>  

 <span data-ttu-id="9483d-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9483d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9483d-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9483d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9483d-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9483d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9483d-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9483d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9483d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9483d-120">See also</span></span>

- [<span data-ttu-id="9483d-121">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="9483d-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="9483d-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9483d-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
