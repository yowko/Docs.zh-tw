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
ms.openlocfilehash: 5e1c1b1984c63bedb3c073f45a7b9a3574afdcec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615679"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="aedf5-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="aedf5-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="aedf5-103">設定將用來初始化預設應用程式域的屬性。</span><span class="sxs-lookup"><span data-stu-id="aedf5-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedf5-104">語法</span><span class="sxs-lookup"><span data-stu-id="aedf5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aedf5-105">參數</span><span class="sxs-lookup"><span data-stu-id="aedf5-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="aedf5-106">在和中的專案數 `pwszPropertyNames` `pwszPropertyValues` 。</span><span class="sxs-lookup"><span data-stu-id="aedf5-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="aedf5-107">在屬性名稱的陣列，如果沒有屬性，則為 null。</span><span class="sxs-lookup"><span data-stu-id="aedf5-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="aedf5-108">目前，這個方法所能辨識的屬性名稱是 "PARTIAL_TRUST_VISIBLE_ASSEMBLIES"。</span><span class="sxs-lookup"><span data-stu-id="aedf5-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="aedf5-109">在屬性值的陣列，如果沒有屬性，則為 null。</span><span class="sxs-lookup"><span data-stu-id="aedf5-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aedf5-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="aedf5-110">Return Value</span></span>  
 <span data-ttu-id="aedf5-111">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="aedf5-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aedf5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aedf5-112">HRESULT</span></span>|<span data-ttu-id="aedf5-113">說明</span><span class="sxs-lookup"><span data-stu-id="aedf5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aedf5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="aedf5-114">S_OK</span></span>|<span data-ttu-id="aedf5-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="aedf5-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="aedf5-116">HRESULT_FROM_WIN32 （ERROR_UNKNOWN_PROPERTY）</span><span class="sxs-lookup"><span data-stu-id="aedf5-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="aedf5-117">`pwszPropertyNames`包含此方法無法辨識的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="aedf5-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aedf5-118">備註</span><span class="sxs-lookup"><span data-stu-id="aedf5-118">Remarks</span></span>  
 <span data-ttu-id="aedf5-119">"PARTIAL_TRUST_VISIBLE_ASSEMBLIES" 的屬性值是具有條件式 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性加上旗標的元件清單 <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> ，在預設應用程式域中，會對部分信任的呼叫者顯示。</span><span class="sxs-lookup"><span data-stu-id="aedf5-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aedf5-120">需求</span><span class="sxs-lookup"><span data-stu-id="aedf5-120">Requirements</span></span>  
 <span data-ttu-id="aedf5-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aedf5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aedf5-122">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="aedf5-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aedf5-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="aedf5-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aedf5-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aedf5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedf5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aedf5-125">See also</span></span>

- [<span data-ttu-id="aedf5-126">裝載</span><span class="sxs-lookup"><span data-stu-id="aedf5-126">Hosting</span></span>](index.md)
- [<span data-ttu-id="aedf5-127">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="aedf5-127">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
