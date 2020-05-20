---
title: ICLRRuntimeHost::ExecuteInAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: 505c16cb7ead7950b6d2d6d401730cc3368fb6aa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703303"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="5a4c3-102">ICLRRuntimeHost::ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="5a4c3-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="5a4c3-103">指定 <xref:System.AppDomain> 要在其中執行指定 managed 程式碼的。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a4c3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a4c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a4c3-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="5a4c3-106">在<xref:System.AppDomain>要在其中執行指定方法之的數位識別碼。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="5a4c3-107">在要在指定的內執行之函式的指標 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="5a4c3-108">在不透明呼叫端所配置記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="5a4c3-109">這個參數是由 common language runtime （CLR）傳遞至網域回呼。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="5a4c3-110">這不是運行時間管理的堆積記憶體;這個記憶體的配置和存留期都是由呼叫者所控制。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a4c3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a4c3-111">Return Value</span></span>  
  
|<span data-ttu-id="5a4c3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a4c3-112">HRESULT</span></span>|<span data-ttu-id="5a4c3-113">說明</span><span class="sxs-lookup"><span data-stu-id="5a4c3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a4c3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a4c3-114">S_OK</span></span>|<span data-ttu-id="5a4c3-115">`ExecuteInAppDomain`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="5a4c3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a4c3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a4c3-117">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5a4c3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5a4c3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5a4c3-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-119">The call timed out.</span></span>|  
|<span data-ttu-id="5a4c3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5a4c3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5a4c3-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5a4c3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5a4c3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5a4c3-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5a4c3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a4c3-124">E_FAIL</span></span>|<span data-ttu-id="5a4c3-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5a4c3-126">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5a4c3-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a4c3-128">備註</span><span class="sxs-lookup"><span data-stu-id="5a4c3-128">Remarks</span></span>  
 <span data-ttu-id="5a4c3-129">`ExecuteInAppDomain`可讓主機控制 <xref:System.AppDomain> 應執行指定 managed 方法的 managed。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="5a4c3-130">藉 <xref:System.AppDomain.Id%2A> 由呼叫[GetCurrentAppDomainId 方法](iclrruntimehost-getcurrentappdomainid-method.md)，您可以取得應用程式域識別碼的值，其對應至屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4c3-131">需求</span><span class="sxs-lookup"><span data-stu-id="5a4c3-131">Requirements</span></span>  
 <span data-ttu-id="5a4c3-132">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a4c3-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4c3-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5a4c3-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a4c3-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5a4c3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a4c3-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a4c3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4c3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a4c3-136">See also</span></span>

- [<span data-ttu-id="5a4c3-137">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="5a4c3-137">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
