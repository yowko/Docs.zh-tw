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
ms.openlocfilehash: 293c1764f4c0d857138726b8ed4855b1e3b03116
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703915"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="9af6f-102">ICLRRuntimeHost::UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="9af6f-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="9af6f-103">卸載 <xref:System.AppDomain> 與指定的數值識別碼對應的 managed。</span><span class="sxs-lookup"><span data-stu-id="9af6f-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9af6f-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9af6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9af6f-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="9af6f-106">在要卸載之應用程式域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="9af6f-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="9af6f-107">[in] `true`表示 common language runtime （CLR）必須等到它完成執行應用程式的目前線程，然後再嘗試卸載應用程式域。</span><span class="sxs-lookup"><span data-stu-id="9af6f-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9af6f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9af6f-108">Return Value</span></span>  
  
|<span data-ttu-id="9af6f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9af6f-109">HRESULT</span></span>|<span data-ttu-id="9af6f-110">說明</span><span class="sxs-lookup"><span data-stu-id="9af6f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9af6f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9af6f-111">S_OK</span></span>|<span data-ttu-id="9af6f-112">`UnloadAppDomain`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9af6f-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="9af6f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9af6f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9af6f-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9af6f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9af6f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9af6f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9af6f-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="9af6f-116">The call timed out.</span></span>|  
|<span data-ttu-id="9af6f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9af6f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9af6f-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9af6f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9af6f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9af6f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9af6f-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="9af6f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9af6f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9af6f-121">E_FAIL</span></span>|<span data-ttu-id="9af6f-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9af6f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9af6f-123">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="9af6f-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9af6f-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9af6f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9af6f-125">備註</span><span class="sxs-lookup"><span data-stu-id="9af6f-125">Remarks</span></span>  
 <span data-ttu-id="9af6f-126">您可以藉由呼叫[GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)，取得目前線程執行所在之應用程式域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="9af6f-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="9af6f-127">這個識別碼會對應至 <xref:System.AppDomain.Id%2A> managed 類型的屬性 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="9af6f-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af6f-128">需求</span><span class="sxs-lookup"><span data-stu-id="9af6f-128">Requirements</span></span>  
 <span data-ttu-id="9af6f-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9af6f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af6f-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="9af6f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9af6f-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9af6f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9af6f-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9af6f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af6f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9af6f-133">See also</span></span>

- [<span data-ttu-id="9af6f-134">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="9af6f-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
