---
title: IHostPolicyManager::OnTimeout 方法
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad1a9bc6b2e5c84f15cf0cf706504f18341f8584
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209173"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="3ea33-102">IHostPolicyManager::OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="3ea33-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="3ea33-103">會告知 common language runtime (CLR) 即將採取的動作呼叫所指定的主機[iclrpolicymanager:: Setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法以回應逾時。</span><span class="sxs-lookup"><span data-stu-id="3ea33-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea33-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ea33-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ea33-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ea33-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="3ea33-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，指出已逾時的作業的種類。</span><span class="sxs-lookup"><span data-stu-id="3ea33-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="3ea33-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示 CLR 的動作所花的逾時的回應。</span><span class="sxs-lookup"><span data-stu-id="3ea33-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ea33-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ea33-108">Return Value</span></span>  
  
|<span data-ttu-id="3ea33-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ea33-109">HRESULT</span></span>|<span data-ttu-id="3ea33-110">描述</span><span class="sxs-lookup"><span data-stu-id="3ea33-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ea33-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ea33-111">S_OK</span></span>|`OnTimeout` <span data-ttu-id="3ea33-112">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3ea33-112">returned successfully.</span></span>|  
|<span data-ttu-id="3ea33-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ea33-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ea33-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3ea33-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ea33-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ea33-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ea33-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3ea33-116">The call timed out.</span></span>|  
|<span data-ttu-id="3ea33-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ea33-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ea33-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3ea33-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ea33-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ea33-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ea33-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3ea33-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ea33-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ea33-121">E_FAIL</span></span>|<span data-ttu-id="3ea33-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="3ea33-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ea33-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="3ea33-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ea33-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3ea33-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ea33-125">需求</span><span class="sxs-lookup"><span data-stu-id="3ea33-125">Requirements</span></span>  
 <span data-ttu-id="3ea33-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea33-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea33-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ea33-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ea33-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3ea33-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3ea33-129">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3ea33-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3ea33-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ea33-130">See also</span></span>

- [<span data-ttu-id="3ea33-131">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="3ea33-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="3ea33-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="3ea33-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="3ea33-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="3ea33-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="3ea33-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="3ea33-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
