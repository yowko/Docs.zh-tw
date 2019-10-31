---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: d5323538447e083a0c727e43261dd68337182b9b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141072"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="87f58-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="87f58-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="87f58-103">修改指定元件的系結原則，並建立新版本的原則。</span><span class="sxs-lookup"><span data-stu-id="87f58-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f58-104">語法</span><span class="sxs-lookup"><span data-stu-id="87f58-104">Syntax</span></span>  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87f58-105">參數</span><span class="sxs-lookup"><span data-stu-id="87f58-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="87f58-106">在要修改之元件的識別。</span><span class="sxs-lookup"><span data-stu-id="87f58-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="87f58-107">在已修改元件的新識別。</span><span class="sxs-lookup"><span data-stu-id="87f58-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="87f58-108">在緩衝區的指標，其中包含要修改之元件的系結原則資料。</span><span class="sxs-lookup"><span data-stu-id="87f58-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="87f58-109">在要取代的系結原則大小。</span><span class="sxs-lookup"><span data-stu-id="87f58-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="87f58-110">在[EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)值的邏輯 OR 組合，表示重新導向的控制權。</span><span class="sxs-lookup"><span data-stu-id="87f58-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="87f58-111">脫銷包含新系結原則資料之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="87f58-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="87f58-112">[in、out]新系結原則緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="87f58-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87f58-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="87f58-113">Return Value</span></span>  
  
|<span data-ttu-id="87f58-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87f58-114">HRESULT</span></span>|<span data-ttu-id="87f58-115">描述</span><span class="sxs-lookup"><span data-stu-id="87f58-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87f58-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="87f58-116">S_OK</span></span>|<span data-ttu-id="87f58-117">已成功修改原則。</span><span class="sxs-lookup"><span data-stu-id="87f58-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="87f58-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="87f58-118">E_INVALIDARG</span></span>|<span data-ttu-id="87f58-119">`pwzSourceAssemblyIdentity` 或 `pwzTargetAssemblyIdentity` 是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="87f58-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="87f58-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="87f58-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="87f58-121">`pbNewApplicationPolicy` 太小。</span><span class="sxs-lookup"><span data-stu-id="87f58-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="87f58-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87f58-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87f58-123">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="87f58-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="87f58-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="87f58-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="87f58-125">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="87f58-125">The call timed out.</span></span>|  
|<span data-ttu-id="87f58-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="87f58-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="87f58-127">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="87f58-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="87f58-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="87f58-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="87f58-129">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="87f58-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="87f58-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87f58-130">E_FAIL</span></span>|<span data-ttu-id="87f58-131">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="87f58-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="87f58-132">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="87f58-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="87f58-133">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="87f58-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87f58-134">備註</span><span class="sxs-lookup"><span data-stu-id="87f58-134">Remarks</span></span>  
 <span data-ttu-id="87f58-135">`ModifyApplicationPolicy` 方法可以呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="87f58-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="87f58-136">第一個呼叫應該為 `pbNewApplicationPolicy` 參數提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="87f58-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="87f58-137">此呼叫會傳回，並具有 `pcbNewAppPolicySize`的必要值。</span><span class="sxs-lookup"><span data-stu-id="87f58-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="87f58-138">第二個呼叫應為 `pcbNewAppPolicySize`提供此值，並指向該大小的緩衝區以供 `pbNewApplicationPolicy`。</span><span class="sxs-lookup"><span data-stu-id="87f58-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f58-139">需求</span><span class="sxs-lookup"><span data-stu-id="87f58-139">Requirements</span></span>  
 <span data-ttu-id="87f58-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87f58-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f58-141">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="87f58-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87f58-142">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="87f58-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87f58-143">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87f58-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f58-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="87f58-144">See also</span></span>

- [<span data-ttu-id="87f58-145">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="87f58-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
