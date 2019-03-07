---
title: ICorRuntimeHost::CreateEvidence 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54c21008e5922a5357f503821d87e297f0d00e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499247"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="6f052-102">ICorRuntimeHost::CreateEvidence 方法</span><span class="sxs-lookup"><span data-stu-id="6f052-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="6f052-103">取得類型的介面指標<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>，可讓主應用程式建立安全性辨識項，要傳遞給[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或是[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="6f052-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f052-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f052-104">Syntax</span></span>  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f052-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f052-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="6f052-106">[out]介面指標<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>用來建立安全性辨識項的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f052-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="6f052-107">這個指標型別`IUnknown`，所以通常應該呼叫的呼叫端`QueryInterface`若要取得的指標，此介面上<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6f052-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f052-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f052-108">Return Value</span></span>  
  
|<span data-ttu-id="6f052-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f052-109">HRESULT</span></span>|<span data-ttu-id="6f052-110">描述</span><span class="sxs-lookup"><span data-stu-id="6f052-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f052-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f052-111">S_OK</span></span>|<span data-ttu-id="6f052-112">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="6f052-112">The operation was successful.</span></span>|  
|<span data-ttu-id="6f052-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6f052-113">S_FALSE</span></span>|<span data-ttu-id="6f052-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="6f052-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6f052-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f052-115">E_FAIL</span></span>|<span data-ttu-id="6f052-116">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="6f052-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6f052-117">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="6f052-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6f052-118">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6f052-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6f052-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f052-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f052-120">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6f052-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f052-121">備註</span><span class="sxs-lookup"><span data-stu-id="6f052-121">Remarks</span></span>  
 <span data-ttu-id="6f052-122">這個方法會傳回空集合無法填入從原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f052-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="6f052-123">您應該使用<xref:System.Security.Policy.Evidence>方法改為。</span><span class="sxs-lookup"><span data-stu-id="6f052-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f052-124">需求</span><span class="sxs-lookup"><span data-stu-id="6f052-124">Requirements</span></span>  
 <span data-ttu-id="6f052-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f052-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f052-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f052-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f052-127">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6f052-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f052-128">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6f052-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f052-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f052-129">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="6f052-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="6f052-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
