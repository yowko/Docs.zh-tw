---
title: "IHostSecurityManager::OpenThreadToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.OpenThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3b5ec31944b58bec6268de6e54503141880e6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="75b2d-102">IHostSecurityManager::OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="75b2d-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="75b2d-103">會開啟與目前執行中執行緒相關聯的判別存取語彙基元。</span><span class="sxs-lookup"><span data-stu-id="75b2d-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="75b2d-104">Syntax</span></span>  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75b2d-105">參數</span><span class="sxs-lookup"><span data-stu-id="75b2d-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="75b2d-106">[in]存取值，指定存取此執行緒語彙基元要求的類型的遮罩。</span><span class="sxs-lookup"><span data-stu-id="75b2d-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="75b2d-107">這些值會定義在 Win32`OpenThreadToken`函式。</span><span class="sxs-lookup"><span data-stu-id="75b2d-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="75b2d-108">必要的存取類型會調解對權杖的判別存取控制清單 (DACL) 來判斷哪些類型的存取權授與或拒絕。</span><span class="sxs-lookup"><span data-stu-id="75b2d-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="75b2d-109">[in]`true`來指定，應該使用的安全性內容的程序呼叫的執行緒; 進行存取檢查`false`來指定要執行呼叫的執行緒本身使用的安全性內容的存取檢查。</span><span class="sxs-lookup"><span data-stu-id="75b2d-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="75b2d-110">如果執行緒正在模擬用戶端，可以是用戶端處理序的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="75b2d-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="75b2d-111">[out]新開啟的存取語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="75b2d-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75b2d-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="75b2d-112">Return Value</span></span>  
  
|<span data-ttu-id="75b2d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75b2d-113">HRESULT</span></span>|<span data-ttu-id="75b2d-114">描述</span><span class="sxs-lookup"><span data-stu-id="75b2d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75b2d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="75b2d-115">S_OK</span></span>|<span data-ttu-id="75b2d-116">`OpenThreadToken`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="75b2d-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="75b2d-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="75b2d-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="75b2d-118">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="75b2d-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="75b2d-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="75b2d-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="75b2d-120">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="75b2d-120">The call timed out.</span></span>|  
|<span data-ttu-id="75b2d-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="75b2d-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="75b2d-122">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="75b2d-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="75b2d-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="75b2d-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="75b2d-124">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="75b2d-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="75b2d-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="75b2d-125">E_FAIL</span></span>|<span data-ttu-id="75b2d-126">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="75b2d-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="75b2d-127">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="75b2d-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="75b2d-128">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="75b2d-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75b2d-129">備註</span><span class="sxs-lookup"><span data-stu-id="75b2d-129">Remarks</span></span>  
 <span data-ttu-id="75b2d-130">`IHostSecurityManager::OpenThreadToken`行為類似對應的 Win32 函式的名稱相同，不同之處在於 Win32 函式可讓呼叫端来傳入任意的執行緒控制代碼，而`IHostSecurityManager::OpenThreadToken`開啟與呼叫執行緒相關聯的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="75b2d-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="75b2d-131">`HANDLE`類型不是 COM 相容，也就是它的大小是特定的作業系統，且其需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="75b2d-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="75b2d-132">因此，這個語彙基元是僅供處理程序，則 CLR 與主機之間。</span><span class="sxs-lookup"><span data-stu-id="75b2d-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75b2d-133">需求</span><span class="sxs-lookup"><span data-stu-id="75b2d-133">Requirements</span></span>  
 <span data-ttu-id="75b2d-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75b2d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75b2d-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75b2d-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75b2d-136">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="75b2d-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75b2d-137">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75b2d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b2d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75b2d-138">See Also</span></span>  
 [<span data-ttu-id="75b2d-139">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="75b2d-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="75b2d-140">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="75b2d-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
