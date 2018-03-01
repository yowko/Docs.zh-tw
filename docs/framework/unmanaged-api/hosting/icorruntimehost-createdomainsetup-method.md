---
title: "ICorRuntimeHost::CreateDomainSetup 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e15f40402b222037f7ed8b23be3df36acafc73c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="b6478-102">ICorRuntimeHost::CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="b6478-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="b6478-103">取得類型的介面指標來 IAppDomainSetup<xref:System.AppDomainSetup?displayProperty=nameWithType>執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6478-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="b6478-104">`IAppDomainSetup`提供方法來設定應用程式定義域的層面，才能建立。</span><span class="sxs-lookup"><span data-stu-id="b6478-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6478-105">語法</span><span class="sxs-lookup"><span data-stu-id="b6478-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6478-106">參數</span><span class="sxs-lookup"><span data-stu-id="b6478-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="b6478-107">[out]介面指標<xref:System.AppDomainSetup?displayProperty=nameWithType>執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6478-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="b6478-108">這個參數的型別為`IUnknown`，因此呼叫端通常應該呼叫`QueryInterface`這個指標，以取得類型的介面指標上`IAppDomainSetup`。</span><span class="sxs-lookup"><span data-stu-id="b6478-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6478-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6478-109">Return Value</span></span>  
  
|<span data-ttu-id="b6478-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6478-110">HRESULT</span></span>|<span data-ttu-id="b6478-111">描述</span><span class="sxs-lookup"><span data-stu-id="b6478-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6478-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6478-112">S_OK</span></span>|<span data-ttu-id="b6478-113">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="b6478-113">The operation was successful.</span></span>|  
|<span data-ttu-id="b6478-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b6478-114">S_FALSE</span></span>|<span data-ttu-id="b6478-115">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="b6478-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b6478-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6478-116">E_FAIL</span></span>|<span data-ttu-id="b6478-117">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b6478-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b6478-118">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="b6478-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b6478-119">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b6478-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b6478-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6478-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6478-121">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b6478-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6478-122">備註</span><span class="sxs-lookup"><span data-stu-id="b6478-122">Remarks</span></span>  
 <span data-ttu-id="b6478-123">從這個方法傳回的指標通常會傳遞為參數，以[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b6478-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6478-124">需求</span><span class="sxs-lookup"><span data-stu-id="b6478-124">Requirements</span></span>  
 <span data-ttu-id="b6478-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6478-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6478-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6478-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6478-127">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6478-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6478-128">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="b6478-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6478-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6478-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="b6478-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b6478-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
