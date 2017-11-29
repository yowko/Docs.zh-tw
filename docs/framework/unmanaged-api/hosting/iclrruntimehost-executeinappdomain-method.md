---
title: "ICLRRuntimeHost::ExecuteInAppDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da6e9b52c0ea6f2935aad70779e159db91a4f501
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="b22b6-102">ICLRRuntimeHost::ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="b22b6-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="b22b6-103">指定<xref:System.AppDomain>，以執行指定的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b22b6-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b22b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="b22b6-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b22b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="b22b6-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="b22b6-106">[in]數值識別碼<xref:System.AppDomain>執行指定的方法。</span><span class="sxs-lookup"><span data-stu-id="b22b6-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="b22b6-107">[in]執行位於指定的函式的指標<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="b22b6-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="b22b6-108">[in]不透明的呼叫端配置記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="b22b6-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="b22b6-109">這個參數會由 common language runtime (CLR) 傳遞給網域回呼。</span><span class="sxs-lookup"><span data-stu-id="b22b6-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="b22b6-110">它不是執行階段 managed 堆積的記憶體配置和存留期這個記憶體是由呼叫者控制。</span><span class="sxs-lookup"><span data-stu-id="b22b6-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b22b6-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="b22b6-111">Return Value</span></span>  
  
|<span data-ttu-id="b22b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b22b6-112">HRESULT</span></span>|<span data-ttu-id="b22b6-113">描述</span><span class="sxs-lookup"><span data-stu-id="b22b6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b22b6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b22b6-114">S_OK</span></span>|<span data-ttu-id="b22b6-115">`ExecuteInAppDomain`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b22b6-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="b22b6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b22b6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b22b6-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b22b6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b22b6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b22b6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b22b6-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b22b6-119">The call timed out.</span></span>|  
|<span data-ttu-id="b22b6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b22b6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b22b6-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b22b6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b22b6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b22b6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b22b6-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b22b6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b22b6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b22b6-124">E_FAIL</span></span>|<span data-ttu-id="b22b6-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b22b6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b22b6-126">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="b22b6-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b22b6-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b22b6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b22b6-128">備註</span><span class="sxs-lookup"><span data-stu-id="b22b6-128">Remarks</span></span>  
 <span data-ttu-id="b22b6-129">`ExecuteInAppDomain`可讓主機以控制管理 over<xref:System.AppDomain>應該在執行指定的 managed 的方法。</span><span class="sxs-lookup"><span data-stu-id="b22b6-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="b22b6-130">您可以取得的應用程式定義域的識別項，會對應至值的值<xref:System.AppDomain.Id%2A>屬性，藉由呼叫[GetCurrentAppDomainId 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b22b6-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b22b6-131">需求</span><span class="sxs-lookup"><span data-stu-id="b22b6-131">Requirements</span></span>  
 <span data-ttu-id="b22b6-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b22b6-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b22b6-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b22b6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b22b6-134">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b22b6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b22b6-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b22b6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b22b6-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b22b6-136">See Also</span></span>  
 [<span data-ttu-id="b22b6-137">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b22b6-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
