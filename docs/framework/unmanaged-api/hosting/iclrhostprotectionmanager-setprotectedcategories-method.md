---
title: ICLRHostProtectionManager::SetProtectedCategories 方法
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63b6e85b6abe20e9e1f0b00648a06a31735e63c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183621"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="ecb64-102">ICLRHostProtectionManager::SetProtectedCategories 方法</span><span class="sxs-lookup"><span data-stu-id="ecb64-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="ecb64-103">指定的 managed 的類型和成員的類別應該禁止在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="ecb64-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecb64-104">語法</span><span class="sxs-lookup"><span data-stu-id="ecb64-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecb64-105">參數</span><span class="sxs-lookup"><span data-stu-id="ecb64-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="ecb64-106">[in]組合[EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)值，指出哪一個類別的 managed 的類型和成員應該禁止在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="ecb64-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecb64-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ecb64-107">Return Value</span></span>  
  
|<span data-ttu-id="ecb64-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecb64-108">HRESULT</span></span>|<span data-ttu-id="ecb64-109">描述</span><span class="sxs-lookup"><span data-stu-id="ecb64-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecb64-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecb64-110">S_OK</span></span>|`SetProtectedCategories` <span data-ttu-id="ecb64-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ecb64-111">returned successfully.</span></span>|  
|<span data-ttu-id="ecb64-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecb64-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecb64-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ecb64-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecb64-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecb64-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecb64-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="ecb64-115">The call timed out.</span></span>|  
|<span data-ttu-id="ecb64-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecb64-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecb64-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ecb64-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecb64-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecb64-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecb64-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="ecb64-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecb64-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecb64-120">E_FAIL</span></span>|<span data-ttu-id="ecb64-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecb64-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecb64-122">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="ecb64-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecb64-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ecb64-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecb64-124">備註</span><span class="sxs-lookup"><span data-stu-id="ecb64-124">Remarks</span></span>  
 <span data-ttu-id="ecb64-125">每個`EApiCategories`值指的是 managed 的類型和成員的清單。</span><span class="sxs-lookup"><span data-stu-id="ecb64-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="ecb64-126">`EApiCategories`列舉型別和`SetProtectedCategories`方法直接相關的 managed<xref:System.Security.Permissions.HostProtectionAttribute>類別，用來標記 managed 的類型和成員，將功能對應至所描述的類別公開`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="ecb64-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="ecb64-127">如需詳細資訊，請參閱 <<c0> <xref:System.Security.Permissions.HostProtectionAttribute> 而<xref:System.Security.Permissions.HostProtectionResource>列舉型別，會直接對應到`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="ecb64-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecb64-128">需求</span><span class="sxs-lookup"><span data-stu-id="ecb64-128">Requirements</span></span>  
 <span data-ttu-id="ecb64-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ecb64-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecb64-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ecb64-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecb64-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ecb64-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ecb64-132">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ecb64-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ecb64-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecb64-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="ecb64-134">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="ecb64-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="ecb64-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="ecb64-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ecb64-136">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="ecb64-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
