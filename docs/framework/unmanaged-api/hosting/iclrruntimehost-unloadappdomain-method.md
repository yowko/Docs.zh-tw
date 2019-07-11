---
title: ICLRRuntimeHost::UnloadAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e1a2358590b95b39b6495b74078f079c5b34876
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765685"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="3a029-102">ICLRRuntimeHost::UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="3a029-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="3a029-103">卸載 managed <xref:System.AppDomain> ，其對應於指定的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="3a029-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a029-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a029-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a029-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a029-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="3a029-106">[in]若要卸載的應用程式定義域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="3a029-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="3a029-107">[in]`true`來表示，common language runtime (CLR) 必須等到完成之前嘗試卸載應用程式定義域中執行的應用程式目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="3a029-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a029-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a029-108">Return Value</span></span>  
  
|<span data-ttu-id="3a029-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a029-109">HRESULT</span></span>|<span data-ttu-id="3a029-110">說明</span><span class="sxs-lookup"><span data-stu-id="3a029-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a029-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a029-111">S_OK</span></span>|<span data-ttu-id="3a029-112">`UnloadAppDomain` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3a029-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="3a029-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a029-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a029-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3a029-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a029-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a029-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a029-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3a029-116">The call timed out.</span></span>|  
|<span data-ttu-id="3a029-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a029-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a029-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3a029-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a029-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a029-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a029-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3a029-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a029-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a029-121">E_FAIL</span></span>|<span data-ttu-id="3a029-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a029-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a029-123">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="3a029-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a029-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3a029-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a029-125">備註</span><span class="sxs-lookup"><span data-stu-id="3a029-125">Remarks</span></span>  
 <span data-ttu-id="3a029-126">您可以取得數字的識別項，藉由呼叫目前的執行緒正在執行的所在之應用程式定義域[GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3a029-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="3a029-127">此識別碼會對應到<xref:System.AppDomain.Id%2A>的 managed 屬性<xref:System.AppDomain>型別。</span><span class="sxs-lookup"><span data-stu-id="3a029-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a029-128">需求</span><span class="sxs-lookup"><span data-stu-id="3a029-128">Requirements</span></span>  
 <span data-ttu-id="3a029-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a029-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a029-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a029-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a029-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3a029-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a029-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a029-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a029-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a029-133">See also</span></span>

- [<span data-ttu-id="3a029-134">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="3a029-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
