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
ms.openlocfilehash: 32483be43d4d4fe9d185c091e15a13c6feb95600
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728819"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="730fd-102">ICLRRuntimeHost::SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="730fd-102">ICLRRuntimeHost::SetHostControl Method</span></span>

<span data-ttu-id="730fd-103">設定 common language runtime (CLR) 可用來取得主機 [IHostControl 介面](ihostcontrol-interface.md)之實作為的介面指標。</span><span class="sxs-lookup"><span data-stu-id="730fd-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="730fd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="730fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="730fd-105">Parameters</span></span>  

 `pHostControl`  
 <span data-ttu-id="730fd-106">在主機的 [IHostControl 介面](ihostcontrol-interface.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="730fd-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="730fd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="730fd-107">Return Value</span></span>  
  
|<span data-ttu-id="730fd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="730fd-108">HRESULT</span></span>|<span data-ttu-id="730fd-109">描述</span><span class="sxs-lookup"><span data-stu-id="730fd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="730fd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="730fd-110">S_OK</span></span>|<span data-ttu-id="730fd-111">`SetHostControl` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="730fd-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="730fd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="730fd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="730fd-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="730fd-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="730fd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="730fd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="730fd-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="730fd-115">The call timed out.</span></span>|  
|<span data-ttu-id="730fd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="730fd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="730fd-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="730fd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="730fd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="730fd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="730fd-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="730fd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="730fd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="730fd-120">E_FAIL</span></span>|<span data-ttu-id="730fd-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="730fd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="730fd-122">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="730fd-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="730fd-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="730fd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="730fd-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="730fd-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="730fd-125">CLR 已初始化。</span><span class="sxs-lookup"><span data-stu-id="730fd-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="730fd-126">備註</span><span class="sxs-lookup"><span data-stu-id="730fd-126">Remarks</span></span>  

 <span data-ttu-id="730fd-127">您必須在 `SetHostControl` CLR 初始化之前呼叫，也就是在呼叫 [Start 方法](iclrruntimehost-start-method.md) 或使用任何 [中繼資料介面](../metadata/metadata-interfaces.md)之前。</span><span class="sxs-lookup"><span data-stu-id="730fd-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="730fd-128">建議您在 `SetHostControl` 呼叫 [CorBindToCurrentRuntime 函數](corbindtocurrentruntime-function.md) 或 [CorBindToRuntimeEx 函數](corbindtoruntimeex-function.md)之後立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="730fd-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730fd-129">需求</span><span class="sxs-lookup"><span data-stu-id="730fd-129">Requirements</span></span>  

 <span data-ttu-id="730fd-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="730fd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="730fd-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="730fd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="730fd-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="730fd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="730fd-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="730fd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730fd-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="730fd-134">See also</span></span>

- [<span data-ttu-id="730fd-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="730fd-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="730fd-136">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="730fd-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
