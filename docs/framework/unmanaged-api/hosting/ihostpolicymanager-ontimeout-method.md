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
ms.openlocfilehash: e8a14dd6a6d196cea9caa6be669b2b75a167eca8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141099"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="5c9e4-102">IHostPolicyManager::OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="5c9e4-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="5c9e4-103">通知主機 common language runtime （CLR）即將採取[ICLRPolicyManager：： SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法呼叫所指定的動作，以回應超時。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c9e4-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c9e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c9e4-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="5c9e4-106">在其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示已超時的作業種類。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="5c9e4-107">在其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示 CLR 為了回應超時而採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c9e4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="5c9e4-108">Return Value</span></span>  
  
|<span data-ttu-id="5c9e4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c9e4-109">HRESULT</span></span>|<span data-ttu-id="5c9e4-110">描述</span><span class="sxs-lookup"><span data-stu-id="5c9e4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c9e4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c9e4-111">S_OK</span></span>|<span data-ttu-id="5c9e4-112">已成功傳回 `OnTimeout`。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="5c9e4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c9e4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c9e4-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c9e4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c9e4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c9e4-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c9e4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c9e4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c9e4-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c9e4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c9e4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c9e4-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c9e4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c9e4-121">E_FAIL</span></span>|<span data-ttu-id="5c9e4-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c9e4-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c9e4-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c9e4-125">需求</span><span class="sxs-lookup"><span data-stu-id="5c9e4-125">Requirements</span></span>  
 <span data-ttu-id="5c9e4-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c9e4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9e4-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5c9e4-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c9e4-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5c9e4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c9e4-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9e4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9e4-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c9e4-130">See also</span></span>

- [<span data-ttu-id="5c9e4-131">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="5c9e4-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="5c9e4-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="5c9e4-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="5c9e4-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="5c9e4-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="5c9e4-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="5c9e4-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
