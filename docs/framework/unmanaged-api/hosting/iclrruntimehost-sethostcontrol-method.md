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
ms.openlocfilehash: 644b31ae8e8f0c51c08bcad57220a028406cfd3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504068"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="813df-102">ICLRRuntimeHost::SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="813df-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="813df-103">設定 common language runtime （CLR）可用來取得[IHostControl 介面](ihostcontrol-interface.md)之主機的介面指標。</span><span class="sxs-lookup"><span data-stu-id="813df-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813df-104">語法</span><span class="sxs-lookup"><span data-stu-id="813df-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="813df-105">參數</span><span class="sxs-lookup"><span data-stu-id="813df-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="813df-106">在主機的[IHostControl 介面](ihostcontrol-interface.md)的介面指標。</span><span class="sxs-lookup"><span data-stu-id="813df-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="813df-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="813df-107">Return Value</span></span>  
  
|<span data-ttu-id="813df-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="813df-108">HRESULT</span></span>|<span data-ttu-id="813df-109">說明</span><span class="sxs-lookup"><span data-stu-id="813df-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="813df-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="813df-110">S_OK</span></span>|<span data-ttu-id="813df-111">`SetHostControl`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="813df-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="813df-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="813df-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="813df-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="813df-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="813df-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="813df-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="813df-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="813df-115">The call timed out.</span></span>|  
|<span data-ttu-id="813df-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="813df-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="813df-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="813df-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="813df-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="813df-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="813df-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="813df-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="813df-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="813df-120">E_FAIL</span></span>|<span data-ttu-id="813df-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="813df-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="813df-122">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="813df-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="813df-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="813df-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="813df-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="813df-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="813df-125">CLR 已經初始化。</span><span class="sxs-lookup"><span data-stu-id="813df-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="813df-126">備註</span><span class="sxs-lookup"><span data-stu-id="813df-126">Remarks</span></span>  
 <span data-ttu-id="813df-127">您必須在 `SetHostControl` CLR 初始化之前呼叫，也就是在呼叫[Start 方法](iclrruntimehost-start-method.md)或使用任何[中繼資料介面](../metadata/metadata-interfaces.md)之前。</span><span class="sxs-lookup"><span data-stu-id="813df-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="813df-128">建議您在 `SetHostControl` 呼叫[CorBindToCurrentRuntime 函數](corbindtocurrentruntime-function.md)或[CorBindToRuntimeEx 函數](corbindtoruntimeex-function.md)之後立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="813df-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="813df-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="813df-129">Requirements</span></span>  
 <span data-ttu-id="813df-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="813df-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="813df-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="813df-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="813df-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="813df-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="813df-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="813df-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813df-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="813df-134">See also</span></span>

- [<span data-ttu-id="813df-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="813df-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="813df-136">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="813df-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
