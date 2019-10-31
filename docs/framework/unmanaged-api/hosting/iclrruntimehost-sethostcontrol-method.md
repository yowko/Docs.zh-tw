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
ms.openlocfilehash: 68b06a2840de277bdaed1dc9ce0b51e6b363c897
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120457"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="f6dba-102">ICLRRuntimeHost::SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="f6dba-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="f6dba-103">設定 common language runtime （CLR）可用來取得[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)之主機的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f6dba-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6dba-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6dba-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6dba-105">參數</span><span class="sxs-lookup"><span data-stu-id="f6dba-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="f6dba-106">在主機的[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f6dba-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6dba-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f6dba-107">Return Value</span></span>  
  
|<span data-ttu-id="f6dba-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6dba-108">HRESULT</span></span>|<span data-ttu-id="f6dba-109">描述</span><span class="sxs-lookup"><span data-stu-id="f6dba-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6dba-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6dba-110">S_OK</span></span>|<span data-ttu-id="f6dba-111">已成功傳回 `SetHostControl`。</span><span class="sxs-lookup"><span data-stu-id="f6dba-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="f6dba-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6dba-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6dba-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f6dba-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6dba-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6dba-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6dba-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f6dba-115">The call timed out.</span></span>|  
|<span data-ttu-id="f6dba-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6dba-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6dba-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f6dba-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6dba-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6dba-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6dba-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="f6dba-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6dba-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6dba-120">E_FAIL</span></span>|<span data-ttu-id="f6dba-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f6dba-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6dba-122">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f6dba-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6dba-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f6dba-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f6dba-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="f6dba-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="f6dba-125">CLR 已經初始化。</span><span class="sxs-lookup"><span data-stu-id="f6dba-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6dba-126">備註</span><span class="sxs-lookup"><span data-stu-id="f6dba-126">Remarks</span></span>  
 <span data-ttu-id="f6dba-127">在初始化 CLR 之前，您必須先呼叫 `SetHostControl`，也就是在呼叫[Start 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)或使用任何[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)之前。</span><span class="sxs-lookup"><span data-stu-id="f6dba-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="f6dba-128">建議您在呼叫[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)函式或[CorBindToRuntimeEx 函數](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)之後，立即呼叫 `SetHostControl`。</span><span class="sxs-lookup"><span data-stu-id="f6dba-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6dba-129">需求</span><span class="sxs-lookup"><span data-stu-id="f6dba-129">Requirements</span></span>  
 <span data-ttu-id="f6dba-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6dba-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6dba-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f6dba-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6dba-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f6dba-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6dba-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6dba-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6dba-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6dba-134">See also</span></span>

- [<span data-ttu-id="f6dba-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="f6dba-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="f6dba-136">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="f6dba-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
