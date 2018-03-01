---
title: "IHostPolicyManager::OnTimeout 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b8c29bc281b64368e8b310e2b13f3fcb1bdc6ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="0ad28-102">IHostPolicyManager::OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="0ad28-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="0ad28-103">通知 common language runtime (CLR) 即將採取的動作呼叫所指定的主機[iclrpolicymanager:: Setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法以回應逾時。</span><span class="sxs-lookup"><span data-stu-id="0ad28-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad28-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ad28-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ad28-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ad28-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="0ad28-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示作業已逾時的類型。</span><span class="sxs-lookup"><span data-stu-id="0ad28-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="0ad28-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出動作 CLR 所花的回應逾時。</span><span class="sxs-lookup"><span data-stu-id="0ad28-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ad28-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0ad28-108">Return Value</span></span>  
  
|<span data-ttu-id="0ad28-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ad28-109">HRESULT</span></span>|<span data-ttu-id="0ad28-110">描述</span><span class="sxs-lookup"><span data-stu-id="0ad28-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ad28-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ad28-111">S_OK</span></span>|<span data-ttu-id="0ad28-112">`OnTimeout`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0ad28-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="0ad28-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ad28-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ad28-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ad28-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ad28-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ad28-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ad28-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0ad28-116">The call timed out.</span></span>|  
|<span data-ttu-id="0ad28-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ad28-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ad28-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0ad28-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ad28-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ad28-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ad28-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0ad28-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ad28-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ad28-121">E_FAIL</span></span>|<span data-ttu-id="0ad28-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0ad28-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ad28-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="0ad28-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ad28-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0ad28-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ad28-125">需求</span><span class="sxs-lookup"><span data-stu-id="0ad28-125">Requirements</span></span>  
 <span data-ttu-id="0ad28-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad28-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ad28-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ad28-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ad28-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0ad28-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ad28-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ad28-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad28-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad28-130">See Also</span></span>  
 [<span data-ttu-id="0ad28-131">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="0ad28-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="0ad28-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="0ad28-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="0ad28-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0ad28-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="0ad28-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0ad28-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
