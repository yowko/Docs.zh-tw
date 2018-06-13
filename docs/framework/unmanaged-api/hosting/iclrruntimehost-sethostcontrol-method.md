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
ms.openlocfilehash: 46cfaa5870d7bbc7edcbe438ddf57fe5f70ad938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434961"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="86ce4-102">ICLRRuntimeHost::SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="86ce4-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="86ce4-103">設定 common language runtime (CLR) 可用來取得主機實作的介面指標[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="86ce4-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ce4-104">語法</span><span class="sxs-lookup"><span data-stu-id="86ce4-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86ce4-105">參數</span><span class="sxs-lookup"><span data-stu-id="86ce4-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="86ce4-106">[in]主應用程式的實作的介面指標[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="86ce4-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86ce4-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="86ce4-107">Return Value</span></span>  
  
|<span data-ttu-id="86ce4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86ce4-108">HRESULT</span></span>|<span data-ttu-id="86ce4-109">描述</span><span class="sxs-lookup"><span data-stu-id="86ce4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86ce4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="86ce4-110">S_OK</span></span>|<span data-ttu-id="86ce4-111">`SetHostControl` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="86ce4-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="86ce4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86ce4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86ce4-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="86ce4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86ce4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86ce4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86ce4-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="86ce4-115">The call timed out.</span></span>|  
|<span data-ttu-id="86ce4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86ce4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86ce4-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="86ce4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86ce4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86ce4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86ce4-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="86ce4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86ce4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86ce4-120">E_FAIL</span></span>|<span data-ttu-id="86ce4-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="86ce4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86ce4-122">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="86ce4-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86ce4-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="86ce4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="86ce4-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="86ce4-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="86ce4-125">CLR 已經初始化。</span><span class="sxs-lookup"><span data-stu-id="86ce4-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86ce4-126">備註</span><span class="sxs-lookup"><span data-stu-id="86ce4-126">Remarks</span></span>  
 <span data-ttu-id="86ce4-127">您必須呼叫`SetHostControl`初始化 CLR 時，也就是在呼叫之前先[啟動方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)或使用任何[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="86ce4-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="86ce4-128">建議您呼叫`SetHostControl`後立即呼叫[CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)或[CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)。</span><span class="sxs-lookup"><span data-stu-id="86ce4-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86ce4-129">需求</span><span class="sxs-lookup"><span data-stu-id="86ce4-129">Requirements</span></span>  
 <span data-ttu-id="86ce4-130">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86ce4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86ce4-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86ce4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86ce4-132">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="86ce4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86ce4-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86ce4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ce4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86ce4-134">See Also</span></span>  
 [<span data-ttu-id="86ce4-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="86ce4-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="86ce4-136">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="86ce4-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
