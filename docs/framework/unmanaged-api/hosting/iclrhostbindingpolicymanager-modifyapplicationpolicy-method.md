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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178094"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="38a8b-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="38a8b-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="38a8b-103">修改指定程式集的繫結原則，並創建策略的新版本。</span><span class="sxs-lookup"><span data-stu-id="38a8b-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="38a8b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="38a8b-105">參數</span><span class="sxs-lookup"><span data-stu-id="38a8b-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="38a8b-106">[在]要修改的程式集的標識。</span><span class="sxs-lookup"><span data-stu-id="38a8b-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="38a8b-107">[在]修改程式集的新標識。</span><span class="sxs-lookup"><span data-stu-id="38a8b-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="38a8b-108">[在]指向緩衝區的指標，其中包含要修改的繫結原則資料。</span><span class="sxs-lookup"><span data-stu-id="38a8b-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="38a8b-109">[在]要替換的繫結原則的大小。</span><span class="sxs-lookup"><span data-stu-id="38a8b-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="38a8b-110">[在][EHostBindingPolicy修改標誌](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)值的邏輯 OR 組合，指示重定向的控制。</span><span class="sxs-lookup"><span data-stu-id="38a8b-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="38a8b-111">[出]指向包含新繫結原則資料的緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="38a8b-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="38a8b-112">[進出]指向新繫結原則緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="38a8b-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38a8b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="38a8b-113">Return Value</span></span>  
  
|<span data-ttu-id="38a8b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38a8b-114">HRESULT</span></span>|<span data-ttu-id="38a8b-115">描述</span><span class="sxs-lookup"><span data-stu-id="38a8b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38a8b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="38a8b-116">S_OK</span></span>|<span data-ttu-id="38a8b-117">已成功修改策略。</span><span class="sxs-lookup"><span data-stu-id="38a8b-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="38a8b-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="38a8b-118">E_INVALIDARG</span></span>|<span data-ttu-id="38a8b-119">`pwzSourceAssemblyIdentity`或`pwzTargetAssemblyIdentity`為空引用。</span><span class="sxs-lookup"><span data-stu-id="38a8b-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="38a8b-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="38a8b-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="38a8b-121">`pbNewApplicationPolicy` 太小了。</span><span class="sxs-lookup"><span data-stu-id="38a8b-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="38a8b-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38a8b-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38a8b-123">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="38a8b-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38a8b-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38a8b-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38a8b-125">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="38a8b-125">The call timed out.</span></span>|  
|<span data-ttu-id="38a8b-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38a8b-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38a8b-127">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="38a8b-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38a8b-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38a8b-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38a8b-129">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="38a8b-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38a8b-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38a8b-130">E_FAIL</span></span>|<span data-ttu-id="38a8b-131">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="38a8b-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38a8b-132">方法返回E_FAIL後，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="38a8b-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38a8b-133">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="38a8b-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38a8b-134">備註</span><span class="sxs-lookup"><span data-stu-id="38a8b-134">Remarks</span></span>  
 <span data-ttu-id="38a8b-135">該方法`ModifyApplicationPolicy`可以調用兩次。</span><span class="sxs-lookup"><span data-stu-id="38a8b-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="38a8b-136">第一個調用應為`pbNewApplicationPolicy`參數提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="38a8b-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="38a8b-137">此調用將返回，並帶有`pcbNewAppPolicySize`所需的值。</span><span class="sxs-lookup"><span data-stu-id="38a8b-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="38a8b-138">第二個調用應為`pcbNewAppPolicySize`提供此值，並指向 該大小的緩衝區。 `pbNewApplicationPolicy`</span><span class="sxs-lookup"><span data-stu-id="38a8b-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a8b-139">需求</span><span class="sxs-lookup"><span data-stu-id="38a8b-139">Requirements</span></span>  
 <span data-ttu-id="38a8b-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38a8b-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a8b-141">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38a8b-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38a8b-142">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="38a8b-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38a8b-143">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a8b-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a8b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38a8b-144">See also</span></span>

- [<span data-ttu-id="38a8b-145">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="38a8b-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
