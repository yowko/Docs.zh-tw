---
title: IHostIoCompletionManager::CloseIoCompletionPort 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32a7c8b1c1c61eddb18ade1e77af5ea973fbaadc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760125"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="e54e9-102">IHostIoCompletionManager::CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="e54e9-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="e54e9-103">要求主機關閉開啟的先前呼叫的連接埠[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e54e9-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e54e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e54e9-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e54e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="e54e9-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="e54e9-106">[in]若要關閉的連接埠的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e54e9-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e54e9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e54e9-107">Return Value</span></span>  
  
|<span data-ttu-id="e54e9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e54e9-108">HRESULT</span></span>|<span data-ttu-id="e54e9-109">描述</span><span class="sxs-lookup"><span data-stu-id="e54e9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e54e9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e54e9-110">S_OK</span></span>|<span data-ttu-id="e54e9-111">`CloseIoCompletionPort` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e54e9-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="e54e9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e54e9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e54e9-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e54e9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e54e9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e54e9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e54e9-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e54e9-115">The call timed out.</span></span>|  
|<span data-ttu-id="e54e9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e54e9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e54e9-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e54e9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e54e9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e54e9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e54e9-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e54e9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e54e9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e54e9-120">E_FAIL</span></span>|<span data-ttu-id="e54e9-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e54e9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e54e9-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="e54e9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e54e9-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e54e9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e54e9-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e54e9-124">E_INVALIDARG</span></span>|<span data-ttu-id="e54e9-125">傳遞了無效的連接埠的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e54e9-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e54e9-126">備註</span><span class="sxs-lookup"><span data-stu-id="e54e9-126">Remarks</span></span>  
 <span data-ttu-id="e54e9-127">`hPort` 必須是由先前呼叫所建立的連接埠的控制代碼`CreateIoCompletionPort`。</span><span class="sxs-lookup"><span data-stu-id="e54e9-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e54e9-128">需求</span><span class="sxs-lookup"><span data-stu-id="e54e9-128">Requirements</span></span>  
 <span data-ttu-id="e54e9-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e54e9-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e54e9-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e54e9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e54e9-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e54e9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e54e9-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e54e9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54e9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e54e9-133">See also</span></span>

- [<span data-ttu-id="e54e9-134">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="e54e9-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e54e9-135">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="e54e9-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
