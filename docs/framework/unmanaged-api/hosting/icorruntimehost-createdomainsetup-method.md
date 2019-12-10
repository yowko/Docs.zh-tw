---
title: ICorRuntimeHost::CreateDomainSetup 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 217874e625604613e67170a118a7bc3616e02c4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139642"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="29cfb-102">ICorRuntimeHost::CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="29cfb-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="29cfb-103">取得 IAppDomainSetup 類型的介面指標到 <xref:System.AppDomainSetup?displayProperty=nameWithType> 實例。</span><span class="sxs-lookup"><span data-stu-id="29cfb-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="29cfb-104">`IAppDomainSetup` 提供方法，在應用程式域建立之前設定其層面。</span><span class="sxs-lookup"><span data-stu-id="29cfb-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29cfb-105">語法</span><span class="sxs-lookup"><span data-stu-id="29cfb-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29cfb-106">參數</span><span class="sxs-lookup"><span data-stu-id="29cfb-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="29cfb-107">脫銷<xref:System.AppDomainSetup?displayProperty=nameWithType> 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="29cfb-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="29cfb-108">這個參數的類型為 `IUnknown`，因此呼叫端通常應該在這個指標上呼叫 `QueryInterface`，以取得類型 `IAppDomainSetup`的介面指標。</span><span class="sxs-lookup"><span data-stu-id="29cfb-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29cfb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="29cfb-109">Return Value</span></span>  
  
|<span data-ttu-id="29cfb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29cfb-110">HRESULT</span></span>|<span data-ttu-id="29cfb-111">描述</span><span class="sxs-lookup"><span data-stu-id="29cfb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29cfb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="29cfb-112">S_OK</span></span>|<span data-ttu-id="29cfb-113">作業成功。</span><span class="sxs-lookup"><span data-stu-id="29cfb-113">The operation was successful.</span></span>|  
|<span data-ttu-id="29cfb-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="29cfb-114">S_FALSE</span></span>|<span data-ttu-id="29cfb-115">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="29cfb-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="29cfb-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29cfb-116">E_FAIL</span></span>|<span data-ttu-id="29cfb-117">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="29cfb-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="29cfb-118">如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="29cfb-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="29cfb-119">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="29cfb-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="29cfb-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29cfb-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29cfb-121">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="29cfb-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29cfb-122">備註</span><span class="sxs-lookup"><span data-stu-id="29cfb-122">Remarks</span></span>  
 <span data-ttu-id="29cfb-123">從這個方法傳回的指標通常會當做參數傳遞給[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="29cfb-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29cfb-124">需求</span><span class="sxs-lookup"><span data-stu-id="29cfb-124">Requirements</span></span>  
 <span data-ttu-id="29cfb-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29cfb-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29cfb-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="29cfb-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29cfb-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="29cfb-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29cfb-128">**.NET Framework 版本：** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="29cfb-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29cfb-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="29cfb-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="29cfb-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="29cfb-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
