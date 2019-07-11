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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1beeb0ff6b2e3493f0814fc3371f189bd4d485d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778015"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="e8562-102">IHostSecurityManager::OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="e8562-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="e8562-103">開啟與目前執行中執行緒相關聯的 discretionary 存取權杖。</span><span class="sxs-lookup"><span data-stu-id="e8562-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8562-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8562-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8562-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8562-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="e8562-106">[in]存取值，指定的存取權的執行緒 token 的要求的類型的遮罩。</span><span class="sxs-lookup"><span data-stu-id="e8562-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="e8562-107">這些值會定義在 Win32 中`OpenThreadToken`函式。</span><span class="sxs-lookup"><span data-stu-id="e8562-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="e8562-108">要求的存取類型會協調對權杖的判別存取控制清單 (DACL)，以判斷哪些類型的存取權授與或拒絕。</span><span class="sxs-lookup"><span data-stu-id="e8562-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="e8562-109">[in]`true`來指定應該使用的安全性內容的程序呼叫的執行緒; 會建立在存取檢查`false`可以指定應該使用的安全性內容呼叫的執行緒本身要執行存取檢查。</span><span class="sxs-lookup"><span data-stu-id="e8562-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="e8562-110">如果執行緒模擬用戶端，可以是安全性內容的用戶端處理序。</span><span class="sxs-lookup"><span data-stu-id="e8562-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="e8562-111">[out]新開啟的存取語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="e8562-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8562-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="e8562-112">Return Value</span></span>  
  
|<span data-ttu-id="e8562-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8562-113">HRESULT</span></span>|<span data-ttu-id="e8562-114">描述</span><span class="sxs-lookup"><span data-stu-id="e8562-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8562-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8562-115">S_OK</span></span>|<span data-ttu-id="e8562-116">`OpenThreadToken` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e8562-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="e8562-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8562-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8562-118">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e8562-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8562-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8562-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8562-120">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e8562-120">The call timed out.</span></span>|  
|<span data-ttu-id="e8562-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8562-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8562-122">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e8562-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8562-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8562-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8562-124">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e8562-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8562-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8562-125">E_FAIL</span></span>|<span data-ttu-id="e8562-126">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8562-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8562-127">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="e8562-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8562-128">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e8562-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8562-129">備註</span><span class="sxs-lookup"><span data-stu-id="e8562-129">Remarks</span></span>  
 <span data-ttu-id="e8562-130">`IHostSecurityManager::OpenThreadToken` 行為類似對應的 Win32 函式的名稱相同，不同之處在於 Win32 函式可讓呼叫者傳入任意的執行緒控制代碼，而`IHostSecurityManager::OpenThreadToken`開啟呼叫的執行緒相關聯的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e8562-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="e8562-131">`HANDLE`類型不是 COM 相容，也就是它的大小是特定作業系統，而且需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="e8562-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="e8562-132">因此，此權杖是只在處理序中，CLR 和主機之間使用。</span><span class="sxs-lookup"><span data-stu-id="e8562-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8562-133">需求</span><span class="sxs-lookup"><span data-stu-id="e8562-133">Requirements</span></span>  
 <span data-ttu-id="e8562-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8562-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8562-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8562-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8562-136">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e8562-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8562-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8562-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8562-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8562-138">See also</span></span>

- [<span data-ttu-id="e8562-139">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="e8562-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="e8562-140">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="e8562-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
