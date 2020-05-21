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
ms.openlocfilehash: 4a91f57126c0cf2074bd086ddb2fb4cd9e0716d4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762314"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="78b7c-102">ICorRuntimeHost::CreateEvidence 方法</span><span class="sxs-lookup"><span data-stu-id="78b7c-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="78b7c-103">取得類型的介面指標 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> ，可讓主機建立要傳遞至[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或[CreateDomainEx](icorruntimehost-createdomainex-method.md)方法的安全性辨識項。</span><span class="sxs-lookup"><span data-stu-id="78b7c-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="78b7c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="78b7c-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="78b7c-106">脫銷實例的介面指標， <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> 用來建立安全性辨識項。</span><span class="sxs-lookup"><span data-stu-id="78b7c-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="78b7c-107">這個指標具有類型 `IUnknown` ，因此呼叫端通常會 `QueryInterface` 在這個介面上呼叫，以取得的指標 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="78b7c-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78b7c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="78b7c-108">Return Value</span></span>  
  
|<span data-ttu-id="78b7c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78b7c-109">HRESULT</span></span>|<span data-ttu-id="78b7c-110">Description</span><span class="sxs-lookup"><span data-stu-id="78b7c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78b7c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="78b7c-111">S_OK</span></span>|<span data-ttu-id="78b7c-112">作業成功。</span><span class="sxs-lookup"><span data-stu-id="78b7c-112">The operation was successful.</span></span>|  
|<span data-ttu-id="78b7c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="78b7c-113">S_FALSE</span></span>|<span data-ttu-id="78b7c-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="78b7c-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="78b7c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78b7c-115">E_FAIL</span></span>|<span data-ttu-id="78b7c-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="78b7c-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="78b7c-117">如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。</span><span class="sxs-lookup"><span data-stu-id="78b7c-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="78b7c-118">後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="78b7c-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78b7c-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78b7c-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78b7c-120">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="78b7c-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78b7c-121">備註</span><span class="sxs-lookup"><span data-stu-id="78b7c-121">Remarks</span></span>  
 <span data-ttu-id="78b7c-122">這個方法會傳回無法從機器碼填入的空集合。</span><span class="sxs-lookup"><span data-stu-id="78b7c-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="78b7c-123">您應該改為使用 <xref:System.Security.Policy.Evidence> 方法。</span><span class="sxs-lookup"><span data-stu-id="78b7c-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b7c-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="78b7c-124">Requirements</span></span>  
 <span data-ttu-id="78b7c-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78b7c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78b7c-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="78b7c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78b7c-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="78b7c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78b7c-128">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="78b7c-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b7c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78b7c-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="78b7c-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="78b7c-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
