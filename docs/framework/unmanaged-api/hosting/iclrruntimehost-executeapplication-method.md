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
ms.openlocfilehash: 38938de335e5f0d7cb8051554c400f16df012362
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965349"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="d27e5-102">ICLRRuntimeHost::ExecuteApplication 方法</span><span class="sxs-lookup"><span data-stu-id="d27e5-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="d27e5-103">在以資訊清單為基礎的 ClickOnce 部署案例中使用, 以指定要在新的網域中啟動的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d27e5-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="d27e5-104">如需這些案例的詳細資訊, 請參閱[ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。</span><span class="sxs-lookup"><span data-stu-id="d27e5-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d27e5-105">語法</span><span class="sxs-lookup"><span data-stu-id="d27e5-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d27e5-106">參數</span><span class="sxs-lookup"><span data-stu-id="d27e5-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="d27e5-107">在應用程式的完整名稱, 如所定義<xref:System.ApplicationIdentity>。</span><span class="sxs-lookup"><span data-stu-id="d27e5-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="d27e5-108">在`ppwzManifestPaths`陣列中包含的字串數目。</span><span class="sxs-lookup"><span data-stu-id="d27e5-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="d27e5-109">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="d27e5-109">[in] Optional.</span></span> <span data-ttu-id="d27e5-110">字串陣列, 其中包含應用程式的資訊清單路徑。</span><span class="sxs-lookup"><span data-stu-id="d27e5-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="d27e5-111">在`ppwzActivationData`陣列中包含的字串數目。</span><span class="sxs-lookup"><span data-stu-id="d27e5-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="d27e5-112">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="d27e5-112">[in] Optional.</span></span> <span data-ttu-id="d27e5-113">字串陣列, 其中包含應用程式的啟用資料, 例如透過 Web 部署之應用程式的 URL 查詢字串部分。</span><span class="sxs-lookup"><span data-stu-id="d27e5-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="d27e5-114">脫銷從應用程式的進入點傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d27e5-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d27e5-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="d27e5-115">Return Value</span></span>  
  
|<span data-ttu-id="d27e5-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d27e5-116">HRESULT</span></span>|<span data-ttu-id="d27e5-117">描述</span><span class="sxs-lookup"><span data-stu-id="d27e5-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d27e5-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="d27e5-118">S_OK</span></span>|<span data-ttu-id="d27e5-119">`ExecuteApplication`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d27e5-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="d27e5-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d27e5-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d27e5-121">Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d27e5-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d27e5-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d27e5-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d27e5-123">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d27e5-123">The call timed out.</span></span>|  
|<span data-ttu-id="d27e5-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d27e5-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d27e5-125">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d27e5-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d27e5-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d27e5-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d27e5-127">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d27e5-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d27e5-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d27e5-128">E_FAIL</span></span>|<span data-ttu-id="d27e5-129">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d27e5-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d27e5-130">如果方法傳回 E_FAIL, 則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="d27e5-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d27e5-131">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d27e5-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d27e5-132">備註</span><span class="sxs-lookup"><span data-stu-id="d27e5-132">Remarks</span></span>  
 <span data-ttu-id="d27e5-133">`ExecuteApplication`是用來在新建立的應用程式域中啟動 ClickOnce 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d27e5-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="d27e5-134">`pReturnValue`輸出參數會設定為應用程式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d27e5-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="d27e5-135">如果您提供的值為 null `pReturnValue`, `ExecuteApplication`則不會失敗, 但不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="d27e5-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d27e5-136">在呼叫`ExecuteApplication`方法來啟動以資訊清單為基礎的應用程式之前, 請不要呼叫[Start 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d27e5-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="d27e5-137">如果先呼叫`ExecuteApplication`方法,方法呼叫將會失敗。 `Start`</span><span class="sxs-lookup"><span data-stu-id="d27e5-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d27e5-138">需求</span><span class="sxs-lookup"><span data-stu-id="d27e5-138">Requirements</span></span>  
 <span data-ttu-id="d27e5-139">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d27e5-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d27e5-140">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d27e5-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d27e5-141">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d27e5-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d27e5-142">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d27e5-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27e5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d27e5-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="d27e5-144">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="d27e5-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="d27e5-145">SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="d27e5-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="d27e5-146">逐步解說：依需求使用設計工具以 ClickOnce 部署 API 下載組件</span><span class="sxs-lookup"><span data-stu-id="d27e5-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
