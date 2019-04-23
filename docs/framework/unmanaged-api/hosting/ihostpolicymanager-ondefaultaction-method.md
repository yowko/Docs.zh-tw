---
title: IHostPolicyManager::OnDefaultAction 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45167a2b358b9a7a39390c07f552aa3f3dabce4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108650"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="50dc7-102">IHostPolicyManager::OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="50dc7-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="50dc7-103">會告知 common language runtime (CLR) 即將採取預設動作的呼叫所設定的主機[iclrpolicymanager:: Setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)方法以回應執行緒中止或<xref:System.AppDomain>卸載。</span><span class="sxs-lookup"><span data-stu-id="50dc7-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50dc7-104">語法</span><span class="sxs-lookup"><span data-stu-id="50dc7-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50dc7-105">參數</span><span class="sxs-lookup"><span data-stu-id="50dc7-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="50dc7-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示 CLR 正在回應的事件的種類。</span><span class="sxs-lookup"><span data-stu-id="50dc7-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="50dc7-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示 CLR 正在以回應事件的動作。</span><span class="sxs-lookup"><span data-stu-id="50dc7-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50dc7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="50dc7-108">Return Value</span></span>  
  
|<span data-ttu-id="50dc7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50dc7-109">HRESULT</span></span>|<span data-ttu-id="50dc7-110">描述</span><span class="sxs-lookup"><span data-stu-id="50dc7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50dc7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="50dc7-111">S_OK</span></span>|<span data-ttu-id="50dc7-112">`OnDefaultAction` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="50dc7-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="50dc7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50dc7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50dc7-114">不到程序中，載入 CLR 或 CLR 中不能在其中執行 managed 程式碼，或處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="50dc7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="50dc7-115">已成功</span><span class="sxs-lookup"><span data-stu-id="50dc7-115">successfully</span></span>|  
|<span data-ttu-id="50dc7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50dc7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50dc7-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="50dc7-117">The call timed out.</span></span>|  
|<span data-ttu-id="50dc7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50dc7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50dc7-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="50dc7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50dc7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50dc7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50dc7-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="50dc7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50dc7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50dc7-122">E_FAIL</span></span>|<span data-ttu-id="50dc7-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="50dc7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50dc7-124">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="50dc7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50dc7-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="50dc7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50dc7-126">需求</span><span class="sxs-lookup"><span data-stu-id="50dc7-126">Requirements</span></span>  
 <span data-ttu-id="50dc7-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50dc7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50dc7-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50dc7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50dc7-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="50dc7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50dc7-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50dc7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50dc7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50dc7-131">See also</span></span>

- [<span data-ttu-id="50dc7-132">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="50dc7-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="50dc7-133">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="50dc7-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="50dc7-134">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="50dc7-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="50dc7-135">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="50dc7-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
