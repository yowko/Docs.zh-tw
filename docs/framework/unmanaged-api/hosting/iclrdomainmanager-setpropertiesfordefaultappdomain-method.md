---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd7c835cdc4b53c753d714216d1745eb0b80c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772940"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="de141-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="de141-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="de141-103">設定將用來初始化預設應用程式定義域的屬性。</span><span class="sxs-lookup"><span data-stu-id="de141-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de141-104">語法</span><span class="sxs-lookup"><span data-stu-id="de141-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de141-105">參數</span><span class="sxs-lookup"><span data-stu-id="de141-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="de141-106">[in]中的項目數`pwszPropertyNames`和`pwszPropertyValues`。</span><span class="sxs-lookup"><span data-stu-id="de141-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="de141-107">[in]屬性名稱或如果沒有屬性則為 null 的陣列。</span><span class="sxs-lookup"><span data-stu-id="de141-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="de141-108">目前，唯一的屬性名稱都能夠辨識這個方法是"PARTIAL_TRUST_VISIBLE_ASSEMBLIES 」。</span><span class="sxs-lookup"><span data-stu-id="de141-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="de141-109">[in]屬性值或如果沒有屬性則為 null 的陣列。</span><span class="sxs-lookup"><span data-stu-id="de141-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de141-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="de141-110">Return Value</span></span>  
 <span data-ttu-id="de141-111">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="de141-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="de141-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de141-112">HRESULT</span></span>|<span data-ttu-id="de141-113">說明</span><span class="sxs-lookup"><span data-stu-id="de141-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de141-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="de141-114">S_OK</span></span>|<span data-ttu-id="de141-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="de141-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="de141-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="de141-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="de141-117">`pwszPropertyNames` 包含無法辨識這個方法的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="de141-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de141-118">備註</span><span class="sxs-lookup"><span data-stu-id="de141-118">Remarks</span></span>  
 <span data-ttu-id="de141-119">「 PARTIAL_TRUST_VISIBLE_ASSEMBLIES"的屬性值是一份具有條件式的組件<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性<xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>旗標，將會看見部分信任呼叫端在預設應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="de141-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de141-120">需求</span><span class="sxs-lookup"><span data-stu-id="de141-120">Requirements</span></span>  
 <span data-ttu-id="de141-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de141-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de141-122">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="de141-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="de141-123">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="de141-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de141-124">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de141-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de141-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de141-125">See also</span></span>

- [<span data-ttu-id="de141-126">裝載</span><span class="sxs-lookup"><span data-stu-id="de141-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="de141-127">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="de141-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
