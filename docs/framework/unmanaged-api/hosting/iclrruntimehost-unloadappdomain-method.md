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
ms.openlocfilehash: 2a6dc878f156d5d18970fed72c9722bab60f9ba8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120399"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="833ce-102">ICLRRuntimeHost::UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="833ce-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="833ce-103">卸載對應至指定之數位識別碼的 managed <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="833ce-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="833ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="833ce-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="833ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="833ce-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="833ce-106">在要卸載之應用程式域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="833ce-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="833ce-107">[in] `true`，表示 common language runtime （CLR）必須等到它完成執行應用程式的目前線程，然後再嘗試卸載應用程式域。</span><span class="sxs-lookup"><span data-stu-id="833ce-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="833ce-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="833ce-108">Return Value</span></span>  
  
|<span data-ttu-id="833ce-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="833ce-109">HRESULT</span></span>|<span data-ttu-id="833ce-110">描述</span><span class="sxs-lookup"><span data-stu-id="833ce-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="833ce-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="833ce-111">S_OK</span></span>|<span data-ttu-id="833ce-112">已成功傳回 `UnloadAppDomain`。</span><span class="sxs-lookup"><span data-stu-id="833ce-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="833ce-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="833ce-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="833ce-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="833ce-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="833ce-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="833ce-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="833ce-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="833ce-116">The call timed out.</span></span>|  
|<span data-ttu-id="833ce-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="833ce-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="833ce-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="833ce-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="833ce-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="833ce-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="833ce-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="833ce-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="833ce-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="833ce-121">E_FAIL</span></span>|<span data-ttu-id="833ce-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="833ce-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="833ce-123">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="833ce-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="833ce-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="833ce-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="833ce-125">備註</span><span class="sxs-lookup"><span data-stu-id="833ce-125">Remarks</span></span>  
 <span data-ttu-id="833ce-126">您可以藉由呼叫[GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)，取得目前線程執行所在之應用程式域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="833ce-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="833ce-127">這個識別碼會對應至 managed <xref:System.AppDomain> 類型的 <xref:System.AppDomain.Id%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="833ce-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="833ce-128">需求</span><span class="sxs-lookup"><span data-stu-id="833ce-128">Requirements</span></span>  
 <span data-ttu-id="833ce-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="833ce-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="833ce-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="833ce-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="833ce-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="833ce-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="833ce-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="833ce-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="833ce-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="833ce-133">See also</span></span>

- [<span data-ttu-id="833ce-134">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="833ce-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
