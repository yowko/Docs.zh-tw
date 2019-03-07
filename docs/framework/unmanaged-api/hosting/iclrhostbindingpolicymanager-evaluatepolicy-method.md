---
title: ICLRHostBindingPolicyManager::EvaluatePolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3310f584475a4d6a6f0e3e790db13875faf60cf2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466683"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="597ae-102">ICLRHostBindingPolicyManager::EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="597ae-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="597ae-103">代表主應用程式，會評估繫結原則。</span><span class="sxs-lookup"><span data-stu-id="597ae-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="597ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="597ae-104">Syntax</span></span>  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="597ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="597ae-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="597ae-106">[in]之前的原則評估的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="597ae-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="597ae-107">[in]包含原則的資料緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="597ae-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="597ae-108">[in]大小`pbApplicationPolicy`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="597ae-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="597ae-109">[out]新的原則資料評估後的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="597ae-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="597ae-110">[in、 out]新的原則資料評估後的組件身分識別參考緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="597ae-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="597ae-111">[out]邏輯 OR 結合指標[EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)值，表示已套用哪些原則。</span><span class="sxs-lookup"><span data-stu-id="597ae-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="597ae-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="597ae-112">Return Value</span></span>  
  
|<span data-ttu-id="597ae-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="597ae-113">HRESULT</span></span>|<span data-ttu-id="597ae-114">描述</span><span class="sxs-lookup"><span data-stu-id="597ae-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="597ae-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="597ae-115">S_OK</span></span>|<span data-ttu-id="597ae-116">已成功完成評估。</span><span class="sxs-lookup"><span data-stu-id="597ae-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="597ae-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="597ae-117">E_INVALIDARG</span></span>|<span data-ttu-id="597ae-118">請`pwzReferenceIdentity`或`pbApplicationPolicy`為 null 參考。</span><span class="sxs-lookup"><span data-stu-id="597ae-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="597ae-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="597ae-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="597ae-120">`cbAppPolicySize` 為太小。</span><span class="sxs-lookup"><span data-stu-id="597ae-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="597ae-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="597ae-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="597ae-122">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="597ae-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="597ae-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="597ae-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="597ae-124">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="597ae-124">The call timed out.</span></span>|  
|<span data-ttu-id="597ae-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="597ae-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="597ae-126">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="597ae-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="597ae-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="597ae-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="597ae-128">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="597ae-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="597ae-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="597ae-129">E_FAIL</span></span>|<span data-ttu-id="597ae-130">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="597ae-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="597ae-131">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="597ae-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="597ae-132">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="597ae-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="597ae-133">備註</span><span class="sxs-lookup"><span data-stu-id="597ae-133">Remarks</span></span>  
 <span data-ttu-id="597ae-134">`EvaluatePolicy`方法可讓主應用程式會影響到維護主機特定組件的繫結原則版本控制需求。</span><span class="sxs-lookup"><span data-stu-id="597ae-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="597ae-135">原則引擎本身會保持在 CLR 中。</span><span class="sxs-lookup"><span data-stu-id="597ae-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="597ae-136">需求</span><span class="sxs-lookup"><span data-stu-id="597ae-136">Requirements</span></span>  
 <span data-ttu-id="597ae-137">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="597ae-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="597ae-138">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="597ae-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="597ae-139">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="597ae-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="597ae-140">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="597ae-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597ae-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="597ae-141">See also</span></span>
- [<span data-ttu-id="597ae-142">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="597ae-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
