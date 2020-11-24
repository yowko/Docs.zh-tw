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
ms.openlocfilehash: a54c25cb0cae906dc2d030900b9a1e1dbbbb2f1e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680517"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="21f1d-102">IHostSecurityManager::RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="21f1d-102">IHostSecurityManager::RevertToSelf Method</span></span>

<span data-ttu-id="21f1d-103">終止目前使用者身分識別的模擬，並傳回原始執行緒 token。</span><span class="sxs-lookup"><span data-stu-id="21f1d-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="21f1d-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="21f1d-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="21f1d-105">Return Value</span></span>  
  
|<span data-ttu-id="21f1d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21f1d-106">HRESULT</span></span>|<span data-ttu-id="21f1d-107">描述</span><span class="sxs-lookup"><span data-stu-id="21f1d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21f1d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="21f1d-108">S_OK</span></span>|<span data-ttu-id="21f1d-109">`RevertToSelf` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="21f1d-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="21f1d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21f1d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21f1d-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="21f1d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21f1d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21f1d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21f1d-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="21f1d-113">The call timed out.</span></span>|  
|<span data-ttu-id="21f1d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21f1d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21f1d-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="21f1d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21f1d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21f1d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21f1d-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="21f1d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21f1d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21f1d-118">E_FAIL</span></span>|<span data-ttu-id="21f1d-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="21f1d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21f1d-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="21f1d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21f1d-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="21f1d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21f1d-122">備註</span><span class="sxs-lookup"><span data-stu-id="21f1d-122">Remarks</span></span>  

 <span data-ttu-id="21f1d-123">`RevertToSelf` 在先前呼叫 [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) 方法之後，呼叫以返回原始執行緒標記。</span><span class="sxs-lookup"><span data-stu-id="21f1d-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f1d-124">需求</span><span class="sxs-lookup"><span data-stu-id="21f1d-124">Requirements</span></span>  

 <span data-ttu-id="21f1d-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21f1d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f1d-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="21f1d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21f1d-127">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="21f1d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21f1d-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f1d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f1d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21f1d-129">See also</span></span>

- [<span data-ttu-id="21f1d-130">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="21f1d-130">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="21f1d-131">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="21f1d-131">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="21f1d-132">ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="21f1d-132">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
