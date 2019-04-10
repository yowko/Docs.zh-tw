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
ms.openlocfilehash: 490af9ca67b538e0093115a6b371b65d9788772f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222961"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="eeca5-102">ICLRRuntimeHost::UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="eeca5-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="eeca5-103">卸載 managed <xref:System.AppDomain> ，其對應於指定的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="eeca5-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeca5-104">語法</span><span class="sxs-lookup"><span data-stu-id="eeca5-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeca5-105">參數</span><span class="sxs-lookup"><span data-stu-id="eeca5-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="eeca5-106">[in]若要卸載的應用程式定義域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="eeca5-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="eeca5-107">[in]`true`來表示，common language runtime (CLR) 必須等到完成之前嘗試卸載應用程式定義域中執行的應用程式目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="eeca5-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eeca5-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="eeca5-108">Return Value</span></span>  
  
|<span data-ttu-id="eeca5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eeca5-109">HRESULT</span></span>|<span data-ttu-id="eeca5-110">描述</span><span class="sxs-lookup"><span data-stu-id="eeca5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eeca5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eeca5-111">S_OK</span></span>|`UnloadAppDomain` <span data-ttu-id="eeca5-112">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="eeca5-112">returned successfully.</span></span>|  
|<span data-ttu-id="eeca5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eeca5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eeca5-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="eeca5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eeca5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eeca5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eeca5-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="eeca5-116">The call timed out.</span></span>|  
|<span data-ttu-id="eeca5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eeca5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eeca5-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eeca5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eeca5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eeca5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eeca5-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="eeca5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eeca5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eeca5-121">E_FAIL</span></span>|<span data-ttu-id="eeca5-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="eeca5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eeca5-123">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="eeca5-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eeca5-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eeca5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeca5-125">備註</span><span class="sxs-lookup"><span data-stu-id="eeca5-125">Remarks</span></span>  
 <span data-ttu-id="eeca5-126">您可以取得數字的識別項，藉由呼叫目前的執行緒正在執行的所在之應用程式定義域[GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)。</span><span class="sxs-lookup"><span data-stu-id="eeca5-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="eeca5-127">此識別碼會對應到<xref:System.AppDomain.Id%2A>的 managed 屬性<xref:System.AppDomain>型別。</span><span class="sxs-lookup"><span data-stu-id="eeca5-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeca5-128">需求</span><span class="sxs-lookup"><span data-stu-id="eeca5-128">Requirements</span></span>  
 <span data-ttu-id="eeca5-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eeca5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeca5-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eeca5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eeca5-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eeca5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="eeca5-132">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="eeca5-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eeca5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eeca5-133">See also</span></span>

- [<span data-ttu-id="eeca5-134">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="eeca5-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
