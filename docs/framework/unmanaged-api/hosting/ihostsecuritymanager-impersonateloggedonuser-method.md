---
title: IHostSecurityManager::ImpersonateLoggedOnUser 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: 93051ca9a0b6f57f41d0d17335a838fe92832d8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121489"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="5654a-102">IHostSecurityManager::ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="5654a-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="5654a-103">要求使用目前使用者識別的認證來執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="5654a-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5654a-104">語法</span><span class="sxs-lookup"><span data-stu-id="5654a-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5654a-105">參數</span><span class="sxs-lookup"><span data-stu-id="5654a-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="5654a-106">在Token，代表要模擬之使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="5654a-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5654a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5654a-107">Return Value</span></span>  
  
|<span data-ttu-id="5654a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5654a-108">HRESULT</span></span>|<span data-ttu-id="5654a-109">描述</span><span class="sxs-lookup"><span data-stu-id="5654a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5654a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5654a-110">S_OK</span></span>|<span data-ttu-id="5654a-111">已成功傳回 `ImpersonateLoggedOnUser`。</span><span class="sxs-lookup"><span data-stu-id="5654a-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="5654a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5654a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5654a-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5654a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5654a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5654a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5654a-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="5654a-115">The call timed out.</span></span>|  
|<span data-ttu-id="5654a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5654a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5654a-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5654a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5654a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5654a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5654a-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="5654a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5654a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5654a-120">E_FAIL</span></span>|<span data-ttu-id="5654a-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5654a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5654a-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="5654a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5654a-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5654a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5654a-124">備註</span><span class="sxs-lookup"><span data-stu-id="5654a-124">Remarks</span></span>  
 <span data-ttu-id="5654a-125">呼叫 `LogonUser` 或相關的 Win32 函式，以取得目前使用者識別之認證的控制碼。</span><span class="sxs-lookup"><span data-stu-id="5654a-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="5654a-126">`HANDLE` 類型不符合 COM 標準，也就是說，它的大小是作業系統特有的，而且需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="5654a-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="5654a-127">因此，此權杖僅適用于在進程內的 CLR 與主控制項之間使用。</span><span class="sxs-lookup"><span data-stu-id="5654a-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5654a-128">需求</span><span class="sxs-lookup"><span data-stu-id="5654a-128">Requirements</span></span>  
 <span data-ttu-id="5654a-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5654a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5654a-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5654a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5654a-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5654a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5654a-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5654a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5654a-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="5654a-133">See also</span></span>

- [<span data-ttu-id="5654a-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="5654a-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="5654a-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="5654a-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="5654a-136">RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="5654a-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
