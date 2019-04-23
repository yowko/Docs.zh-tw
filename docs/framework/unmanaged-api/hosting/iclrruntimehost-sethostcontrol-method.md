---
title: ICLRRuntimeHost::SetHostControl 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6817a2154e876dfa83540e3496f42acdcdb25a83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198761"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="6c49f-102">ICLRRuntimeHost::SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="6c49f-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="6c49f-103">設定 common language runtime (CLR) 可用來取得主機實作的介面指標[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6c49f-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c49f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c49f-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c49f-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c49f-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="6c49f-106">[in]主機實作的介面指標[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6c49f-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c49f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c49f-107">Return Value</span></span>  
  
|<span data-ttu-id="6c49f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c49f-108">HRESULT</span></span>|<span data-ttu-id="6c49f-109">描述</span><span class="sxs-lookup"><span data-stu-id="6c49f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c49f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c49f-110">S_OK</span></span>|<span data-ttu-id="6c49f-111">`SetHostControl` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6c49f-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="6c49f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c49f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c49f-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6c49f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c49f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c49f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c49f-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6c49f-115">The call timed out.</span></span>|  
|<span data-ttu-id="6c49f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c49f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c49f-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6c49f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c49f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c49f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c49f-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6c49f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c49f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c49f-120">E_FAIL</span></span>|<span data-ttu-id="6c49f-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c49f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c49f-122">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="6c49f-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c49f-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6c49f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c49f-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="6c49f-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="6c49f-125">已初始化 CLR。</span><span class="sxs-lookup"><span data-stu-id="6c49f-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c49f-126">備註</span><span class="sxs-lookup"><span data-stu-id="6c49f-126">Remarks</span></span>  
 <span data-ttu-id="6c49f-127">您必須呼叫`SetHostControl`CLR 初始化時，也就是在呼叫之前先[啟動方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)，或使用任一[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="6c49f-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="6c49f-128">建議您呼叫`SetHostControl`後立即呼叫[CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)或是[CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)。</span><span class="sxs-lookup"><span data-stu-id="6c49f-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c49f-129">需求</span><span class="sxs-lookup"><span data-stu-id="6c49f-129">Requirements</span></span>  
 <span data-ttu-id="6c49f-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c49f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c49f-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c49f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c49f-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6c49f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c49f-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c49f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c49f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c49f-134">See also</span></span>

- [<span data-ttu-id="6c49f-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="6c49f-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="6c49f-136">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="6c49f-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
