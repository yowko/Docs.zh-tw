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
ms.openlocfilehash: 1be7eee5c2591f26c33572446080a4fa4b3b929d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723892"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="57512-102">ICorRuntimeHost::CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="57512-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>

<span data-ttu-id="57512-103">取得實例的型別 IAppDomainSetup 介面指標 <xref:System.AppDomainSetup?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="57512-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="57512-104">`IAppDomainSetup` 提供方法來設定應用程式域在建立之前的各個層面。</span><span class="sxs-lookup"><span data-stu-id="57512-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57512-105">語法</span><span class="sxs-lookup"><span data-stu-id="57512-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57512-106">參數</span><span class="sxs-lookup"><span data-stu-id="57512-106">Parameters</span></span>  

 `pAppDomainSetup`  
 <span data-ttu-id="57512-107">擴展實例的介面指標 <xref:System.AppDomainSetup?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="57512-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="57512-108">此參數的類型為 `IUnknown` ，因此呼叫端通常會 `QueryInterface` 在這個指標上呼叫，以取得型別的介面指標 `IAppDomainSetup` 。</span><span class="sxs-lookup"><span data-stu-id="57512-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57512-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="57512-109">Return Value</span></span>  
  
|<span data-ttu-id="57512-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57512-110">HRESULT</span></span>|<span data-ttu-id="57512-111">描述</span><span class="sxs-lookup"><span data-stu-id="57512-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57512-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="57512-112">S_OK</span></span>|<span data-ttu-id="57512-113">作業成功。</span><span class="sxs-lookup"><span data-stu-id="57512-113">The operation was successful.</span></span>|  
|<span data-ttu-id="57512-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="57512-114">S_FALSE</span></span>|<span data-ttu-id="57512-115">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="57512-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="57512-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57512-116">E_FAIL</span></span>|<span data-ttu-id="57512-117">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="57512-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="57512-118">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="57512-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="57512-119">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="57512-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="57512-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57512-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57512-121">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="57512-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57512-122">備註</span><span class="sxs-lookup"><span data-stu-id="57512-122">Remarks</span></span>  

 <span data-ttu-id="57512-123">從這個方法傳回的指標通常會以參數形式傳遞至 [CreateDomainEx](icorruntimehost-createdomainex-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="57512-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57512-124">需求</span><span class="sxs-lookup"><span data-stu-id="57512-124">Requirements</span></span>  

 <span data-ttu-id="57512-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57512-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57512-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="57512-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57512-127">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="57512-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57512-128">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="57512-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57512-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57512-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="57512-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="57512-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
