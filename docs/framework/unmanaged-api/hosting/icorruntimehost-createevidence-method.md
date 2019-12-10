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
ms.openlocfilehash: 429ce0510162b3256cdf58f4820b04dd80243e29
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139630"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="67414-102">ICorRuntimeHost::CreateEvidence 方法</span><span class="sxs-lookup"><span data-stu-id="67414-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="67414-103">取得類型 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>的介面指標，可讓主機建立安全性辨識項，以傳遞至[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="67414-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67414-104">語法</span><span class="sxs-lookup"><span data-stu-id="67414-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67414-105">參數</span><span class="sxs-lookup"><span data-stu-id="67414-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="67414-106">脫銷用來建立安全性辨識項之 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="67414-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="67414-107">這個指標的型別 `IUnknown`，因此呼叫端通常應該在這個介面上呼叫 `QueryInterface`，以取得 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>的指標。</span><span class="sxs-lookup"><span data-stu-id="67414-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67414-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="67414-108">Return Value</span></span>  
  
|<span data-ttu-id="67414-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67414-109">HRESULT</span></span>|<span data-ttu-id="67414-110">描述</span><span class="sxs-lookup"><span data-stu-id="67414-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67414-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="67414-111">S_OK</span></span>|<span data-ttu-id="67414-112">作業成功。</span><span class="sxs-lookup"><span data-stu-id="67414-112">The operation was successful.</span></span>|  
|<span data-ttu-id="67414-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="67414-113">S_FALSE</span></span>|<span data-ttu-id="67414-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="67414-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="67414-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67414-115">E_FAIL</span></span>|<span data-ttu-id="67414-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="67414-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="67414-117">如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="67414-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="67414-118">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="67414-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="67414-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="67414-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="67414-120">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="67414-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67414-121">備註</span><span class="sxs-lookup"><span data-stu-id="67414-121">Remarks</span></span>  
 <span data-ttu-id="67414-122">這個方法會傳回無法從機器碼填入的空集合。</span><span class="sxs-lookup"><span data-stu-id="67414-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="67414-123">您應該改用 <xref:System.Security.Policy.Evidence> 方法。</span><span class="sxs-lookup"><span data-stu-id="67414-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67414-124">需求</span><span class="sxs-lookup"><span data-stu-id="67414-124">Requirements</span></span>  
 <span data-ttu-id="67414-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67414-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67414-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="67414-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67414-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="67414-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67414-128">**.NET Framework 版本：** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="67414-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67414-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="67414-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="67414-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="67414-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
