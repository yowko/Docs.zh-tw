---
title: "ICLRDomainManager::SetAppDomainManagerType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c94da8295a0ebb96d45e3a8f122d96bc2126c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="ecb73-102">ICLRDomainManager::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="ecb73-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="ecb73-103">指定型別，衍生自<xref:System.AppDomainManager?displayProperty=nameWithType>類別，將會用來初始化預設應用程式定義域的應用程式定義域管理員。</span><span class="sxs-lookup"><span data-stu-id="ecb73-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecb73-104">語法</span><span class="sxs-lookup"><span data-stu-id="ecb73-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecb73-105">參數</span><span class="sxs-lookup"><span data-stu-id="ecb73-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="ecb73-106">[in]顯示名稱的組件，其中包含應用程式定義域管理員類型。例如:"AdMgrExample，Version = 1.0.0.0，Culture = neutral，PublicKeyToken = 6856bccf150f00b3"。</span><span class="sxs-lookup"><span data-stu-id="ecb73-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="ecb73-107">[in]應用程式定義域管理員，包括命名空間的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ecb73-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="ecb73-108">[in]組合[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)提供應用程式定義域管理員的相關資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="ecb73-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecb73-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ecb73-109">Return Value</span></span>  
 <span data-ttu-id="ecb73-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecb73-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ecb73-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecb73-111">HRESULT</span></span>|<span data-ttu-id="ecb73-112">描述</span><span class="sxs-lookup"><span data-stu-id="ecb73-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecb73-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecb73-113">S_OK</span></span>|<span data-ttu-id="ecb73-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="ecb73-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ecb73-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecb73-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecb73-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ecb73-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecb73-117">備註</span><span class="sxs-lookup"><span data-stu-id="ecb73-117">Remarks</span></span>  
 <span data-ttu-id="ecb73-118">目前，唯一定義的值為`dwInitializeDomainFlags`是`eInitializeNewDomainFlags_NoSecurityChanges`，這會告知 common language runtime (CLR) 的應用程式定義域管理員不會修改安全性設定執行期間<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="ecb73-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ecb73-119">這可讓最佳化具有條件式的組件載入 CLR <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 屬性。</span><span class="sxs-lookup"><span data-stu-id="ecb73-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="ecb73-120">如果此集合的組件的可轉移結束大可以產生顯著的改善，啟動時間。</span><span class="sxs-lookup"><span data-stu-id="ecb73-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecb73-121">如果主機指定`eInitializeNewDomainFlags_NoSecurityChanges`應用程式網域管理員，<xref:System.InvalidOperationException>任何嘗試修改應用程式定義域的安全性，則會擲回。</span><span class="sxs-lookup"><span data-stu-id="ecb73-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="ecb73-122">呼叫[iclrcontrol:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)方法相當於呼叫`ICLRDomainManager::SetAppDomainManagerType`與`eInitializeNewDomainFlags_None`。</span><span class="sxs-lookup"><span data-stu-id="ecb73-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecb73-123">需求</span><span class="sxs-lookup"><span data-stu-id="ecb73-123">Requirements</span></span>  
 <span data-ttu-id="ecb73-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ecb73-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecb73-125">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ecb73-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ecb73-126">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ecb73-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecb73-127">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecb73-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb73-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecb73-128">See Also</span></span>  
 [<span data-ttu-id="ecb73-129">裝載</span><span class="sxs-lookup"><span data-stu-id="ecb73-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="ecb73-130">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="ecb73-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="ecb73-131">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="ecb73-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
