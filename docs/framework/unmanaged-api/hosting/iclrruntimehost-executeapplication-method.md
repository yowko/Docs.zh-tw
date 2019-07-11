---
title: ICLRRuntimeHost::ExecuteApplication 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8db6fd1296420011dcbfbbb0e5682f8a484dc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768808"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="d9e79-102">ICLRRuntimeHost::ExecuteApplication 方法</span><span class="sxs-lookup"><span data-stu-id="d9e79-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="d9e79-103">用於以指定要啟動新的網域中的應用程式的資訊清單為基礎的 ClickOnce 部署案例。</span><span class="sxs-lookup"><span data-stu-id="d9e79-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="d9e79-104">如需有關這些案例的詳細資訊，請參閱 < [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。</span><span class="sxs-lookup"><span data-stu-id="d9e79-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e79-105">語法</span><span class="sxs-lookup"><span data-stu-id="d9e79-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9e79-106">參數</span><span class="sxs-lookup"><span data-stu-id="d9e79-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="d9e79-107">[in]應用程式，針對所定義的完整名稱<xref:System.ApplicationIdentity>。</span><span class="sxs-lookup"><span data-stu-id="d9e79-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="d9e79-108">[in]中所包含的字串數目`ppwzManifestPaths`陣列。</span><span class="sxs-lookup"><span data-stu-id="d9e79-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="d9e79-109">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="d9e79-109">[in] Optional.</span></span> <span data-ttu-id="d9e79-110">字串陣列，其中包含應用程式資訊清單的路徑。</span><span class="sxs-lookup"><span data-stu-id="d9e79-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="d9e79-111">[in]中所包含的字串數目`ppwzActivationData`陣列。</span><span class="sxs-lookup"><span data-stu-id="d9e79-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="d9e79-112">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="d9e79-112">[in] Optional.</span></span> <span data-ttu-id="d9e79-113">字串陣列，其中包含應用程式的啟動資料，例如透過 Web 部署的應用程式的 URL 查詢字串部分。</span><span class="sxs-lookup"><span data-stu-id="d9e79-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="d9e79-114">[out]從應用程式的進入點傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d9e79-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e79-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9e79-115">Return Value</span></span>  
  
|<span data-ttu-id="d9e79-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9e79-116">HRESULT</span></span>|<span data-ttu-id="d9e79-117">說明</span><span class="sxs-lookup"><span data-stu-id="d9e79-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9e79-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9e79-118">S_OK</span></span>|<span data-ttu-id="d9e79-119">`ExecuteApplication` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d9e79-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="d9e79-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9e79-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9e79-121">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d9e79-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9e79-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9e79-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9e79-123">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d9e79-123">The call timed out.</span></span>|  
|<span data-ttu-id="d9e79-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9e79-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9e79-125">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d9e79-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9e79-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9e79-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9e79-127">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d9e79-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9e79-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9e79-128">E_FAIL</span></span>|<span data-ttu-id="d9e79-129">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d9e79-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9e79-130">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d9e79-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9e79-131">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d9e79-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9e79-132">備註</span><span class="sxs-lookup"><span data-stu-id="d9e79-132">Remarks</span></span>  
 <span data-ttu-id="d9e79-133">`ExecuteApplication` 用來啟動新建立的應用程式定義域中的 ClickOnce 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9e79-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="d9e79-134">`pReturnValue`輸出參數設定為應用程式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d9e79-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="d9e79-135">如果您提供的值為 null，如`pReturnValue`，`ExecuteApplication`不會失敗，但它不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="d9e79-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d9e79-136">請勿呼叫[啟動方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法之前呼叫`ExecuteApplication`方法，以啟用資訊清單為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9e79-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="d9e79-137">如果`Start`首先，呼叫方法`ExecuteApplication`方法呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="d9e79-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e79-138">需求</span><span class="sxs-lookup"><span data-stu-id="d9e79-138">Requirements</span></span>  
 <span data-ttu-id="d9e79-139">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e79-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e79-140">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9e79-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9e79-141">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d9e79-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e79-142">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e79-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e79-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9e79-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="d9e79-144">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="d9e79-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="d9e79-145">SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="d9e79-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="d9e79-146">逐步解說：依需求使用設計工具以 ClickOnce 部署 API 下載組件</span><span class="sxs-lookup"><span data-stu-id="d9e79-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
