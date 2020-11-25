---
title: ICLRDebugManager::IsDebuggerAttached 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: 71e11d7db3bd679e7972fb2f6ce098edc3399885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731016"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="beb8a-102">ICLRDebugManager::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="beb8a-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>

<span data-ttu-id="beb8a-103">取得值，表示偵錯工具是否附加至處理序。</span><span class="sxs-lookup"><span data-stu-id="beb8a-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="beb8a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beb8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="beb8a-105">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="beb8a-106">[out] `true` 如果偵錯工具已附加至進程，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="beb8a-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="beb8a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="beb8a-107">Return Value</span></span>  
  
|<span data-ttu-id="beb8a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="beb8a-108">HRESULT</span></span>|<span data-ttu-id="beb8a-109">描述</span><span class="sxs-lookup"><span data-stu-id="beb8a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="beb8a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="beb8a-110">S_OK</span></span>|<span data-ttu-id="beb8a-111">`IsDebuggerAttached` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="beb8a-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="beb8a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="beb8a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="beb8a-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="beb8a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="beb8a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="beb8a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="beb8a-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="beb8a-115">The call timed out.</span></span>|  
|<span data-ttu-id="beb8a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="beb8a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="beb8a-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="beb8a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="beb8a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="beb8a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="beb8a-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="beb8a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="beb8a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="beb8a-120">E_FAIL</span></span>|<span data-ttu-id="beb8a-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="beb8a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="beb8a-122">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="beb8a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="beb8a-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="beb8a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beb8a-124">備註</span><span class="sxs-lookup"><span data-stu-id="beb8a-124">Remarks</span></span>  

 <span data-ttu-id="beb8a-125">`IsDebuggerAttached` 允許主控制項查詢 CLR，以判斷偵錯工具是否已附加至進程。</span><span class="sxs-lookup"><span data-stu-id="beb8a-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb8a-126">需求</span><span class="sxs-lookup"><span data-stu-id="beb8a-126">Requirements</span></span>  

 <span data-ttu-id="beb8a-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="beb8a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb8a-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="beb8a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="beb8a-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="beb8a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="beb8a-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beb8a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb8a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beb8a-131">See also</span></span>

- [<span data-ttu-id="beb8a-132">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="beb8a-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="beb8a-133">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="beb8a-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="beb8a-134">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="beb8a-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)
