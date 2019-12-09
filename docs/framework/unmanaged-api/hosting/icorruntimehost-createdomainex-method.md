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
ms.openlocfilehash: a3a2d1827774ddedc00eb849f64256e3f425b3fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127716"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="b2dd3-102">ICorRuntimeHost::CreateDomainEx 方法</span><span class="sxs-lookup"><span data-stu-id="b2dd3-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="b2dd3-103">建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-103">Creates an application domain.</span></span> <span data-ttu-id="b2dd3-104">呼叫端會接收類型為 <xref:System._AppDomain>的介面指標，<xref:System.AppDomain?displayProperty=nameWithType>的實例。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2dd3-105">這個方法可讓呼叫端傳遞 IAppDomainSetup 實例，以設定所傳回 <xref:System._AppDomain> 實例的其他功能。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2dd3-106">語法</span><span class="sxs-lookup"><span data-stu-id="b2dd3-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2dd3-107">參數</span><span class="sxs-lookup"><span data-stu-id="b2dd3-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="b2dd3-108">在選擇性參數，用來為定義域提供易記名稱。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="b2dd3-109">這個易記名稱可以在使用者介面（例如偵錯工具）中顯示，以識別網域。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="b2dd3-110">在`IAppDomainSetup`類型的選擇性介面指標，由呼叫[ICorRuntimeHost：： CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)方法所取得。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="b2dd3-111">在指向 `IIdentity` 實例的選擇性陣列，表示透過安全性原則對應的辨識項，以建立許可權集合。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="b2dd3-112">您可以藉由呼叫[CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)方法來取得 `IIdentity` 物件。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b2dd3-113">脫銷類型的介面指標 <xref:System._AppDomain> 至可用來進一步控制定義域的 <xref:System.AppDomain?displayProperty=nameWithType> 實例。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2dd3-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="b2dd3-114">Return Value</span></span>  
  
|<span data-ttu-id="b2dd3-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2dd3-115">HRESULT</span></span>|<span data-ttu-id="b2dd3-116">描述</span><span class="sxs-lookup"><span data-stu-id="b2dd3-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2dd3-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2dd3-117">S_OK</span></span>|<span data-ttu-id="b2dd3-118">作業成功。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-118">The operation was successful.</span></span>|  
|<span data-ttu-id="b2dd3-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b2dd3-119">S_FALSE</span></span>|<span data-ttu-id="b2dd3-120">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b2dd3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2dd3-121">E_FAIL</span></span>|<span data-ttu-id="b2dd3-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b2dd3-123">如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b2dd3-124">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b2dd3-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2dd3-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2dd3-126">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2dd3-127">備註</span><span class="sxs-lookup"><span data-stu-id="b2dd3-127">Remarks</span></span>  
 <span data-ttu-id="b2dd3-128">`CreateDomainEx` 藉由允許呼叫端傳入具有屬性值的 `IAppDomainSetup` 實例以設定應用程式域，來擴充[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)的功能。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2dd3-129">需求</span><span class="sxs-lookup"><span data-stu-id="b2dd3-129">Requirements</span></span>  
 <span data-ttu-id="b2dd3-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2dd3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2dd3-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b2dd3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2dd3-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b2dd3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2dd3-133">**.NET Framework 版本：** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="b2dd3-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2dd3-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2dd3-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="b2dd3-135">CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="b2dd3-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="b2dd3-136">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b2dd3-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
