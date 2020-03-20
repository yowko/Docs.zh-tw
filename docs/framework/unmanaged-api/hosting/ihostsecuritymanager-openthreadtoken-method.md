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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176262"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="d7cfb-102">IHostSecurityManager::OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="d7cfb-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="d7cfb-103">打開與當前正在執行的執行緒關聯的可自由訪問權杖。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7cfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7cfb-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7cfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7cfb-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="d7cfb-106">[在]指定對執行緒權杖的請求訪問類型的訪問值的遮罩。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="d7cfb-107">這些值在 Win32`OpenThreadToken`函數中定義。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="d7cfb-108">請求的訪問類型與權杖的任意存取控制清單 （DACL） 協調，以確定授予或拒絕的訪問類型。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="d7cfb-109">[在]`true`指定應使用調用執行緒的進程的安全上下文進行訪問檢查;`false`指定應使用調用執行緒本身的安全上下文執行訪問檢查。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="d7cfb-110">如果執行緒正在類比用戶端，則安全上下文可以是用戶端進程的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="d7cfb-111">[出]指向新打開的訪問權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7cfb-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7cfb-112">Return Value</span></span>  
  
|<span data-ttu-id="d7cfb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7cfb-113">HRESULT</span></span>|<span data-ttu-id="d7cfb-114">描述</span><span class="sxs-lookup"><span data-stu-id="d7cfb-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7cfb-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7cfb-115">S_OK</span></span>|<span data-ttu-id="d7cfb-116">`OpenThreadToken`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="d7cfb-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7cfb-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7cfb-118">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7cfb-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7cfb-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7cfb-120">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-120">The call timed out.</span></span>|  
|<span data-ttu-id="d7cfb-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7cfb-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7cfb-122">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7cfb-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7cfb-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7cfb-124">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7cfb-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7cfb-125">E_FAIL</span></span>|<span data-ttu-id="d7cfb-126">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7cfb-127">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7cfb-128">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7cfb-129">備註</span><span class="sxs-lookup"><span data-stu-id="d7cfb-129">Remarks</span></span>  
 <span data-ttu-id="d7cfb-130">`IHostSecurityManager::OpenThreadToken`行為行為類似于同名的相應 Win32 函數，只不過 Win32 函數允許調用方在控制碼中傳遞到任意執行緒，同時`IHostSecurityManager::OpenThreadToken`僅打開與調用執行緒關聯的權杖。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="d7cfb-131">類型`HANDLE`不符合 COM，即其大小特定于作業系統，並且需要自訂封送。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="d7cfb-132">因此，此權杖僅用於進程，在 CLR 和主機之間。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7cfb-133">需求</span><span class="sxs-lookup"><span data-stu-id="d7cfb-133">Requirements</span></span>  
 <span data-ttu-id="d7cfb-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7cfb-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7cfb-135">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7cfb-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7cfb-136">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d7cfb-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7cfb-137">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7cfb-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cfb-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7cfb-138">See also</span></span>

- [<span data-ttu-id="d7cfb-139">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="d7cfb-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d7cfb-140">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="d7cfb-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
