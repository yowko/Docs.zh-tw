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
ms.openlocfilehash: 5c61e2e1208cec0bda1492964a8d02bd71f5a1c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129324"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="7b1e1-102">ICLRDomainManager::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="7b1e1-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="7b1e1-103">指定將用來初始化預設應用程式域之應用程式網域管理員的衍生自 <xref:System.AppDomainManager?displayProperty=nameWithType> 類別的型別。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b1e1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b1e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b1e1-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="7b1e1-106">在包含應用程式域管理員類型之元件的顯示名稱;例如： "AdMgrExample，Version = 1.0.0.0，Culture = 中性，PublicKeyToken = 6856bccf150f00b3"。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="7b1e1-107">在應用程式域管理員的類型名稱，包括命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="7b1e1-108">在[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)列舉值的組合，可提供應用程式域管理員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b1e1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7b1e1-109">Return Value</span></span>  
 <span data-ttu-id="7b1e1-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7b1e1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b1e1-111">HRESULT</span></span>|<span data-ttu-id="7b1e1-112">描述</span><span class="sxs-lookup"><span data-stu-id="7b1e1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b1e1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b1e1-113">S_OK</span></span>|<span data-ttu-id="7b1e1-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7b1e1-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b1e1-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b1e1-116">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b1e1-117">備註</span><span class="sxs-lookup"><span data-stu-id="7b1e1-117">Remarks</span></span>  
 <span data-ttu-id="7b1e1-118">目前，`dwInitializeDomainFlags` 的唯一定義值是 `eInitializeNewDomainFlags_NoSecurityChanges`，它會告知 common language runtime （CLR），應用程式域管理員在執行 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 方法期間將不會修改安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7b1e1-119">這可讓 CLR 將具有條件式 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性的元件載入優化。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="7b1e1-120">如果這組元件的可轉移關閉很大，這會導致啟動時間大幅改善。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b1e1-121">如果主機指定應用程式域管理員的 `eInitializeNewDomainFlags_NoSecurityChanges`，如果有任何嘗試修改應用程式域的安全性，則會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="7b1e1-122">呼叫[ICLRControl：： SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)方法相當於使用 `eInitializeNewDomainFlags_None`呼叫 `ICLRDomainManager::SetAppDomainManagerType`。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1e1-123">需求</span><span class="sxs-lookup"><span data-stu-id="7b1e1-123">Requirements</span></span>  
 <span data-ttu-id="7b1e1-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b1e1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1e1-125">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="7b1e1-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7b1e1-126">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7b1e1-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b1e1-127">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b1e1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1e1-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="7b1e1-128">See also</span></span>

- [<span data-ttu-id="7b1e1-129">裝載</span><span class="sxs-lookup"><span data-stu-id="7b1e1-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="7b1e1-130">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="7b1e1-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="7b1e1-131">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7b1e1-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
