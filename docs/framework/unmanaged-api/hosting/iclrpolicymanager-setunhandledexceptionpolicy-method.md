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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab00ccd85481f1c6d37e1132e0ecab5e0e86be90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768884"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="28430-102">ICLRPolicyManager::SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="28430-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="28430-103">發生未處理的例外狀況時，請指定 common language runtime (CLR) 的行為。</span><span class="sxs-lookup"><span data-stu-id="28430-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28430-104">語法</span><span class="sxs-lookup"><span data-stu-id="28430-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28430-105">參數</span><span class="sxs-lookup"><span data-stu-id="28430-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="28430-106">[in]其中一個[EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)值，指出是否由 CLR 或主應用程式設定此行為。</span><span class="sxs-lookup"><span data-stu-id="28430-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28430-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="28430-107">Return Value</span></span>  
  
|<span data-ttu-id="28430-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28430-108">HRESULT</span></span>|<span data-ttu-id="28430-109">描述</span><span class="sxs-lookup"><span data-stu-id="28430-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28430-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="28430-110">S_OK</span></span>|<span data-ttu-id="28430-111">`SetUnhandledExceptionPolicy` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="28430-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="28430-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28430-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28430-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="28430-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28430-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28430-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28430-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="28430-115">The call timed out.</span></span>|  
|<span data-ttu-id="28430-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28430-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28430-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="28430-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28430-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28430-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28430-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="28430-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28430-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28430-120">E_FAIL</span></span>|<span data-ttu-id="28430-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="28430-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28430-122">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="28430-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28430-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="28430-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28430-124">備註</span><span class="sxs-lookup"><span data-stu-id="28430-124">Remarks</span></span>  
 <span data-ttu-id="28430-125">根據預設，CLR 是所有未處理的例外狀況的最後一個處理常式，以及其預設行為是要卸除程序。</span><span class="sxs-lookup"><span data-stu-id="28430-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="28430-126">主機可以變更此行為，藉由設定`policy`eHostDeterminedPolicy 的值。</span><span class="sxs-lookup"><span data-stu-id="28430-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="28430-127">這個值表示允許主應用程式實作自己的預設行為，如同舊版的 CLR。</span><span class="sxs-lookup"><span data-stu-id="28430-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28430-128">需求</span><span class="sxs-lookup"><span data-stu-id="28430-128">Requirements</span></span>  
 <span data-ttu-id="28430-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28430-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28430-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28430-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28430-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="28430-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28430-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28430-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28430-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28430-133">See also</span></span>

- [<span data-ttu-id="28430-134">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="28430-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="28430-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="28430-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="28430-136">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="28430-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="28430-137">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="28430-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
