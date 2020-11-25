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
ms.openlocfilehash: dfb96de02549e6d0f178c099793741f7fbd61d55
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724789"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="d7c62-102">IHostSecurityManager::GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="d7c62-102">IHostSecurityManager::GetSecurityContext Method</span></span>

<span data-ttu-id="d7c62-103">從主機取得要求的 [IHostSecurityCoNtext](ihostsecuritycontext-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="d7c62-103">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c62-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7c62-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7c62-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7c62-105">Parameters</span></span>  

 `eContextType`  
 <span data-ttu-id="d7c62-106">在其中一個 [ECoNtextType](econtexttype-enumeration.md) 值，指出要傳回哪一種類型的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="d7c62-106">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="d7c62-107">擴展之介面指標的位址 `IHostSecurityContext` `eContextType` 。</span><span class="sxs-lookup"><span data-stu-id="d7c62-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7c62-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7c62-108">Return Value</span></span>  
  
|<span data-ttu-id="d7c62-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7c62-109">HRESULT</span></span>|<span data-ttu-id="d7c62-110">描述</span><span class="sxs-lookup"><span data-stu-id="d7c62-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7c62-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7c62-111">S_OK</span></span>|<span data-ttu-id="d7c62-112">`GetSecurityContext` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="d7c62-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="d7c62-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7c62-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7c62-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d7c62-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7c62-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7c62-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7c62-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="d7c62-116">The call timed out.</span></span>|  
|<span data-ttu-id="d7c62-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7c62-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7c62-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d7c62-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7c62-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7c62-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7c62-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="d7c62-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7c62-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7c62-121">E_FAIL</span></span>|<span data-ttu-id="d7c62-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d7c62-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7c62-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="d7c62-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7c62-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d7c62-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7c62-125">備註</span><span class="sxs-lookup"><span data-stu-id="d7c62-125">Remarks</span></span>  

 <span data-ttu-id="d7c62-126">主機可以透過 CLR 和使用者程式碼控制執行緒權杖的所有程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="d7c62-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="d7c62-127">它也可以確保在非同步作業或具有限制程式碼存取的程式碼點之間傳遞完整的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="d7c62-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="d7c62-128">`IHostSecurityContext` 封裝此安全性內容資訊，這對 CLR 而言是不透明的。</span><span class="sxs-lookup"><span data-stu-id="d7c62-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="d7c62-129">CLR 會捕捉此資訊，並將其移動到執行緒集區背景工作專案分派、完成項執行，以及模組和類別結構。</span><span class="sxs-lookup"><span data-stu-id="d7c62-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7c62-130">需求</span><span class="sxs-lookup"><span data-stu-id="d7c62-130">Requirements</span></span>  

 <span data-ttu-id="d7c62-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c62-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7c62-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d7c62-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7c62-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d7c62-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7c62-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7c62-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c62-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7c62-135">See also</span></span>

- [<span data-ttu-id="d7c62-136">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="d7c62-136">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="d7c62-137">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="d7c62-137">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d7c62-138">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="d7c62-138">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
