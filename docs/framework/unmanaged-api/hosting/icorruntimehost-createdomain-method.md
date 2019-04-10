---
title: ICorRuntimeHost::CreateDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea63627bc1e689c93634c8fe8b9048b271758573
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156113"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="24470-102">ICorRuntimeHost::CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="24470-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="24470-103">建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="24470-103">Creates an application domain.</span></span> <span data-ttu-id="24470-104">呼叫端會收到類型的介面指標<xref:System._AppDomain>型別的執行個體<xref:System.AppDomain?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="24470-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24470-105">語法</span><span class="sxs-lookup"><span data-stu-id="24470-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24470-106">參數</span><span class="sxs-lookup"><span data-stu-id="24470-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="24470-107">[in]選擇性參數，可用來為網域指定的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="24470-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="24470-108">此易記名稱可以顯示在使用者介面，例如偵錯工具，以識別該定義域。</span><span class="sxs-lookup"><span data-stu-id="24470-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="24470-109">[in]選擇性的指標陣列`IIdentity`執行個體，表示對應到安全性原則，以建立權限集合的辨識項。</span><span class="sxs-lookup"><span data-stu-id="24470-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="24470-110">`IIdentity`物件，可由呼叫[CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="24470-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="24470-111">[out]類型的介面指標<xref:System._AppDomain>的執行個體<xref:System.AppDomain?displayProperty=nameWithType>，可用來進一步控制網域。</span><span class="sxs-lookup"><span data-stu-id="24470-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24470-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="24470-112">Return Value</span></span>  
  
|<span data-ttu-id="24470-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24470-113">HRESULT</span></span>|<span data-ttu-id="24470-114">描述</span><span class="sxs-lookup"><span data-stu-id="24470-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24470-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="24470-115">S_OK</span></span>|<span data-ttu-id="24470-116">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="24470-116">The operation was successful.</span></span>|  
|<span data-ttu-id="24470-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="24470-117">S_FALSE</span></span>|<span data-ttu-id="24470-118">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="24470-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="24470-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24470-119">E_FAIL</span></span>|<span data-ttu-id="24470-120">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="24470-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="24470-121">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="24470-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="24470-122">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="24470-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="24470-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24470-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24470-124">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="24470-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24470-125">需求</span><span class="sxs-lookup"><span data-stu-id="24470-125">Requirements</span></span>  
 <span data-ttu-id="24470-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24470-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24470-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24470-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24470-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="24470-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24470-129">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="24470-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24470-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24470-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="24470-131">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="24470-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
