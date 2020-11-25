---
title: ICLRPolicyManager::SetTimeout 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
ms.openlocfilehash: 459c5bc0699487b62d5dcf76f1044faf53ebab8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732459"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="21325-102">ICLRPolicyManager::SetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="21325-102">ICLRPolicyManager::SetTimeout Method</span></span>

<span data-ttu-id="21325-103">設定指定之作業的超時值。</span><span class="sxs-lookup"><span data-stu-id="21325-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21325-104">語法</span><span class="sxs-lookup"><span data-stu-id="21325-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21325-105">參數</span><span class="sxs-lookup"><span data-stu-id="21325-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="21325-106">在其中一個 [EClrOperation](eclroperation-enumeration.md) 值，表示要設定 timeout 的 common language RUNTIME (CLR) 作業。</span><span class="sxs-lookup"><span data-stu-id="21325-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="21325-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="21325-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="21325-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="21325-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="21325-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="21325-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="21325-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="21325-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="21325-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="21325-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="21325-112">在新的超時值（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="21325-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="21325-113">無限期的值會導致作業永遠不會發生時間。</span><span class="sxs-lookup"><span data-stu-id="21325-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21325-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="21325-114">Return Value</span></span>  
  
|<span data-ttu-id="21325-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21325-115">HRESULT</span></span>|<span data-ttu-id="21325-116">描述</span><span class="sxs-lookup"><span data-stu-id="21325-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21325-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="21325-117">S_OK</span></span>|<span data-ttu-id="21325-118">`SetTimeout` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="21325-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="21325-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21325-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21325-120">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="21325-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21325-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21325-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21325-122">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="21325-122">The call timed out.</span></span>|  
|<span data-ttu-id="21325-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21325-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21325-124">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="21325-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21325-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21325-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21325-126">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="21325-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21325-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21325-127">E_FAIL</span></span>|<span data-ttu-id="21325-128">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="21325-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21325-129">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="21325-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21325-130">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="21325-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21325-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="21325-131">E_INVALIDARG</span></span>|<span data-ttu-id="21325-132">無法針對指定的設定 timeout `operation` ，或為提供的值無效 `operation` 。</span><span class="sxs-lookup"><span data-stu-id="21325-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21325-133">需求</span><span class="sxs-lookup"><span data-stu-id="21325-133">Requirements</span></span>  

 <span data-ttu-id="21325-134">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21325-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21325-135">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="21325-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21325-136">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="21325-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21325-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21325-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21325-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21325-138">See also</span></span>

- [<span data-ttu-id="21325-139">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="21325-139">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="21325-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="21325-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="21325-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="21325-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
