---
title: "IHostSecurityManager::GetSecurityContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.GetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b150700c50842791a2413688583e7e1289852d62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="03be3-102">IHostSecurityManager::GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="03be3-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="03be3-103">取得所要求[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)從主機。</span><span class="sxs-lookup"><span data-stu-id="03be3-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03be3-104">語法</span><span class="sxs-lookup"><span data-stu-id="03be3-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03be3-105">參數</span><span class="sxs-lookup"><span data-stu-id="03be3-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="03be3-106">[in]其中一個[EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值，表示要傳回的安全性內容的類型。</span><span class="sxs-lookup"><span data-stu-id="03be3-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="03be3-107">[out]介面指標的位址`IHostSecurityContext`的`eContextType`。</span><span class="sxs-lookup"><span data-stu-id="03be3-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03be3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="03be3-108">Return Value</span></span>  
  
|<span data-ttu-id="03be3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03be3-109">HRESULT</span></span>|<span data-ttu-id="03be3-110">描述</span><span class="sxs-lookup"><span data-stu-id="03be3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03be3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="03be3-111">S_OK</span></span>|<span data-ttu-id="03be3-112">`GetSecurityContext`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="03be3-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="03be3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03be3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03be3-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="03be3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03be3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03be3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03be3-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="03be3-116">The call timed out.</span></span>|  
|<span data-ttu-id="03be3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03be3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03be3-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="03be3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03be3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03be3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03be3-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="03be3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03be3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03be3-121">E_FAIL</span></span>|<span data-ttu-id="03be3-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="03be3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03be3-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="03be3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03be3-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="03be3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03be3-125">備註</span><span class="sxs-lookup"><span data-stu-id="03be3-125">Remarks</span></span>  
 <span data-ttu-id="03be3-126">主機可以控制執行緒語彙基元的所有程式碼存取 CLR 和使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="03be3-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="03be3-127">它也可以確保完整的安全性內容資訊傳遞到非同步作業或字碼指標，具有受限制的程式碼存取權。</span><span class="sxs-lookup"><span data-stu-id="03be3-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="03be3-128">`IHostSecurityContext`封裝這個資訊安全內容資訊，也就是不透明 CLR。</span><span class="sxs-lookup"><span data-stu-id="03be3-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="03be3-129">CLR 會擷取這項資訊，並會將它移到跨執行緒集區背景工作項目分派、 完成項執行和模組和類別的建構。</span><span class="sxs-lookup"><span data-stu-id="03be3-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03be3-130">需求</span><span class="sxs-lookup"><span data-stu-id="03be3-130">Requirements</span></span>  
 <span data-ttu-id="03be3-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03be3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03be3-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03be3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03be3-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="03be3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03be3-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03be3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03be3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03be3-135">See Also</span></span>  
 [<span data-ttu-id="03be3-136">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="03be3-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="03be3-137">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="03be3-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="03be3-138">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="03be3-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
