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
ms.openlocfilehash: 9840217abdf8b3e1d0917b7447572b6860c181c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720304"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="a0af1-102">ICLRHostBindingPolicyManager::EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="a0af1-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>

<span data-ttu-id="a0af1-103">代表主機評估系結原則。</span><span class="sxs-lookup"><span data-stu-id="a0af1-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0af1-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0af1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a0af1-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0af1-105">Parameters</span></span>  

 `pwzReferenceIdentity`  
 <span data-ttu-id="a0af1-106">在元件在原則評估之前的參考。</span><span class="sxs-lookup"><span data-stu-id="a0af1-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="a0af1-107">在包含原則資料之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="a0af1-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="a0af1-108">在緩衝區的大小 `pbApplicationPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="a0af1-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="a0af1-109">擴展評估新的原則資料之後的元件參考。</span><span class="sxs-lookup"><span data-stu-id="a0af1-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="a0af1-110">[in，out]評估新的原則資料之後，元件身分識別參考緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="a0af1-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="a0af1-111">擴展 [EBindPolicyLevels](ebindpolicylevels-enumeration.md) 值的邏輯或組合指標，表示已套用的原則。</span><span class="sxs-lookup"><span data-stu-id="a0af1-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0af1-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="a0af1-112">Return Value</span></span>  
  
|<span data-ttu-id="a0af1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0af1-113">HRESULT</span></span>|<span data-ttu-id="a0af1-114">描述</span><span class="sxs-lookup"><span data-stu-id="a0af1-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0af1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0af1-115">S_OK</span></span>|<span data-ttu-id="a0af1-116">評估已順利完成。</span><span class="sxs-lookup"><span data-stu-id="a0af1-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="a0af1-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a0af1-117">E_INVALIDARG</span></span>|<span data-ttu-id="a0af1-118">`pwzReferenceIdentity`或 `pbApplicationPolicy` 為 null 參考。</span><span class="sxs-lookup"><span data-stu-id="a0af1-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="a0af1-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a0af1-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a0af1-120">`cbAppPolicySize` 太小了。</span><span class="sxs-lookup"><span data-stu-id="a0af1-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="a0af1-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0af1-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0af1-122">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a0af1-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0af1-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0af1-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0af1-124">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="a0af1-124">The call timed out.</span></span>|  
|<span data-ttu-id="a0af1-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0af1-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0af1-126">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a0af1-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0af1-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0af1-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0af1-128">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="a0af1-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0af1-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0af1-129">E_FAIL</span></span>|<span data-ttu-id="a0af1-130">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a0af1-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0af1-131">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="a0af1-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0af1-132">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a0af1-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0af1-133">備註</span><span class="sxs-lookup"><span data-stu-id="a0af1-133">Remarks</span></span>  

 <span data-ttu-id="a0af1-134">`EvaluatePolicy`方法可讓主機影響系結原則，以維護主機特定的元件版本控制需求。</span><span class="sxs-lookup"><span data-stu-id="a0af1-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="a0af1-135">原則引擎本身會保留在 CLR 內。</span><span class="sxs-lookup"><span data-stu-id="a0af1-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0af1-136">需求</span><span class="sxs-lookup"><span data-stu-id="a0af1-136">Requirements</span></span>  

 <span data-ttu-id="a0af1-137">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0af1-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0af1-138">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a0af1-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0af1-139">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a0af1-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0af1-140">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0af1-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0af1-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0af1-141">See also</span></span>

- [<span data-ttu-id="a0af1-142">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="a0af1-142">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
