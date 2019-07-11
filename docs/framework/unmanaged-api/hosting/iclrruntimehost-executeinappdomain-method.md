---
title: ICLRRuntimeHost::ExecuteInAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314ffb143e99f9490bcd4a6489f2afed314b7c2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768769"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="4b5c1-102">ICLRRuntimeHost::ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="4b5c1-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="4b5c1-103">指定<xref:System.AppDomain>要執行指定的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b5c1-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b5c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b5c1-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="4b5c1-106">[in]數字識別碼<xref:System.AppDomain>要執行指定的方法。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="4b5c1-107">[in]執行位於指定之函式指標<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="4b5c1-108">[in]不透明的呼叫端配置的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="4b5c1-109">這個參數會傳遞由 common language runtime (CLR) 中，網域回呼。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="4b5c1-110">它不是執行階段受管理的堆積記憶體;配置和存留期的這個記憶體是由呼叫者控制的。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b5c1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b5c1-111">Return Value</span></span>  
  
|<span data-ttu-id="4b5c1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b5c1-112">HRESULT</span></span>|<span data-ttu-id="4b5c1-113">描述</span><span class="sxs-lookup"><span data-stu-id="4b5c1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b5c1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b5c1-114">S_OK</span></span>|<span data-ttu-id="4b5c1-115">`ExecuteInAppDomain` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="4b5c1-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b5c1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b5c1-117">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b5c1-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b5c1-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b5c1-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-119">The call timed out.</span></span>|  
|<span data-ttu-id="4b5c1-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b5c1-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b5c1-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b5c1-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b5c1-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b5c1-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b5c1-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b5c1-124">E_FAIL</span></span>|<span data-ttu-id="4b5c1-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b5c1-126">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b5c1-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b5c1-128">備註</span><span class="sxs-lookup"><span data-stu-id="4b5c1-128">Remarks</span></span>  
 <span data-ttu-id="4b5c1-129">`ExecuteInAppDomain` 可讓主機控制管理 over<xref:System.AppDomain>應該在執行指定的 managed 的方法。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="4b5c1-130">您可以取得應用程式定義域的識別項，對應至值的值<xref:System.AppDomain.Id%2A>屬性，藉由呼叫[GetCurrentAppDomainId 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b5c1-131">需求</span><span class="sxs-lookup"><span data-stu-id="4b5c1-131">Requirements</span></span>  
 <span data-ttu-id="4b5c1-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b5c1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b5c1-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b5c1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b5c1-134">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4b5c1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b5c1-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b5c1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5c1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b5c1-136">See also</span></span>

- [<span data-ttu-id="4b5c1-137">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="4b5c1-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
