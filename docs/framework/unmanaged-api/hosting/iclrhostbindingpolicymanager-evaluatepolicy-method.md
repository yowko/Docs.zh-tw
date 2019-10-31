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
ms.openlocfilehash: 9600573a0a730cee10247d5644d587e75856cdd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141187"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="7e99c-102">ICLRHostBindingPolicyManager::EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="7e99c-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="7e99c-103">代表主機評估系結原則。</span><span class="sxs-lookup"><span data-stu-id="7e99c-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e99c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e99c-104">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e99c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e99c-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="7e99c-106">在在原則評估之前的元件參考。</span><span class="sxs-lookup"><span data-stu-id="7e99c-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="7e99c-107">在包含原則資料之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="7e99c-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="7e99c-108">在`pbApplicationPolicy` 緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="7e99c-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="7e99c-109">脫銷評估新原則資料之後的元件參考。</span><span class="sxs-lookup"><span data-stu-id="7e99c-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="7e99c-110">[in、out]評估新的原則資料之後，元件識別參考緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="7e99c-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="7e99c-111">脫銷[EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)值之邏輯 OR 組合的指標，表示已套用的原則。</span><span class="sxs-lookup"><span data-stu-id="7e99c-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e99c-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="7e99c-112">Return Value</span></span>  
  
|<span data-ttu-id="7e99c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e99c-113">HRESULT</span></span>|<span data-ttu-id="7e99c-114">描述</span><span class="sxs-lookup"><span data-stu-id="7e99c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e99c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e99c-115">S_OK</span></span>|<span data-ttu-id="7e99c-116">評估已順利完成。</span><span class="sxs-lookup"><span data-stu-id="7e99c-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="7e99c-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7e99c-117">E_INVALIDARG</span></span>|<span data-ttu-id="7e99c-118">`pwzReferenceIdentity` 或 `pbApplicationPolicy` 都是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="7e99c-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="7e99c-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7e99c-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7e99c-120">`cbAppPolicySize` 太小。</span><span class="sxs-lookup"><span data-stu-id="7e99c-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="7e99c-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7e99c-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7e99c-122">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7e99c-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7e99c-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7e99c-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7e99c-124">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="7e99c-124">The call timed out.</span></span>|  
|<span data-ttu-id="7e99c-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7e99c-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7e99c-126">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7e99c-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7e99c-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7e99c-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7e99c-128">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="7e99c-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7e99c-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e99c-129">E_FAIL</span></span>|<span data-ttu-id="7e99c-130">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7e99c-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e99c-131">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="7e99c-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7e99c-132">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7e99c-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e99c-133">備註</span><span class="sxs-lookup"><span data-stu-id="7e99c-133">Remarks</span></span>  
 <span data-ttu-id="7e99c-134">`EvaluatePolicy` 方法可讓主機影響系結原則，以維護主機特定的元件版本控制需求。</span><span class="sxs-lookup"><span data-stu-id="7e99c-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="7e99c-135">原則引擎本身會保留在 CLR 內部。</span><span class="sxs-lookup"><span data-stu-id="7e99c-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e99c-136">需求</span><span class="sxs-lookup"><span data-stu-id="7e99c-136">Requirements</span></span>  
 <span data-ttu-id="7e99c-137">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e99c-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e99c-138">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7e99c-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e99c-139">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7e99c-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e99c-140">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e99c-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e99c-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e99c-141">See also</span></span>

- [<span data-ttu-id="7e99c-142">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="7e99c-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
