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
ms.openlocfilehash: 89b3f9f248a445cc0568236d6a1df14269de4187
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615692"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="6177a-102">ICLRDomainManager::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="6177a-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="6177a-103">指定 <xref:System.AppDomainManager?displayProperty=nameWithType> 將用來初始化預設應用程式域之應用程式網域管理員的類型（衍生自類別）。</span><span class="sxs-lookup"><span data-stu-id="6177a-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6177a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6177a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6177a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6177a-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="6177a-106">在包含應用程式域管理員類型之元件的顯示名稱;例如： "AdMgrExample，Version = 1.0.0.0，Culture = 中性，PublicKeyToken = 6856bccf150f00b3"。</span><span class="sxs-lookup"><span data-stu-id="6177a-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="6177a-107">在應用程式域管理員的類型名稱，包括命名空間。</span><span class="sxs-lookup"><span data-stu-id="6177a-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="6177a-108">在[EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md)列舉值的組合，可提供應用程式域管理員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6177a-108">[in] A combination of [EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6177a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6177a-109">Return Value</span></span>  
 <span data-ttu-id="6177a-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6177a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6177a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6177a-111">HRESULT</span></span>|<span data-ttu-id="6177a-112">說明</span><span class="sxs-lookup"><span data-stu-id="6177a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6177a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6177a-113">S_OK</span></span>|<span data-ttu-id="6177a-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="6177a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6177a-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6177a-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6177a-116">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6177a-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6177a-117">備註</span><span class="sxs-lookup"><span data-stu-id="6177a-117">Remarks</span></span>  
 <span data-ttu-id="6177a-118">目前，唯一定義的值 `dwInitializeDomainFlags` 是 `eInitializeNewDomainFlags_NoSecurityChanges` ，它會告知 common language RUNTIME （CLR），應用程式域管理員在方法執行期間將不會修改安全性設定 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6177a-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6177a-119">這可讓 CLR 優化具有條件式 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性之元件的載入。</span><span class="sxs-lookup"><span data-stu-id="6177a-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="6177a-120">如果這組元件的可轉移關閉很大，這會導致啟動時間大幅改善。</span><span class="sxs-lookup"><span data-stu-id="6177a-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6177a-121">如果主機 `eInitializeNewDomainFlags_NoSecurityChanges` 為應用程式域管理員指定，則在 <xref:System.InvalidOperationException> 嘗試修改應用程式域的安全性時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="6177a-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="6177a-122">呼叫[ICLRControl：： SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)方法相當於 `ICLRDomainManager::SetAppDomainManagerType` 使用呼叫 `eInitializeNewDomainFlags_None` 。</span><span class="sxs-lookup"><span data-stu-id="6177a-122">Calling the [ICLRControl::SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6177a-123">需求</span><span class="sxs-lookup"><span data-stu-id="6177a-123">Requirements</span></span>  
 <span data-ttu-id="6177a-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6177a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6177a-125">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="6177a-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6177a-126">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6177a-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6177a-127">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6177a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6177a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6177a-128">See also</span></span>

- [<span data-ttu-id="6177a-129">裝載</span><span class="sxs-lookup"><span data-stu-id="6177a-129">Hosting</span></span>](index.md)
- [<span data-ttu-id="6177a-130">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="6177a-130">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
- [<span data-ttu-id="6177a-131">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="6177a-131">EInitializeNewDomainFlags Enumeration</span></span>](einitializenewdomainflags-enumeration.md)
