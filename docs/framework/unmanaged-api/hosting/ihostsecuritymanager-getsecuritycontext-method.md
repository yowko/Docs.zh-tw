---
title: IHostSecurityManager::GetSecurityContext 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b379bb2a9512cd1bd3344ed7f5130f96c0ccfa87
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855573"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="868bf-102">IHostSecurityManager::GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="868bf-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="868bf-103">從主機取得要求的[IHostSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="868bf-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="868bf-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="868bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="868bf-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="868bf-106">在其中一個[ECoNtextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值，指出要傳回哪一種類型的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="868bf-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="868bf-107">脫銷的介面指標`IHostSecurityContext` `eContextType`位址。</span><span class="sxs-lookup"><span data-stu-id="868bf-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="868bf-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="868bf-108">Return Value</span></span>  
  
|<span data-ttu-id="868bf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="868bf-109">HRESULT</span></span>|<span data-ttu-id="868bf-110">說明</span><span class="sxs-lookup"><span data-stu-id="868bf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="868bf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="868bf-111">S_OK</span></span>|<span data-ttu-id="868bf-112">`GetSecurityContext`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="868bf-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="868bf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="868bf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="868bf-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="868bf-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="868bf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="868bf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="868bf-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="868bf-116">The call timed out.</span></span>|  
|<span data-ttu-id="868bf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="868bf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="868bf-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="868bf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="868bf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="868bf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="868bf-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="868bf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="868bf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="868bf-121">E_FAIL</span></span>|<span data-ttu-id="868bf-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="868bf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="868bf-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="868bf-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="868bf-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="868bf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="868bf-125">備註</span><span class="sxs-lookup"><span data-stu-id="868bf-125">Remarks</span></span>  
 <span data-ttu-id="868bf-126">主機可以同時控制 CLR 和使用者程式碼對執行緒標記的所有程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="868bf-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="868bf-127">它也可以確保以限制的程式碼存取，在非同步作業或程式碼點之間傳遞完整的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="868bf-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="868bf-128">`IHostSecurityContext`封裝此安全性內容資訊，這對 CLR 而言是不透明的。</span><span class="sxs-lookup"><span data-stu-id="868bf-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="868bf-129">CLR 會捕捉這項資訊，並將它移到執行緒集區的背景工作專案分派、完成項執行，以及模組和類別結構。</span><span class="sxs-lookup"><span data-stu-id="868bf-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="868bf-130">需求</span><span class="sxs-lookup"><span data-stu-id="868bf-130">Requirements</span></span>  
 <span data-ttu-id="868bf-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="868bf-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="868bf-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="868bf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="868bf-133">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="868bf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="868bf-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="868bf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868bf-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="868bf-135">See also</span></span>

- [<span data-ttu-id="868bf-136">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="868bf-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="868bf-137">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="868bf-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="868bf-138">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="868bf-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
