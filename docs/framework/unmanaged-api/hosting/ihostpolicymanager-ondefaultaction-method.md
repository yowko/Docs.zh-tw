---
title: "IHostPolicyManager::OnDefaultAction 方法"
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
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d1fded3d986e6505d0a321c47b03b5cdf9d881a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="b58fe-102">IHostPolicyManager::OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="b58fe-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="b58fe-103">通知主機 common language runtime (CLR) 即將採取的呼叫所設定的預設動作[iclrpolicymanager:: Setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)方法以回應執行緒中止或<xref:System.AppDomain>卸載。</span><span class="sxs-lookup"><span data-stu-id="b58fe-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="b58fe-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b58fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="b58fe-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="b58fe-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示 CLR 是否有回應的事件類型。</span><span class="sxs-lookup"><span data-stu-id="b58fe-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="b58fe-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示 CLR 正在以回應事件的動作。</span><span class="sxs-lookup"><span data-stu-id="b58fe-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b58fe-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b58fe-108">Return Value</span></span>  
  
|<span data-ttu-id="b58fe-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b58fe-109">HRESULT</span></span>|<span data-ttu-id="b58fe-110">描述</span><span class="sxs-lookup"><span data-stu-id="b58fe-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b58fe-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b58fe-111">S_OK</span></span>|<span data-ttu-id="b58fe-112">`OnDefaultAction`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b58fe-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="b58fe-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b58fe-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b58fe-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b58fe-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="b58fe-115">已成功</span><span class="sxs-lookup"><span data-stu-id="b58fe-115">successfully</span></span>|  
|<span data-ttu-id="b58fe-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b58fe-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b58fe-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b58fe-117">The call timed out.</span></span>|  
|<span data-ttu-id="b58fe-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b58fe-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b58fe-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b58fe-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b58fe-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b58fe-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b58fe-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b58fe-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b58fe-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b58fe-122">E_FAIL</span></span>|<span data-ttu-id="b58fe-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b58fe-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b58fe-124">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="b58fe-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b58fe-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b58fe-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b58fe-126">需求</span><span class="sxs-lookup"><span data-stu-id="b58fe-126">Requirements</span></span>  
 <span data-ttu-id="b58fe-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b58fe-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b58fe-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b58fe-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b58fe-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b58fe-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b58fe-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b58fe-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58fe-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="b58fe-131">See Also</span></span>  
 [<span data-ttu-id="b58fe-132">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="b58fe-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="b58fe-133">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="b58fe-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="b58fe-134">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b58fe-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="b58fe-135">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b58fe-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
