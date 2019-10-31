---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 7b6a4be94e526e7b464b336d221eff936808635a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120577"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="d7393-102">ICLRPolicyManager::SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="d7393-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="d7393-103">當發生未處理的例外狀況時，指定 common language runtime （CLR）的行為。</span><span class="sxs-lookup"><span data-stu-id="d7393-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7393-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7393-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7393-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7393-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="d7393-106">在其中一個[EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)值，指出此行為是由 CLR 還是主機所設定。</span><span class="sxs-lookup"><span data-stu-id="d7393-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7393-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7393-107">Return Value</span></span>  
  
|<span data-ttu-id="d7393-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7393-108">HRESULT</span></span>|<span data-ttu-id="d7393-109">描述</span><span class="sxs-lookup"><span data-stu-id="d7393-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7393-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7393-110">S_OK</span></span>|<span data-ttu-id="d7393-111">已成功傳回 `SetUnhandledExceptionPolicy`。</span><span class="sxs-lookup"><span data-stu-id="d7393-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="d7393-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7393-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7393-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d7393-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7393-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7393-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7393-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d7393-115">The call timed out.</span></span>|  
|<span data-ttu-id="d7393-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7393-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7393-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d7393-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7393-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7393-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7393-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d7393-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7393-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7393-120">E_FAIL</span></span>|<span data-ttu-id="d7393-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d7393-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7393-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d7393-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7393-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d7393-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7393-124">備註</span><span class="sxs-lookup"><span data-stu-id="d7393-124">Remarks</span></span>  
 <span data-ttu-id="d7393-125">根據預設，CLR 是所有未處理之例外狀況的最後處理常式，而其預設行為是卸載進程。</span><span class="sxs-lookup"><span data-stu-id="d7393-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="d7393-126">主機可以藉由將 `policy` 值設定為 eHostDeterminedPolicy 來變更此行為。</span><span class="sxs-lookup"><span data-stu-id="d7393-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="d7393-127">此值可讓主機執行它自己的預設行為，如同舊版的 CLR。</span><span class="sxs-lookup"><span data-stu-id="d7393-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7393-128">需求</span><span class="sxs-lookup"><span data-stu-id="d7393-128">Requirements</span></span>  
 <span data-ttu-id="d7393-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7393-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7393-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d7393-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7393-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d7393-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7393-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7393-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7393-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7393-133">See also</span></span>

- [<span data-ttu-id="d7393-134">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="d7393-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="d7393-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="d7393-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d7393-136">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="d7393-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d7393-137">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="d7393-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
