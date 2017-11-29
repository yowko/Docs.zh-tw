---
title: "ICLRHostProtectionManager::SetProtectedCategories 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetProtectedCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 984a88a9b75a03f421f1dd3f834665fee932876a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="de489-102">ICLRHostProtectionManager::SetProtectedCategories 方法</span><span class="sxs-lookup"><span data-stu-id="de489-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="de489-103">指定的 managed 的類型和成員的類別應該禁止在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="de489-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de489-104">語法</span><span class="sxs-lookup"><span data-stu-id="de489-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de489-105">參數</span><span class="sxs-lookup"><span data-stu-id="de489-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="de489-106">[in]組合[EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)值，表示哪些類別的 managed 的類型和成員應該禁止在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="de489-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de489-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="de489-107">Return Value</span></span>  
  
|<span data-ttu-id="de489-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de489-108">HRESULT</span></span>|<span data-ttu-id="de489-109">描述</span><span class="sxs-lookup"><span data-stu-id="de489-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de489-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="de489-110">S_OK</span></span>|<span data-ttu-id="de489-111">`SetProtectedCategories`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="de489-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="de489-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="de489-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="de489-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="de489-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="de489-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="de489-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="de489-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="de489-115">The call timed out.</span></span>|  
|<span data-ttu-id="de489-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="de489-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="de489-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="de489-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="de489-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="de489-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="de489-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="de489-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="de489-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="de489-120">E_FAIL</span></span>|<span data-ttu-id="de489-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="de489-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="de489-122">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="de489-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="de489-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="de489-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de489-124">備註</span><span class="sxs-lookup"><span data-stu-id="de489-124">Remarks</span></span>  
 <span data-ttu-id="de489-125">每個`EApiCategories`值指的是 managed 的類型和成員的清單。</span><span class="sxs-lookup"><span data-stu-id="de489-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="de489-126">`EApiCategories`列舉型別和`SetProtectedCategories`方法直接相關的 managed<xref:System.Security.Permissions.HostProtectionAttribute>類別，用來標示將功能對應至所描述的類別公開的 managed 的類型和成員`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="de489-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="de489-127">如需詳細資訊，請參閱<xref:System.Security.Permissions.HostProtectionAttribute>和<xref:System.Security.Permissions.HostProtectionResource>列舉型別，會直接對應至`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="de489-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de489-128">需求</span><span class="sxs-lookup"><span data-stu-id="de489-128">Requirements</span></span>  
 <span data-ttu-id="de489-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de489-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de489-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de489-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de489-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="de489-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de489-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de489-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de489-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de489-133">See Also</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [<span data-ttu-id="de489-134">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="de489-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="de489-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="de489-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="de489-136">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="de489-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
