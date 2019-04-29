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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f5de9882f8a029769d0ccbdac21aec541582a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937068"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="00877-102">ICorRuntimeHost::CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="00877-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="00877-103">取得介面指標的類型來 IAppDomainSetup<xref:System.AppDomainSetup?displayProperty=nameWithType>執行個體。</span><span class="sxs-lookup"><span data-stu-id="00877-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="00877-104">`IAppDomainSetup` 提供方法來設定應用程式定義域的層面，才能建立。</span><span class="sxs-lookup"><span data-stu-id="00877-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00877-105">語法</span><span class="sxs-lookup"><span data-stu-id="00877-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00877-106">參數</span><span class="sxs-lookup"><span data-stu-id="00877-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="00877-107">[out]介面指標<xref:System.AppDomainSetup?displayProperty=nameWithType>執行個體。</span><span class="sxs-lookup"><span data-stu-id="00877-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="00877-108">此參數的型別為`IUnknown`，所以通常應該呼叫的呼叫端`QueryInterface`這個指標，若要取得類型的介面指標上`IAppDomainSetup`。</span><span class="sxs-lookup"><span data-stu-id="00877-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00877-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="00877-109">Return Value</span></span>  
  
|<span data-ttu-id="00877-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00877-110">HRESULT</span></span>|<span data-ttu-id="00877-111">描述</span><span class="sxs-lookup"><span data-stu-id="00877-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00877-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="00877-112">S_OK</span></span>|<span data-ttu-id="00877-113">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="00877-113">The operation was successful.</span></span>|  
|<span data-ttu-id="00877-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="00877-114">S_FALSE</span></span>|<span data-ttu-id="00877-115">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="00877-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="00877-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00877-116">E_FAIL</span></span>|<span data-ttu-id="00877-117">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="00877-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="00877-118">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="00877-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="00877-119">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="00877-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="00877-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00877-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00877-121">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="00877-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00877-122">備註</span><span class="sxs-lookup"><span data-stu-id="00877-122">Remarks</span></span>  
 <span data-ttu-id="00877-123">從這個方法傳回的指標，通常做為參數傳遞[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="00877-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00877-124">需求</span><span class="sxs-lookup"><span data-stu-id="00877-124">Requirements</span></span>  
 <span data-ttu-id="00877-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00877-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00877-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00877-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00877-127">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="00877-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00877-128">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="00877-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00877-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00877-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="00877-130">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="00877-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
