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
ms.openlocfilehash: 1088374c9df18ded38b44384be44de245f0bd403
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728949"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="30274-102">ICLRPolicyManager::SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="30274-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>

<span data-ttu-id="30274-103">指定發生未處理的例外狀況時，common language runtime (CLR) 的行為。</span><span class="sxs-lookup"><span data-stu-id="30274-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30274-104">語法</span><span class="sxs-lookup"><span data-stu-id="30274-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30274-105">參數</span><span class="sxs-lookup"><span data-stu-id="30274-105">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="30274-106">在其中一個 [EClrUnhandledException](eclrunhandledexception-enumeration.md) 值，指出行為是由 CLR 或主控制項設定。</span><span class="sxs-lookup"><span data-stu-id="30274-106">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30274-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="30274-107">Return Value</span></span>  
  
|<span data-ttu-id="30274-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30274-108">HRESULT</span></span>|<span data-ttu-id="30274-109">描述</span><span class="sxs-lookup"><span data-stu-id="30274-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30274-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="30274-110">S_OK</span></span>|<span data-ttu-id="30274-111">`SetUnhandledExceptionPolicy` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="30274-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="30274-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30274-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30274-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="30274-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30274-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30274-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30274-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="30274-115">The call timed out.</span></span>|  
|<span data-ttu-id="30274-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30274-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30274-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="30274-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30274-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30274-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30274-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="30274-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30274-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30274-120">E_FAIL</span></span>|<span data-ttu-id="30274-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="30274-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30274-122">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="30274-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30274-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="30274-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30274-124">備註</span><span class="sxs-lookup"><span data-stu-id="30274-124">Remarks</span></span>  

 <span data-ttu-id="30274-125">根據預設，CLR 是所有未處理之例外狀況的最終處理常式，而其預設行為是卸載進程。</span><span class="sxs-lookup"><span data-stu-id="30274-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="30274-126">主機可以藉由將值設定為 eHostDeterminedPolicy 來變更此行為 `policy` 。</span><span class="sxs-lookup"><span data-stu-id="30274-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="30274-127">此值可讓主機執行它自己的預設行為，如同舊版的 CLR 一樣。</span><span class="sxs-lookup"><span data-stu-id="30274-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30274-128">需求</span><span class="sxs-lookup"><span data-stu-id="30274-128">Requirements</span></span>  

 <span data-ttu-id="30274-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30274-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30274-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="30274-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30274-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="30274-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30274-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30274-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30274-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30274-133">See also</span></span>

- [<span data-ttu-id="30274-134">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="30274-134">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="30274-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="30274-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="30274-136">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="30274-136">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="30274-137">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="30274-137">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
