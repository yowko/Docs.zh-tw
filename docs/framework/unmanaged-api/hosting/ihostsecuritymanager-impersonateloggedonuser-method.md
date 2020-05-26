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
ms.openlocfilehash: ada12a35691e0897a44f4f00e2e439fc08ef18af
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803898"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="9216d-102">IHostSecurityManager::ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="9216d-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="9216d-103">要求使用目前使用者識別的認證來執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="9216d-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9216d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9216d-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9216d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9216d-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="9216d-106">在Token，代表要模擬之使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="9216d-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9216d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9216d-107">Return Value</span></span>  
  
|<span data-ttu-id="9216d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9216d-108">HRESULT</span></span>|<span data-ttu-id="9216d-109">描述</span><span class="sxs-lookup"><span data-stu-id="9216d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9216d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9216d-110">S_OK</span></span>|<span data-ttu-id="9216d-111">`ImpersonateLoggedOnUser`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9216d-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="9216d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9216d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9216d-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9216d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9216d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9216d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9216d-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="9216d-115">The call timed out.</span></span>|  
|<span data-ttu-id="9216d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9216d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9216d-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9216d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9216d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9216d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9216d-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="9216d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9216d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9216d-120">E_FAIL</span></span>|<span data-ttu-id="9216d-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9216d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9216d-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="9216d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9216d-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9216d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9216d-124">備註</span><span class="sxs-lookup"><span data-stu-id="9216d-124">Remarks</span></span>  
 <span data-ttu-id="9216d-125">呼叫 `LogonUser` 或相關的 Win32 函式，以取得目前使用者識別之認證的控制碼。</span><span class="sxs-lookup"><span data-stu-id="9216d-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="9216d-126">`HANDLE`型別不符合 COM 標準，也就是說，它的大小是作業系統特有的，而且需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="9216d-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="9216d-127">因此，此權杖僅適用于在進程內的 CLR 與主控制項之間使用。</span><span class="sxs-lookup"><span data-stu-id="9216d-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9216d-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="9216d-128">Requirements</span></span>  
 <span data-ttu-id="9216d-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9216d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9216d-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="9216d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9216d-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9216d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9216d-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9216d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9216d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9216d-133">See also</span></span>

- [<span data-ttu-id="9216d-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="9216d-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="9216d-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="9216d-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="9216d-136">RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="9216d-136">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)
