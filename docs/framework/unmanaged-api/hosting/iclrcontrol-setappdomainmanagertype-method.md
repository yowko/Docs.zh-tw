---
title: ICLRControl::SetAppDomainManagerType 方法
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79d3651bb949899681eac2e7d2ac49d9233ccc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531768"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="15aee-102">ICLRControl::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="15aee-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="15aee-103">設定型別衍生自<xref:System.AppDomainManager>做為應用程式定義域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="15aee-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15aee-104">語法</span><span class="sxs-lookup"><span data-stu-id="15aee-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15aee-105">參數</span><span class="sxs-lookup"><span data-stu-id="15aee-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="15aee-106">[in]要求的型別衍生自組件名稱<xref:System.AppDomainManager>實作。</span><span class="sxs-lookup"><span data-stu-id="15aee-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="15aee-107">[in]在實作型別的名稱`pwzAppDomainManagerAssembly`實作的功能參數<xref:System.AppDomainManager>。</span><span class="sxs-lookup"><span data-stu-id="15aee-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15aee-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="15aee-108">Return Value</span></span>  
  
|<span data-ttu-id="15aee-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15aee-109">HRESULT</span></span>|<span data-ttu-id="15aee-110">描述</span><span class="sxs-lookup"><span data-stu-id="15aee-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15aee-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="15aee-111">S_OK</span></span>|<span data-ttu-id="15aee-112">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="15aee-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="15aee-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15aee-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15aee-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="15aee-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15aee-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15aee-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15aee-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="15aee-116">The call timed out.</span></span>|  
|<span data-ttu-id="15aee-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15aee-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15aee-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="15aee-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15aee-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15aee-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15aee-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="15aee-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15aee-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15aee-121">E_FAIL</span></span>|<span data-ttu-id="15aee-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="15aee-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15aee-123">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="15aee-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15aee-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="15aee-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15aee-125">需求</span><span class="sxs-lookup"><span data-stu-id="15aee-125">Requirements</span></span>  
 <span data-ttu-id="15aee-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15aee-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15aee-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15aee-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15aee-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="15aee-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15aee-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15aee-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15aee-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15aee-130">See also</span></span>
- [<span data-ttu-id="15aee-131">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="15aee-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="15aee-132">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="15aee-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
