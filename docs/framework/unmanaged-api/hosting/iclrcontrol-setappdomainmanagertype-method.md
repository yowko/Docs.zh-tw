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
ms.openlocfilehash: be778fed910b2cbdbf5e9ae7754abae437ef6bec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433730"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="c2536-102">ICLRControl::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="c2536-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="c2536-103">設定型別衍生自<xref:System.AppDomainManager>做為應用程式定義域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="c2536-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2536-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2536-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2536-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2536-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="c2536-106">[in]要求的型別衍生自組件名稱<xref:System.AppDomainManager>實作。</span><span class="sxs-lookup"><span data-stu-id="c2536-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="c2536-107">[in]實作中的型別名稱`pwzAppDomainManagerAssembly`實作的功能的參數<xref:System.AppDomainManager>。</span><span class="sxs-lookup"><span data-stu-id="c2536-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2536-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c2536-108">Return Value</span></span>  
  
|<span data-ttu-id="c2536-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2536-109">HRESULT</span></span>|<span data-ttu-id="c2536-110">描述</span><span class="sxs-lookup"><span data-stu-id="c2536-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2536-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2536-111">S_OK</span></span>|<span data-ttu-id="c2536-112">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c2536-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="c2536-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2536-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2536-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c2536-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2536-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2536-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2536-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c2536-116">The call timed out.</span></span>|  
|<span data-ttu-id="c2536-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2536-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2536-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c2536-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2536-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2536-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2536-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c2536-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2536-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2536-121">E_FAIL</span></span>|<span data-ttu-id="c2536-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c2536-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2536-123">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="c2536-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2536-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c2536-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2536-125">需求</span><span class="sxs-lookup"><span data-stu-id="c2536-125">Requirements</span></span>  
 <span data-ttu-id="c2536-126">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2536-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2536-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2536-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2536-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c2536-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2536-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2536-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2536-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2536-130">See Also</span></span>  
 [<span data-ttu-id="c2536-131">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="c2536-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c2536-132">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="c2536-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
