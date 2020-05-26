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
ms.openlocfilehash: 456553e4cb5a6c6a557b5c3ac677fad12a5798bf
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803822"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="23f06-102">IHostSecurityManager::RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="23f06-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="23f06-103">終止目前使用者身分識別的模擬，並傳回原始的執行緒 token。</span><span class="sxs-lookup"><span data-stu-id="23f06-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f06-104">語法</span><span class="sxs-lookup"><span data-stu-id="23f06-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="23f06-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="23f06-105">Return Value</span></span>  
  
|<span data-ttu-id="23f06-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23f06-106">HRESULT</span></span>|<span data-ttu-id="23f06-107">描述</span><span class="sxs-lookup"><span data-stu-id="23f06-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23f06-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="23f06-108">S_OK</span></span>|<span data-ttu-id="23f06-109">`RevertToSelf`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="23f06-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="23f06-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23f06-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23f06-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="23f06-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="23f06-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23f06-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="23f06-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="23f06-113">The call timed out.</span></span>|  
|<span data-ttu-id="23f06-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="23f06-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="23f06-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="23f06-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="23f06-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="23f06-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="23f06-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="23f06-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="23f06-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23f06-118">E_FAIL</span></span>|<span data-ttu-id="23f06-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="23f06-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="23f06-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="23f06-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="23f06-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="23f06-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23f06-122">備註</span><span class="sxs-lookup"><span data-stu-id="23f06-122">Remarks</span></span>  
 <span data-ttu-id="23f06-123">`RevertToSelf`呼叫[ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md)方法之後，會呼叫以回到原始執行緒標記。</span><span class="sxs-lookup"><span data-stu-id="23f06-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f06-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="23f06-124">Requirements</span></span>  
 <span data-ttu-id="23f06-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23f06-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f06-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="23f06-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23f06-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="23f06-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23f06-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f06-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f06-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23f06-129">See also</span></span>

- [<span data-ttu-id="23f06-130">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="23f06-130">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="23f06-131">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="23f06-131">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="23f06-132">ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="23f06-132">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
