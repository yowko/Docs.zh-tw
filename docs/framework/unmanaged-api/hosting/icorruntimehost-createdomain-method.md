---
title: "ICorRuntimeHost::CreateDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe0adad8397f42716368691abbb1d1c303fced97
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="1a5df-102">ICorRuntimeHost::CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1a5df-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="1a5df-103">建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="1a5df-103">Creates an application domain.</span></span> <span data-ttu-id="1a5df-104">呼叫端會收到類型的介面指標<xref:System._AppDomain>型別的執行個體<xref:System.AppDomain?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1a5df-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a5df-105">語法</span><span class="sxs-lookup"><span data-stu-id="1a5df-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a5df-106">參數</span><span class="sxs-lookup"><span data-stu-id="1a5df-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="1a5df-107">[in]選擇性參數，用來讓易記名稱的網域。</span><span class="sxs-lookup"><span data-stu-id="1a5df-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="1a5df-108">此易記名稱可以顯示在使用者介面，例如偵錯工具，以識別該定義域。</span><span class="sxs-lookup"><span data-stu-id="1a5df-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="1a5df-109">[in]選擇性的指標陣列`IIdentity`代表對應透過安全性原則，以建立權限集合的辨識項的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1a5df-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="1a5df-110">`IIdentity`可取得物件，請呼叫[CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1a5df-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1a5df-111">[out]類型的介面指標<xref:System._AppDomain>的執行個體<xref:System.AppDomain?displayProperty=nameWithType>可用來進一步控制網域。</span><span class="sxs-lookup"><span data-stu-id="1a5df-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a5df-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="1a5df-112">Return Value</span></span>  
  
|<span data-ttu-id="1a5df-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a5df-113">HRESULT</span></span>|<span data-ttu-id="1a5df-114">描述</span><span class="sxs-lookup"><span data-stu-id="1a5df-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a5df-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a5df-115">S_OK</span></span>|<span data-ttu-id="1a5df-116">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="1a5df-116">The operation was successful.</span></span>|  
|<span data-ttu-id="1a5df-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1a5df-117">S_FALSE</span></span>|<span data-ttu-id="1a5df-118">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="1a5df-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1a5df-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1a5df-119">E_FAIL</span></span>|<span data-ttu-id="1a5df-120">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1a5df-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1a5df-121">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="1a5df-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1a5df-122">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1a5df-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1a5df-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a5df-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a5df-124">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1a5df-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a5df-125">需求</span><span class="sxs-lookup"><span data-stu-id="1a5df-125">Requirements</span></span>  
 <span data-ttu-id="1a5df-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1a5df-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a5df-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1a5df-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a5df-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1a5df-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a5df-129">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="1a5df-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5df-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a5df-130">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="1a5df-131">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="1a5df-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
