---
title: IHostPolicyManager::OnFailure 方法
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3187a72d4b05be8d7b5b49df149366c4beb11d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779605"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="b8dbb-102">IHostPolicyManager::OnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="b8dbb-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="b8dbb-103">會告知 common language runtime (CLR) 即將採取的動作呼叫所指定的主機[iclrpolicymanager:: Setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)資源配置或回收失敗的回應中的方法。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8dbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8dbb-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8dbb-105">參數</span><span class="sxs-lookup"><span data-stu-id="b8dbb-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="b8dbb-106">[in]其中一個[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值，表示的失敗的回應 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="b8dbb-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)的值，指出動作 CLR 正在回應`failure`。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8dbb-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b8dbb-108">Return Value</span></span>  
  
|<span data-ttu-id="b8dbb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8dbb-109">HRESULT</span></span>|<span data-ttu-id="b8dbb-110">描述</span><span class="sxs-lookup"><span data-stu-id="b8dbb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8dbb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8dbb-111">S_OK</span></span>|<span data-ttu-id="b8dbb-112">`OnFailure` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b8dbb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b8dbb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b8dbb-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b8dbb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b8dbb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b8dbb-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-116">The call timed out.</span></span>|  
|<span data-ttu-id="b8dbb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b8dbb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b8dbb-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b8dbb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b8dbb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b8dbb-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b8dbb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8dbb-121">E_FAIL</span></span>|<span data-ttu-id="b8dbb-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b8dbb-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b8dbb-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8dbb-125">需求</span><span class="sxs-lookup"><span data-stu-id="b8dbb-125">Requirements</span></span>  
 <span data-ttu-id="b8dbb-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8dbb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8dbb-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8dbb-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8dbb-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b8dbb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8dbb-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8dbb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8dbb-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8dbb-130">See also</span></span>

- [<span data-ttu-id="b8dbb-131">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="b8dbb-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="b8dbb-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="b8dbb-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="b8dbb-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b8dbb-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="b8dbb-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b8dbb-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
