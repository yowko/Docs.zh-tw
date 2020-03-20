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
ms.openlocfilehash: d5b5fa5198ae2c0bba30ae0f8d6d3834f2891672
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178011"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="115a7-102">IHostPolicyManager::OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="115a7-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="115a7-103">通知主機通用語言運行時 （CLR） 即將執行調用[ICLRPolicyManager 指定的操作：：SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法以回應超時。</span><span class="sxs-lookup"><span data-stu-id="115a7-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="115a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="115a7-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="115a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="115a7-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="115a7-106">[在][EClr操作](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值之一，指示超時的操作類型。</span><span class="sxs-lookup"><span data-stu-id="115a7-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="115a7-107">[在][EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值之一，指示 CLR 為回應超時而執行的操作。</span><span class="sxs-lookup"><span data-stu-id="115a7-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="115a7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="115a7-108">Return Value</span></span>  
  
|<span data-ttu-id="115a7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="115a7-109">HRESULT</span></span>|<span data-ttu-id="115a7-110">描述</span><span class="sxs-lookup"><span data-stu-id="115a7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="115a7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="115a7-111">S_OK</span></span>|<span data-ttu-id="115a7-112">`OnTimeout`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="115a7-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="115a7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="115a7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="115a7-114">CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="115a7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="115a7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="115a7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="115a7-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="115a7-116">The call timed out.</span></span>|  
|<span data-ttu-id="115a7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="115a7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="115a7-118">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="115a7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="115a7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="115a7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="115a7-120">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="115a7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="115a7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="115a7-121">E_FAIL</span></span>|<span data-ttu-id="115a7-122">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="115a7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="115a7-123">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="115a7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="115a7-124">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="115a7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="115a7-125">需求</span><span class="sxs-lookup"><span data-stu-id="115a7-125">Requirements</span></span>  
 <span data-ttu-id="115a7-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="115a7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="115a7-127">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="115a7-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="115a7-128">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="115a7-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="115a7-129">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="115a7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115a7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="115a7-130">See also</span></span>

- [<span data-ttu-id="115a7-131">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="115a7-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="115a7-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="115a7-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="115a7-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="115a7-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="115a7-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="115a7-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
