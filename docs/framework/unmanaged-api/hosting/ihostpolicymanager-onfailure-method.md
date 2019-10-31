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
ms.openlocfilehash: 3bb65d747d7cdc81bd534108f6189eb1c94e3b15
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128549"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="b9e8d-102">IHostPolicyManager::OnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="b9e8d-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="b9e8d-103">通知主機 common language runtime （CLR）即將採取[ICLRPolicyManager：： SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)方法呼叫所指定的動作，以回應資源配置或回收失敗。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9e8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9e8d-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9e8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9e8d-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="b9e8d-106">在其中一個[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值，表示 CLR 回應的失敗類型。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="b9e8d-107">在其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示 CLR 為了回應 `failure`而採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9e8d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9e8d-108">Return Value</span></span>  
  
|<span data-ttu-id="b9e8d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9e8d-109">HRESULT</span></span>|<span data-ttu-id="b9e8d-110">描述</span><span class="sxs-lookup"><span data-stu-id="b9e8d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9e8d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9e8d-111">S_OK</span></span>|<span data-ttu-id="b9e8d-112">已成功傳回 `OnFailure`。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b9e8d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9e8d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9e8d-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9e8d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9e8d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9e8d-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-116">The call timed out.</span></span>|  
|<span data-ttu-id="b9e8d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9e8d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9e8d-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9e8d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9e8d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9e8d-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9e8d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9e8d-121">E_FAIL</span></span>|<span data-ttu-id="b9e8d-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9e8d-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9e8d-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9e8d-125">需求</span><span class="sxs-lookup"><span data-stu-id="b9e8d-125">Requirements</span></span>  
 <span data-ttu-id="b9e8d-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e8d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9e8d-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b9e8d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9e8d-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b9e8d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9e8d-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9e8d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e8d-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9e8d-130">See also</span></span>

- [<span data-ttu-id="b9e8d-131">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="b9e8d-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="b9e8d-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="b9e8d-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="b9e8d-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b9e8d-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="b9e8d-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b9e8d-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
