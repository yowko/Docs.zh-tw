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
ms.openlocfilehash: f72a66354bfc907dab7ebc24de515bdfb20ddfb2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703591"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="d8baa-102">ICLRHostBindingPolicyManager::EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="d8baa-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="d8baa-103">代表主機評估系結原則。</span><span class="sxs-lookup"><span data-stu-id="d8baa-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8baa-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8baa-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d8baa-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8baa-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="d8baa-106">在在原則評估之前的元件參考。</span><span class="sxs-lookup"><span data-stu-id="d8baa-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="d8baa-107">在包含原則資料之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="d8baa-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="d8baa-108">在緩衝區的大小 `pbApplicationPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="d8baa-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="d8baa-109">脫銷評估新原則資料之後的元件參考。</span><span class="sxs-lookup"><span data-stu-id="d8baa-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="d8baa-110">[in、out]評估新的原則資料之後，元件識別參考緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="d8baa-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="d8baa-111">脫銷[EBindPolicyLevels](ebindpolicylevels-enumeration.md)值之邏輯 OR 組合的指標，表示已套用的原則。</span><span class="sxs-lookup"><span data-stu-id="d8baa-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8baa-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8baa-112">Return Value</span></span>  
  
|<span data-ttu-id="d8baa-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8baa-113">HRESULT</span></span>|<span data-ttu-id="d8baa-114">說明</span><span class="sxs-lookup"><span data-stu-id="d8baa-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8baa-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8baa-115">S_OK</span></span>|<span data-ttu-id="d8baa-116">評估已順利完成。</span><span class="sxs-lookup"><span data-stu-id="d8baa-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="d8baa-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d8baa-117">E_INVALIDARG</span></span>|<span data-ttu-id="d8baa-118">`pwzReferenceIdentity`或 `pbApplicationPolicy` 為 null 參考。</span><span class="sxs-lookup"><span data-stu-id="d8baa-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="d8baa-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d8baa-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d8baa-120">`cbAppPolicySize` 太小了。</span><span class="sxs-lookup"><span data-stu-id="d8baa-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="d8baa-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8baa-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8baa-122">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d8baa-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8baa-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8baa-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8baa-124">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d8baa-124">The call timed out.</span></span>|  
|<span data-ttu-id="d8baa-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8baa-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8baa-126">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d8baa-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8baa-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8baa-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8baa-128">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d8baa-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8baa-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8baa-129">E_FAIL</span></span>|<span data-ttu-id="d8baa-130">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d8baa-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8baa-131">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d8baa-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8baa-132">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d8baa-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8baa-133">備註</span><span class="sxs-lookup"><span data-stu-id="d8baa-133">Remarks</span></span>  
 <span data-ttu-id="d8baa-134">`EvaluatePolicy`方法可讓主機影響系結原則，以維護主機特定的元件版本控制需求。</span><span class="sxs-lookup"><span data-stu-id="d8baa-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="d8baa-135">原則引擎本身會保留在 CLR 內部。</span><span class="sxs-lookup"><span data-stu-id="d8baa-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8baa-136">需求</span><span class="sxs-lookup"><span data-stu-id="d8baa-136">Requirements</span></span>  
 <span data-ttu-id="d8baa-137">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8baa-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8baa-138">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d8baa-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8baa-139">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d8baa-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8baa-140">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8baa-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8baa-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8baa-141">See also</span></span>

- [<span data-ttu-id="d8baa-142">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="d8baa-142">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
