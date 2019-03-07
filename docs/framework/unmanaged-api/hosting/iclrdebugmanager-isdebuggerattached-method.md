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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404d60bf0dfb8de1d7effae01b22b15e8931757c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473938"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="d6886-102">ICLRDebugManager::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="d6886-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="d6886-103">取得值，表示偵錯工具是否附加至處理序。</span><span class="sxs-lookup"><span data-stu-id="d6886-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6886-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6886-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6886-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6886-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d6886-106">[out]`true`偵錯工具附加至處理序，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="d6886-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6886-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d6886-107">Return Value</span></span>  
  
|<span data-ttu-id="d6886-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6886-108">HRESULT</span></span>|<span data-ttu-id="d6886-109">描述</span><span class="sxs-lookup"><span data-stu-id="d6886-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6886-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6886-110">S_OK</span></span>|<span data-ttu-id="d6886-111">`IsDebuggerAttached` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d6886-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="d6886-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6886-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6886-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d6886-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6886-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6886-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6886-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d6886-115">The call timed out.</span></span>|  
|<span data-ttu-id="d6886-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6886-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6886-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d6886-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6886-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6886-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6886-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d6886-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6886-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6886-120">E_FAIL</span></span>|<span data-ttu-id="d6886-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d6886-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6886-122">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d6886-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6886-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d6886-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6886-124">備註</span><span class="sxs-lookup"><span data-stu-id="d6886-124">Remarks</span></span>  
 <span data-ttu-id="d6886-125">`IsDebuggerAttached` 可讓查詢以判斷是否要將偵錯工具附加至處理程序的 CLR 主機。</span><span class="sxs-lookup"><span data-stu-id="d6886-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6886-126">需求</span><span class="sxs-lookup"><span data-stu-id="d6886-126">Requirements</span></span>  
 <span data-ttu-id="d6886-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6886-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6886-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6886-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6886-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d6886-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6886-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6886-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6886-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6886-131">See also</span></span>
- [<span data-ttu-id="d6886-132">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="d6886-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d6886-133">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="d6886-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="d6886-134">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="d6886-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
