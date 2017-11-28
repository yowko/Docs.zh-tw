---
title: "ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51775f52e34f35d8ef9f3a8533363be73e9bd7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="b009a-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="b009a-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="b009a-103">修改繫結原則的指定組件，並建立新的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b009a-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b009a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b009a-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="b009a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b009a-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="b009a-106">[in]若要修改組件的識別。</span><span class="sxs-lookup"><span data-stu-id="b009a-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="b009a-107">[in]已修改的組件的新識別。</span><span class="sxs-lookup"><span data-stu-id="b009a-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="b009a-108">[in]包含要修改的組件的繫結原則資料緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="b009a-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="b009a-109">[in]要被取代的繫結原則的大小。</span><span class="sxs-lookup"><span data-stu-id="b009a-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="b009a-110">[in]邏輯 OR 組合的[EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)值，表示重新導向的控制項。</span><span class="sxs-lookup"><span data-stu-id="b009a-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="b009a-111">[out]包含新的繫結原則資料緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="b009a-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="b009a-112">[in、 out]新的繫結原則緩衝區的大小指標。</span><span class="sxs-lookup"><span data-stu-id="b009a-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b009a-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="b009a-113">Return Value</span></span>  
  
|<span data-ttu-id="b009a-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b009a-114">HRESULT</span></span>|<span data-ttu-id="b009a-115">描述</span><span class="sxs-lookup"><span data-stu-id="b009a-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b009a-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="b009a-116">S_OK</span></span>|<span data-ttu-id="b009a-117">已成功修改原則。</span><span class="sxs-lookup"><span data-stu-id="b009a-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="b009a-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b009a-118">E_INVALIDARG</span></span>|<span data-ttu-id="b009a-119">`pwzSourceAssemblyIdentity`或`pwzTargetAssemblyIdentity`是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="b009a-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="b009a-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b009a-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b009a-121">`pbNewApplicationPolicy`為太小。</span><span class="sxs-lookup"><span data-stu-id="b009a-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="b009a-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b009a-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b009a-123">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b009a-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b009a-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b009a-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b009a-125">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b009a-125">The call timed out.</span></span>|  
|<span data-ttu-id="b009a-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b009a-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b009a-127">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b009a-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b009a-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b009a-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b009a-129">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b009a-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b009a-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b009a-130">E_FAIL</span></span>|<span data-ttu-id="b009a-131">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b009a-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b009a-132">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="b009a-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b009a-133">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b009a-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b009a-134">備註</span><span class="sxs-lookup"><span data-stu-id="b009a-134">Remarks</span></span>  
 <span data-ttu-id="b009a-135">`ModifyApplicationPolicy`兩次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b009a-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="b009a-136">第一次呼叫應該提供的 null 值`pbNewApplicationPolicy`參數。</span><span class="sxs-lookup"><span data-stu-id="b009a-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="b009a-137">此呼叫會傳回與所需值`pcbNewAppPolicySize`。</span><span class="sxs-lookup"><span data-stu-id="b009a-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="b009a-138">第二次呼叫應該提供此值`pcbNewAppPolicySize`，並指向該大小的緩衝區`pbNewApplicationPolicy`。</span><span class="sxs-lookup"><span data-stu-id="b009a-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b009a-139">需求</span><span class="sxs-lookup"><span data-stu-id="b009a-139">Requirements</span></span>  
 <span data-ttu-id="b009a-140">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b009a-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b009a-141">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b009a-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b009a-142">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b009a-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b009a-143">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b009a-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b009a-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b009a-144">See Also</span></span>  
 [<span data-ttu-id="b009a-145">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b009a-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
