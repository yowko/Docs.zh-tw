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
ms.openlocfilehash: a21391f52a27e7f7a3abe533499c6b2581ec4a73
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615735"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="d6324-102">ICLRDebugManager::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="d6324-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="d6324-103">取得值，表示偵錯工具是否附加至處理序。</span><span class="sxs-lookup"><span data-stu-id="d6324-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6324-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6324-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6324-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6324-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d6324-106">[out] `true`如果偵錯工具已附加至進程，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="d6324-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6324-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d6324-107">Return Value</span></span>  
  
|<span data-ttu-id="d6324-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6324-108">HRESULT</span></span>|<span data-ttu-id="d6324-109">說明</span><span class="sxs-lookup"><span data-stu-id="d6324-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6324-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6324-110">S_OK</span></span>|<span data-ttu-id="d6324-111">`IsDebuggerAttached`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d6324-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="d6324-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6324-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6324-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d6324-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6324-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6324-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6324-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d6324-115">The call timed out.</span></span>|  
|<span data-ttu-id="d6324-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6324-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6324-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d6324-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6324-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6324-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6324-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d6324-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6324-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6324-120">E_FAIL</span></span>|<span data-ttu-id="d6324-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d6324-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6324-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d6324-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6324-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d6324-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6324-124">備註</span><span class="sxs-lookup"><span data-stu-id="d6324-124">Remarks</span></span>  
 <span data-ttu-id="d6324-125">`IsDebuggerAttached`允許主機查詢 CLR，以判斷偵錯工具是否附加至進程。</span><span class="sxs-lookup"><span data-stu-id="d6324-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6324-126">需求</span><span class="sxs-lookup"><span data-stu-id="d6324-126">Requirements</span></span>  
 <span data-ttu-id="d6324-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6324-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6324-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d6324-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6324-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d6324-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6324-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6324-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6324-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6324-131">See also</span></span>

- [<span data-ttu-id="d6324-132">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="d6324-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d6324-133">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="d6324-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="d6324-134">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="d6324-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)
