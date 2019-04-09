---
title: IHostSecurityManager::RevertToSelf 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d282f6d37a2be8a41f4fbda579b3b467b9bfc8ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120064"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="d4718-102">IHostSecurityManager::RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="d4718-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="d4718-103">終止目前的使用者身分識別模擬，並傳回原始的執行緒 token。</span><span class="sxs-lookup"><span data-stu-id="d4718-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4718-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4718-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d4718-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4718-105">Return Value</span></span>  
  
|<span data-ttu-id="d4718-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4718-106">HRESULT</span></span>|<span data-ttu-id="d4718-107">描述</span><span class="sxs-lookup"><span data-stu-id="d4718-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4718-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4718-108">S_OK</span></span>|`RevertToSelf` <span data-ttu-id="d4718-109">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d4718-109">returned successfully.</span></span>|  
|<span data-ttu-id="d4718-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4718-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4718-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d4718-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4718-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4718-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4718-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d4718-113">The call timed out.</span></span>|  
|<span data-ttu-id="d4718-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4718-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4718-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d4718-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4718-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4718-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4718-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d4718-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4718-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4718-118">E_FAIL</span></span>|<span data-ttu-id="d4718-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4718-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4718-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d4718-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4718-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d4718-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4718-122">備註</span><span class="sxs-lookup"><span data-stu-id="d4718-122">Remarks</span></span>  
 `RevertToSelf` <span data-ttu-id="d4718-123">呼叫以傳回至原始的執行緒 token，在先前呼叫後[ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d4718-123">is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4718-124">需求</span><span class="sxs-lookup"><span data-stu-id="d4718-124">Requirements</span></span>  
 <span data-ttu-id="d4718-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4718-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4718-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4718-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4718-127">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d4718-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d4718-128">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d4718-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4718-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4718-129">See also</span></span>

- [<span data-ttu-id="d4718-130">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="d4718-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d4718-131">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="d4718-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="d4718-132">ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="d4718-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
