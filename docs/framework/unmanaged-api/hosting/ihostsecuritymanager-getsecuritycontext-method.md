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
ms.openlocfilehash: e43eb7ebfc367e7d4a7a209a5037fcc4566cd7ec
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803932"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="080e8-102">IHostSecurityManager::GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="080e8-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="080e8-103">從主機取得要求的[IHostSecurityCoNtext](ihostsecuritycontext-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="080e8-103">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="080e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="080e8-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="080e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="080e8-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="080e8-106">在其中一個[ECoNtextType](econtexttype-enumeration.md)值，指出要傳回哪一種類型的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="080e8-106">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="080e8-107">脫銷的介面指標位址 `IHostSecurityContext` `eContextType` 。</span><span class="sxs-lookup"><span data-stu-id="080e8-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="080e8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="080e8-108">Return Value</span></span>  
  
|<span data-ttu-id="080e8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="080e8-109">HRESULT</span></span>|<span data-ttu-id="080e8-110">描述</span><span class="sxs-lookup"><span data-stu-id="080e8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="080e8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="080e8-111">S_OK</span></span>|<span data-ttu-id="080e8-112">`GetSecurityContext`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="080e8-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="080e8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="080e8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="080e8-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="080e8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="080e8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="080e8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="080e8-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="080e8-116">The call timed out.</span></span>|  
|<span data-ttu-id="080e8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="080e8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="080e8-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="080e8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="080e8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="080e8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="080e8-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="080e8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="080e8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="080e8-121">E_FAIL</span></span>|<span data-ttu-id="080e8-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="080e8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="080e8-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="080e8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="080e8-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="080e8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="080e8-125">備註</span><span class="sxs-lookup"><span data-stu-id="080e8-125">Remarks</span></span>  
 <span data-ttu-id="080e8-126">主機可以同時控制 CLR 和使用者程式碼對執行緒標記的所有程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="080e8-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="080e8-127">它也可以確保以限制的程式碼存取，在非同步作業或程式碼點之間傳遞完整的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="080e8-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="080e8-128">`IHostSecurityContext`封裝此安全性內容資訊，這對 CLR 而言是不透明的。</span><span class="sxs-lookup"><span data-stu-id="080e8-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="080e8-129">CLR 會捕捉這項資訊，並將它移到執行緒集區的背景工作專案分派、完成項執行，以及模組和類別結構。</span><span class="sxs-lookup"><span data-stu-id="080e8-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="080e8-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="080e8-130">Requirements</span></span>  
 <span data-ttu-id="080e8-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="080e8-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="080e8-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="080e8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="080e8-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="080e8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="080e8-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="080e8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="080e8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="080e8-135">See also</span></span>

- [<span data-ttu-id="080e8-136">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="080e8-136">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="080e8-137">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="080e8-137">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="080e8-138">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="080e8-138">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
