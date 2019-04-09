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
ms.openlocfilehash: 1d6c071b3ac68cb38fc85aff65fff49a71ea4275
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095383"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="5249b-102">ICLRDebugManager::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="5249b-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="5249b-103">取得值，表示偵錯工具是否附加至處理序。</span><span class="sxs-lookup"><span data-stu-id="5249b-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5249b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5249b-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5249b-105">參數</span><span class="sxs-lookup"><span data-stu-id="5249b-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="5249b-106">[out]`true`偵錯工具附加至處理序，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="5249b-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5249b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5249b-107">Return Value</span></span>  
  
|<span data-ttu-id="5249b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5249b-108">HRESULT</span></span>|<span data-ttu-id="5249b-109">描述</span><span class="sxs-lookup"><span data-stu-id="5249b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5249b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5249b-110">S_OK</span></span>|`IsDebuggerAttached` <span data-ttu-id="5249b-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5249b-111">returned successfully.</span></span>|  
|<span data-ttu-id="5249b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5249b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5249b-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5249b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5249b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5249b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5249b-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5249b-115">The call timed out.</span></span>|  
|<span data-ttu-id="5249b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5249b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5249b-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5249b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5249b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5249b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5249b-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5249b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5249b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5249b-120">E_FAIL</span></span>|<span data-ttu-id="5249b-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="5249b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5249b-122">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="5249b-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5249b-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5249b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5249b-124">備註</span><span class="sxs-lookup"><span data-stu-id="5249b-124">Remarks</span></span>  
 `IsDebuggerAttached` <span data-ttu-id="5249b-125">可讓查詢以判斷是否要將偵錯工具附加至處理程序的 CLR 主機。</span><span class="sxs-lookup"><span data-stu-id="5249b-125">allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5249b-126">需求</span><span class="sxs-lookup"><span data-stu-id="5249b-126">Requirements</span></span>  
 <span data-ttu-id="5249b-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5249b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5249b-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5249b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5249b-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5249b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5249b-130">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5249b-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5249b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5249b-131">See also</span></span>

- [<span data-ttu-id="5249b-132">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="5249b-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="5249b-133">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="5249b-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="5249b-134">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="5249b-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
