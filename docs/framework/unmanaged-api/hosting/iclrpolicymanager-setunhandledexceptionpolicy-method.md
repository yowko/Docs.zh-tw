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
ms.openlocfilehash: 7fa02c4c79da118543117aada7d1b9cca09c4cae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703396"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="df000-102">ICLRPolicyManager::SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="df000-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="df000-103">當發生未處理的例外狀況時，指定 common language runtime （CLR）的行為。</span><span class="sxs-lookup"><span data-stu-id="df000-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df000-104">語法</span><span class="sxs-lookup"><span data-stu-id="df000-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df000-105">參數</span><span class="sxs-lookup"><span data-stu-id="df000-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="df000-106">在其中一個[EClrUnhandledException](eclrunhandledexception-enumeration.md)值，指出此行為是由 CLR 還是主機所設定。</span><span class="sxs-lookup"><span data-stu-id="df000-106">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df000-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="df000-107">Return Value</span></span>  
  
|<span data-ttu-id="df000-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df000-108">HRESULT</span></span>|<span data-ttu-id="df000-109">說明</span><span class="sxs-lookup"><span data-stu-id="df000-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df000-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="df000-110">S_OK</span></span>|<span data-ttu-id="df000-111">`SetUnhandledExceptionPolicy`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="df000-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="df000-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df000-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df000-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="df000-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="df000-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="df000-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="df000-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="df000-115">The call timed out.</span></span>|  
|<span data-ttu-id="df000-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="df000-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="df000-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="df000-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="df000-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="df000-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="df000-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="df000-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="df000-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df000-120">E_FAIL</span></span>|<span data-ttu-id="df000-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="df000-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="df000-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="df000-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="df000-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="df000-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df000-124">備註</span><span class="sxs-lookup"><span data-stu-id="df000-124">Remarks</span></span>  
 <span data-ttu-id="df000-125">根據預設，CLR 是所有未處理之例外狀況的最後處理常式，而其預設行為是卸載進程。</span><span class="sxs-lookup"><span data-stu-id="df000-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="df000-126">主機可以藉由將值設定為 eHostDeterminedPolicy 來變更此行為 `policy` 。</span><span class="sxs-lookup"><span data-stu-id="df000-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="df000-127">此值可讓主機執行它自己的預設行為，如同舊版的 CLR。</span><span class="sxs-lookup"><span data-stu-id="df000-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df000-128">需求</span><span class="sxs-lookup"><span data-stu-id="df000-128">Requirements</span></span>  
 <span data-ttu-id="df000-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df000-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df000-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="df000-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df000-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="df000-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df000-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df000-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df000-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df000-133">See also</span></span>

- [<span data-ttu-id="df000-134">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="df000-134">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="df000-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="df000-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="df000-136">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="df000-136">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="df000-137">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="df000-137">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
