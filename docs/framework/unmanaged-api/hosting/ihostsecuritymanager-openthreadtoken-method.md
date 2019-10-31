---
title: IHostSecurityManager::OpenThreadToken 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 2ced153798355aff882f0244f3dd946c39dea2bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121474"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="2419b-102">IHostSecurityManager::OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="2419b-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="2419b-103">開啟與目前執行中線程相關聯的任意存取權杖。</span><span class="sxs-lookup"><span data-stu-id="2419b-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2419b-104">語法</span><span class="sxs-lookup"><span data-stu-id="2419b-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2419b-105">參數</span><span class="sxs-lookup"><span data-stu-id="2419b-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="2419b-106">在存取值的遮罩，指定對執行緒 token 所要求的存取類型。</span><span class="sxs-lookup"><span data-stu-id="2419b-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="2419b-107">這些值是在 Win32 `OpenThreadToken` 函數中定義。</span><span class="sxs-lookup"><span data-stu-id="2419b-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="2419b-108">要求的存取類型會與權杖的任意存取控制清單（DACL）進行協調，以決定要授與或拒絕哪些類型的存取權。</span><span class="sxs-lookup"><span data-stu-id="2419b-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="2419b-109">[in] `true` 指定應該使用呼叫執行緒之進程的安全性內容來進行存取檢查;`false`，指定應該使用呼叫執行緒本身的安全性內容來執行存取檢查。</span><span class="sxs-lookup"><span data-stu-id="2419b-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="2419b-110">如果執行緒正在模擬用戶端，則安全性內容可以是用戶端進程的其中一個。</span><span class="sxs-lookup"><span data-stu-id="2419b-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="2419b-111">脫銷新開啟之存取權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="2419b-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2419b-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2419b-112">Return Value</span></span>  
  
|<span data-ttu-id="2419b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2419b-113">HRESULT</span></span>|<span data-ttu-id="2419b-114">描述</span><span class="sxs-lookup"><span data-stu-id="2419b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2419b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2419b-115">S_OK</span></span>|<span data-ttu-id="2419b-116">已成功傳回 `OpenThreadToken`。</span><span class="sxs-lookup"><span data-stu-id="2419b-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="2419b-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2419b-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2419b-118">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2419b-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2419b-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2419b-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2419b-120">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2419b-120">The call timed out.</span></span>|  
|<span data-ttu-id="2419b-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2419b-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2419b-122">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2419b-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2419b-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2419b-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2419b-124">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2419b-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2419b-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2419b-125">E_FAIL</span></span>|<span data-ttu-id="2419b-126">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2419b-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2419b-127">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2419b-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2419b-128">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2419b-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2419b-129">備註</span><span class="sxs-lookup"><span data-stu-id="2419b-129">Remarks</span></span>  
 <span data-ttu-id="2419b-130">`IHostSecurityManager::OpenThreadToken` 的行為類似于相同名稱的對應 Win32 函式，不同之處在于 Win32 函式允許呼叫端將控制碼傳入任意執行緒，而 `IHostSecurityManager::OpenThreadToken` 只會開啟與呼叫執行緒相關聯的 token。</span><span class="sxs-lookup"><span data-stu-id="2419b-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="2419b-131">`HANDLE` 類型不符合 COM 標準，也就是說，它的大小是作業系統特有的，而且需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="2419b-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="2419b-132">因此，此權杖僅適用于在進程內的 CLR 與主控制項之間使用。</span><span class="sxs-lookup"><span data-stu-id="2419b-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2419b-133">需求</span><span class="sxs-lookup"><span data-stu-id="2419b-133">Requirements</span></span>  
 <span data-ttu-id="2419b-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2419b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2419b-135">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2419b-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2419b-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2419b-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2419b-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2419b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2419b-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="2419b-138">See also</span></span>

- [<span data-ttu-id="2419b-139">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="2419b-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="2419b-140">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="2419b-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
