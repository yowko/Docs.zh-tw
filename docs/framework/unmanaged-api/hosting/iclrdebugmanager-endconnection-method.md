---
title: ICLRDebugManager::EndConnection 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: d6f22d6185f4063078463043a6ffd46e56289267
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719849"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="b8d15-102">ICLRDebugManager::EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="b8d15-102">ICLRDebugManager::EndConnection Method</span></span>

<span data-ttu-id="b8d15-103">移除工作清單與識別碼和易記名稱之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="b8d15-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d15-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8d15-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8d15-105">參數</span><span class="sxs-lookup"><span data-stu-id="b8d15-105">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="b8d15-106">在連接的主機特定識別碼以及 common language runtime (CLR) 工作的相關清單。</span><span class="sxs-lookup"><span data-stu-id="b8d15-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8d15-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b8d15-107">Return Value</span></span>  
  
|<span data-ttu-id="b8d15-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8d15-108">HRESULT</span></span>|<span data-ttu-id="b8d15-109">描述</span><span class="sxs-lookup"><span data-stu-id="b8d15-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8d15-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8d15-110">S_OK</span></span>|<span data-ttu-id="b8d15-111">`EndConnection` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="b8d15-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="b8d15-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b8d15-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b8d15-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b8d15-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b8d15-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b8d15-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b8d15-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="b8d15-115">The call timed out.</span></span>|  
|<span data-ttu-id="b8d15-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b8d15-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b8d15-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b8d15-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b8d15-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b8d15-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b8d15-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="b8d15-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b8d15-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8d15-120">E_FAIL</span></span>|<span data-ttu-id="b8d15-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b8d15-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b8d15-122">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="b8d15-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b8d15-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b8d15-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b8d15-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b8d15-124">E_INVALIDARG</span></span>|<span data-ttu-id="b8d15-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) 從未使用 `dwConnectionId` 或 `dwConnectionId` 為零來呼叫。</span><span class="sxs-lookup"><span data-stu-id="b8d15-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8d15-126">備註</span><span class="sxs-lookup"><span data-stu-id="b8d15-126">Remarks</span></span>  

 <span data-ttu-id="b8d15-127">[ICLRDebugManager](iclrdebugmanager-interface.md) 提供三種方法：、 `BeginConnection` [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)和 `EndConnection` ，以便將工作清單與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b8d15-127">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b8d15-128">您必須針對每一組工作以特定順序呼叫這三種方法。</span><span class="sxs-lookup"><span data-stu-id="b8d15-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="b8d15-129">`BeginConnection` 先呼叫，以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="b8d15-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="b8d15-130">`SetConnectionTasks` 會在旁邊呼叫，以提供與該連接相關聯的工作集。</span><span class="sxs-lookup"><span data-stu-id="b8d15-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="b8d15-131">`EndConnection` 最後會呼叫，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b8d15-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8d15-132">需求</span><span class="sxs-lookup"><span data-stu-id="b8d15-132">Requirements</span></span>  

 <span data-ttu-id="b8d15-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8d15-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8d15-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b8d15-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8d15-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b8d15-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8d15-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d15-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d15-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d15-137">See also</span></span>

- [<span data-ttu-id="b8d15-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b8d15-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b8d15-139">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="b8d15-139">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="b8d15-140">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="b8d15-140">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="b8d15-141">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="b8d15-141">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="b8d15-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="b8d15-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
