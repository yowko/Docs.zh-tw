---
title: ICorRuntimeHost::CreateDomainEx 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ed45c3975c58331490f89d8ca705f080d01d74e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466800"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="0eb5e-102">ICorRuntimeHost::CreateDomainEx 方法</span><span class="sxs-lookup"><span data-stu-id="0eb5e-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="0eb5e-103">建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-103">Creates an application domain.</span></span> <span data-ttu-id="0eb5e-104">呼叫端會收到類型的介面指標<xref:System._AppDomain>，執行個體的型別<xref:System.AppDomain?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0eb5e-105">這個方法可讓呼叫端傳遞 IAppDomainSetup 執行個體來設定傳回的其他功能<xref:System._AppDomain>執行個體。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb5e-106">語法</span><span class="sxs-lookup"><span data-stu-id="0eb5e-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eb5e-107">參數</span><span class="sxs-lookup"><span data-stu-id="0eb5e-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="0eb5e-108">[in]選擇性參數，可用來為網域指定的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="0eb5e-109">此易記名稱可以顯示在使用者介面，例如偵錯工具，以識別該定義域。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="0eb5e-110">[in]選擇性的介面指標的型別`IAppDomainSetup`呼叫得到[icorruntimehost:: Createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="0eb5e-111">[in]選擇性的指標陣列`IIdentity`執行個體，表示對應到安全性原則，以建立權限集合的辨識項。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="0eb5e-112">`IIdentity`物件，可由呼叫[CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="0eb5e-113">[out]類型的介面指標<xref:System._AppDomain>的執行個體<xref:System.AppDomain?displayProperty=nameWithType>，可用來進一步控制網域。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eb5e-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="0eb5e-114">Return Value</span></span>  
  
|<span data-ttu-id="0eb5e-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0eb5e-115">HRESULT</span></span>|<span data-ttu-id="0eb5e-116">描述</span><span class="sxs-lookup"><span data-stu-id="0eb5e-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0eb5e-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="0eb5e-117">S_OK</span></span>|<span data-ttu-id="0eb5e-118">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-118">The operation was successful.</span></span>|  
|<span data-ttu-id="0eb5e-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0eb5e-119">S_FALSE</span></span>|<span data-ttu-id="0eb5e-120">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0eb5e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0eb5e-121">E_FAIL</span></span>|<span data-ttu-id="0eb5e-122">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0eb5e-123">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0eb5e-124">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0eb5e-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0eb5e-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0eb5e-126">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eb5e-127">備註</span><span class="sxs-lookup"><span data-stu-id="0eb5e-127">Remarks</span></span>  
 <span data-ttu-id="0eb5e-128">`CreateDomainEx` 擴充功能[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)藉由呼叫者傳入`IAppDomainSetup`與設定應用程式定義域的屬性值的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eb5e-129">需求</span><span class="sxs-lookup"><span data-stu-id="0eb5e-129">Requirements</span></span>  
 <span data-ttu-id="0eb5e-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb5e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb5e-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0eb5e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0eb5e-132">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0eb5e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eb5e-133">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="0eb5e-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb5e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eb5e-134">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="0eb5e-135">CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="0eb5e-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="0eb5e-136">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="0eb5e-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
