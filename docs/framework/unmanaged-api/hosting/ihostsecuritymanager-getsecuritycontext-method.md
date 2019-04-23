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
ms.openlocfilehash: 1f4f923e868b72e9de33884e4814ebfa329a16e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105806"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="07b58-102">IHostSecurityManager::GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="07b58-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="07b58-103">取得要求[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)從主應用程式。</span><span class="sxs-lookup"><span data-stu-id="07b58-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07b58-104">語法</span><span class="sxs-lookup"><span data-stu-id="07b58-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07b58-105">參數</span><span class="sxs-lookup"><span data-stu-id="07b58-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="07b58-106">[in]其中一個[EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值，表示要傳回的安全性內容的類型。</span><span class="sxs-lookup"><span data-stu-id="07b58-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="07b58-107">[out]介面指標的位址`IHostSecurityContext`的`eContextType`。</span><span class="sxs-lookup"><span data-stu-id="07b58-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07b58-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="07b58-108">Return Value</span></span>  
  
|<span data-ttu-id="07b58-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07b58-109">HRESULT</span></span>|<span data-ttu-id="07b58-110">描述</span><span class="sxs-lookup"><span data-stu-id="07b58-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07b58-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="07b58-111">S_OK</span></span>|<span data-ttu-id="07b58-112">`GetSecurityContext` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="07b58-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="07b58-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07b58-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07b58-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="07b58-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07b58-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07b58-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07b58-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="07b58-116">The call timed out.</span></span>|  
|<span data-ttu-id="07b58-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07b58-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07b58-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="07b58-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07b58-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07b58-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07b58-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="07b58-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07b58-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07b58-121">E_FAIL</span></span>|<span data-ttu-id="07b58-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="07b58-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07b58-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="07b58-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07b58-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="07b58-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07b58-125">備註</span><span class="sxs-lookup"><span data-stu-id="07b58-125">Remarks</span></span>  
 <span data-ttu-id="07b58-126">主機可以控制執行緒權杖的所有程式碼存取 CLR 和使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="07b58-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="07b58-127">它也可以確保完整的安全性內容資訊傳遞到非同步作業或受限制的程式碼存取的字碼指標。</span><span class="sxs-lookup"><span data-stu-id="07b58-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="07b58-128">`IHostSecurityContext` 封裝此資訊安全內容資訊，也就是對 CLR 不透明。</span><span class="sxs-lookup"><span data-stu-id="07b58-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="07b58-129">CLR 會擷取這項資訊，並會將它移到跨執行緒集區背景工作項目分派、 完成項執行和模組和類別的建構。</span><span class="sxs-lookup"><span data-stu-id="07b58-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07b58-130">需求</span><span class="sxs-lookup"><span data-stu-id="07b58-130">Requirements</span></span>  
 <span data-ttu-id="07b58-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07b58-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07b58-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07b58-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07b58-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="07b58-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07b58-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07b58-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b58-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07b58-135">See also</span></span>

- [<span data-ttu-id="07b58-136">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="07b58-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="07b58-137">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="07b58-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="07b58-138">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="07b58-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
