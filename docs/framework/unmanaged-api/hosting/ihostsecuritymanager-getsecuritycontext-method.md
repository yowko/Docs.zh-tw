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
ms.openlocfilehash: 7198698edce48546c4f9a82ace18d5a6e71891ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176249"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="93495-102">IHostSecurityManager::GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="93495-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="93495-103">從主機獲取請求的[IHost 安全上下文](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="93495-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93495-104">語法</span><span class="sxs-lookup"><span data-stu-id="93495-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93495-105">參數</span><span class="sxs-lookup"><span data-stu-id="93495-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="93495-106">[在][ECoNtextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值之一，指示要返回的安全上下文的類型。</span><span class="sxs-lookup"><span data-stu-id="93495-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="93495-107">[出]指向 的`IHostSecurityContext`介面指標的位址`eContextType`。</span><span class="sxs-lookup"><span data-stu-id="93495-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93495-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="93495-108">Return Value</span></span>  
  
|<span data-ttu-id="93495-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93495-109">HRESULT</span></span>|<span data-ttu-id="93495-110">描述</span><span class="sxs-lookup"><span data-stu-id="93495-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93495-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="93495-111">S_OK</span></span>|<span data-ttu-id="93495-112">`GetSecurityContext`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="93495-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="93495-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93495-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93495-114">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="93495-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="93495-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93495-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93495-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="93495-116">The call timed out.</span></span>|  
|<span data-ttu-id="93495-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93495-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93495-118">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="93495-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93495-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93495-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93495-120">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="93495-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93495-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93495-121">E_FAIL</span></span>|<span data-ttu-id="93495-122">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="93495-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93495-123">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="93495-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93495-124">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="93495-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93495-125">備註</span><span class="sxs-lookup"><span data-stu-id="93495-125">Remarks</span></span>  
 <span data-ttu-id="93495-126">主機可以通過 CLR 和使用者代碼控制對執行緒權杖的所有代碼訪問。</span><span class="sxs-lookup"><span data-stu-id="93495-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="93495-127">它還可確保在具有受限代碼存取權限的非同步作業或代碼點傳遞完整的安全上下文資訊。</span><span class="sxs-lookup"><span data-stu-id="93495-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="93495-128">`IHostSecurityContext`封裝此安全上下文資訊，這些資訊對 CLR 是不透明的。</span><span class="sxs-lookup"><span data-stu-id="93495-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="93495-129">CLR 捕獲此資訊並將其跨執行緒池輔助工項調度、終端子執行以及模組和類構造移動。</span><span class="sxs-lookup"><span data-stu-id="93495-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93495-130">需求</span><span class="sxs-lookup"><span data-stu-id="93495-130">Requirements</span></span>  
 <span data-ttu-id="93495-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93495-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93495-132">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93495-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93495-133">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="93495-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93495-134">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93495-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93495-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93495-135">See also</span></span>

- [<span data-ttu-id="93495-136">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="93495-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="93495-137">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="93495-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="93495-138">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="93495-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
