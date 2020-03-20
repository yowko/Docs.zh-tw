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
ms.openlocfilehash: 8d987614c1a5a2c90ccb3faa11c605767ae5cfda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178027"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="0f2b8-102">IHostPolicyManager::OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="0f2b8-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="0f2b8-103">通知主機通用語言運行時 （CLR） 即將採取由調用[ICLRPolicyManager：：：SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)方法以回應執行緒中止或<xref:System.AppDomain>卸載而設置的預設操作。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f2b8-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f2b8-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f2b8-105">參數</span><span class="sxs-lookup"><span data-stu-id="0f2b8-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="0f2b8-106">[在][EClr操作](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值之一，指示 CLR 正在回應的事件種類。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="0f2b8-107">[在][EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值之一，指示 CLR 為回應事件而執行的操作。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f2b8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0f2b8-108">Return Value</span></span>  
  
|<span data-ttu-id="0f2b8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f2b8-109">HRESULT</span></span>|<span data-ttu-id="0f2b8-110">描述</span><span class="sxs-lookup"><span data-stu-id="0f2b8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f2b8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f2b8-111">S_OK</span></span>|<span data-ttu-id="0f2b8-112">`OnDefaultAction`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="0f2b8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f2b8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f2b8-114">CLR 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="0f2b8-115">成功</span><span class="sxs-lookup"><span data-stu-id="0f2b8-115">successfully</span></span>|  
|<span data-ttu-id="0f2b8-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f2b8-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f2b8-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-117">The call timed out.</span></span>|  
|<span data-ttu-id="0f2b8-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f2b8-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f2b8-119">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f2b8-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f2b8-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f2b8-121">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f2b8-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f2b8-122">E_FAIL</span></span>|<span data-ttu-id="0f2b8-123">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f2b8-124">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f2b8-125">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f2b8-126">需求</span><span class="sxs-lookup"><span data-stu-id="0f2b8-126">Requirements</span></span>  
 <span data-ttu-id="0f2b8-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f2b8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f2b8-128">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f2b8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f2b8-129">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0f2b8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f2b8-130">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f2b8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f2b8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f2b8-131">See also</span></span>

- [<span data-ttu-id="0f2b8-132">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="0f2b8-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="0f2b8-133">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="0f2b8-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="0f2b8-134">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0f2b8-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="0f2b8-135">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0f2b8-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
