---
title: ICLRDomainManager::SetAppDomainManagerType 方法
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c2927195b650f1098292f3d59cd887e084aea21
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490056"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="faaae-102">ICLRDomainManager::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="faaae-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="faaae-103">指定的型別，衍生自<xref:System.AppDomainManager?displayProperty=nameWithType>類別，將會用來初始化預設應用程式定義域的應用程式定義域管理員。</span><span class="sxs-lookup"><span data-stu-id="faaae-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faaae-104">語法</span><span class="sxs-lookup"><span data-stu-id="faaae-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faaae-105">參數</span><span class="sxs-lookup"><span data-stu-id="faaae-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="faaae-106">[in]包含應用程式定義域管理員類型; 組件的顯示名稱例如：「 AdMgrExample，version=1.0.0.0，Culture = neutral，PublicKeyToken = 6856bccf150f00b3"。</span><span class="sxs-lookup"><span data-stu-id="faaae-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="faaae-107">[in]應用程式定義域管理員，包括命名空間型別名稱。</span><span class="sxs-lookup"><span data-stu-id="faaae-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="faaae-108">[in]組合[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)提供應用程式定義域管理員的相關資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="faaae-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faaae-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="faaae-109">Return Value</span></span>  
 <span data-ttu-id="faaae-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="faaae-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="faaae-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="faaae-111">HRESULT</span></span>|<span data-ttu-id="faaae-112">描述</span><span class="sxs-lookup"><span data-stu-id="faaae-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="faaae-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="faaae-113">S_OK</span></span>|<span data-ttu-id="faaae-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="faaae-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="faaae-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="faaae-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="faaae-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="faaae-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faaae-117">備註</span><span class="sxs-lookup"><span data-stu-id="faaae-117">Remarks</span></span>  
 <span data-ttu-id="faaae-118">目前，唯一定義的值`dwInitializeDomainFlags`已`eInitializeNewDomainFlags_NoSecurityChanges`，這會告知 common language runtime (CLR)，應用程式定義域管理員不會修改安全性設定執行期間<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="faaae-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="faaae-119">這可讓 CLR 的最佳化的條件式的組件載入<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性。</span><span class="sxs-lookup"><span data-stu-id="faaae-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="faaae-120">如果這個集合的組件的可轉移關閉很大，這會導致啟動時間大幅提升。</span><span class="sxs-lookup"><span data-stu-id="faaae-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="faaae-121">如果指定了主機`eInitializeNewDomainFlags_NoSecurityChanges`應用程式網域管理員，<xref:System.InvalidOperationException>任何嘗試修改應用程式定義域的安全性，便會擲回。</span><span class="sxs-lookup"><span data-stu-id="faaae-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="faaae-122">呼叫[iclrcontrol:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)方法就相當於呼叫`ICLRDomainManager::SetAppDomainManagerType`使用`eInitializeNewDomainFlags_None`。</span><span class="sxs-lookup"><span data-stu-id="faaae-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faaae-123">需求</span><span class="sxs-lookup"><span data-stu-id="faaae-123">Requirements</span></span>  
 <span data-ttu-id="faaae-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="faaae-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faaae-125">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="faaae-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="faaae-126">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="faaae-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faaae-127">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faaae-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faaae-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faaae-128">See also</span></span>
- [<span data-ttu-id="faaae-129">裝載</span><span class="sxs-lookup"><span data-stu-id="faaae-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="faaae-130">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="faaae-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="faaae-131">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="faaae-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
