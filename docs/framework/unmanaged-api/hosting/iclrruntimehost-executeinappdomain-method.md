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
ms.openlocfilehash: c847f177f48d72f28192d1efabe93c65a7b3f4b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120497"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="e6d35-102">ICLRRuntimeHost::ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="e6d35-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="e6d35-103">指定要在其中執行指定 managed 程式碼的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="e6d35-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d35-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6d35-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6d35-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6d35-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="e6d35-106">在要在其中執行指定方法之 <xref:System.AppDomain> 的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6d35-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="e6d35-107">在要在指定的 <xref:System.AppDomain>內執行之函式的指標。</span><span class="sxs-lookup"><span data-stu-id="e6d35-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="e6d35-108">在不透明呼叫端所配置記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="e6d35-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="e6d35-109">這個參數是由 common language runtime （CLR）傳遞至網域回呼。</span><span class="sxs-lookup"><span data-stu-id="e6d35-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="e6d35-110">這不是運行時間管理的堆積記憶體;這個記憶體的配置和存留期都是由呼叫者所控制。</span><span class="sxs-lookup"><span data-stu-id="e6d35-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6d35-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6d35-111">Return Value</span></span>  
  
|<span data-ttu-id="e6d35-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6d35-112">HRESULT</span></span>|<span data-ttu-id="e6d35-113">描述</span><span class="sxs-lookup"><span data-stu-id="e6d35-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6d35-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6d35-114">S_OK</span></span>|<span data-ttu-id="e6d35-115">已成功傳回 `ExecuteInAppDomain`。</span><span class="sxs-lookup"><span data-stu-id="e6d35-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="e6d35-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6d35-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6d35-117">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e6d35-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6d35-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6d35-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6d35-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e6d35-119">The call timed out.</span></span>|  
|<span data-ttu-id="e6d35-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6d35-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6d35-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e6d35-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6d35-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6d35-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6d35-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e6d35-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6d35-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6d35-124">E_FAIL</span></span>|<span data-ttu-id="e6d35-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e6d35-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6d35-126">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="e6d35-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6d35-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e6d35-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6d35-128">備註</span><span class="sxs-lookup"><span data-stu-id="e6d35-128">Remarks</span></span>  
 <span data-ttu-id="e6d35-129">`ExecuteInAppDomain` 可讓主機控制要在哪一個 managed <xref:System.AppDomain> 中執行指定的 managed 方法。</span><span class="sxs-lookup"><span data-stu-id="e6d35-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="e6d35-130">您可以藉由呼叫[GetCurrentAppDomainId 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)，取得應用程式域識別碼的值，其對應至 <xref:System.AppDomain.Id%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e6d35-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d35-131">需求</span><span class="sxs-lookup"><span data-stu-id="e6d35-131">Requirements</span></span>  
 <span data-ttu-id="e6d35-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6d35-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d35-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e6d35-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6d35-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e6d35-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6d35-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d35-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d35-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6d35-136">See also</span></span>

- [<span data-ttu-id="e6d35-137">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e6d35-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
