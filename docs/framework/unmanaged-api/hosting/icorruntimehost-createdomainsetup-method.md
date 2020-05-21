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
ms.openlocfilehash: aa1ce70311cd4ef0204c1c31efee8bd7b313c81d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762327"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="a2802-102">ICorRuntimeHost::CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="a2802-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="a2802-103">取得實例之類型 IAppDomainSetup 的介面指標 <xref:System.AppDomainSetup?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a2802-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="a2802-104">`IAppDomainSetup`提供方法來設定應用程式域的各個層面，然後再建立。</span><span class="sxs-lookup"><span data-stu-id="a2802-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2802-105">語法</span><span class="sxs-lookup"><span data-stu-id="a2802-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2802-106">參數</span><span class="sxs-lookup"><span data-stu-id="a2802-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="a2802-107">脫銷實例的介面指標 <xref:System.AppDomainSetup?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a2802-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="a2802-108">這個參數的類型為 `IUnknown` ，因此呼叫端通常會 `QueryInterface` 在此指標上呼叫，以取得類型的介面指標 `IAppDomainSetup` 。</span><span class="sxs-lookup"><span data-stu-id="a2802-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2802-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2802-109">Return Value</span></span>  
  
|<span data-ttu-id="a2802-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2802-110">HRESULT</span></span>|<span data-ttu-id="a2802-111">Description</span><span class="sxs-lookup"><span data-stu-id="a2802-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2802-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2802-112">S_OK</span></span>|<span data-ttu-id="a2802-113">作業成功。</span><span class="sxs-lookup"><span data-stu-id="a2802-113">The operation was successful.</span></span>|  
|<span data-ttu-id="a2802-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a2802-114">S_FALSE</span></span>|<span data-ttu-id="a2802-115">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="a2802-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a2802-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2802-116">E_FAIL</span></span>|<span data-ttu-id="a2802-117">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a2802-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a2802-118">如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。</span><span class="sxs-lookup"><span data-stu-id="a2802-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a2802-119">後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a2802-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2802-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2802-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2802-121">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a2802-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2802-122">備註</span><span class="sxs-lookup"><span data-stu-id="a2802-122">Remarks</span></span>  
 <span data-ttu-id="a2802-123">從這個方法傳回的指標通常會當做參數傳遞給[CreateDomainEx](icorruntimehost-createdomainex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a2802-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2802-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="a2802-124">Requirements</span></span>  
 <span data-ttu-id="a2802-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2802-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2802-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a2802-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2802-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a2802-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2802-128">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="a2802-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2802-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2802-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="a2802-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a2802-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
