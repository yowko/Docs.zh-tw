---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3d5e53dd0845fbd01dbd9d20ce8feef12748c04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985175"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="a192a-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="a192a-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="a192a-103">取得資料繫結在指定的檔案路徑組件的組件識別。</span><span class="sxs-lookup"><span data-stu-id="a192a-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a192a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a192a-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a192a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a192a-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="a192a-106">[in]要評估的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="a192a-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a192a-107">[in]值為[ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)列舉，指出組件的識別型別。</span><span class="sxs-lookup"><span data-stu-id="a192a-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="a192a-108">供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="a192a-108">Provided for future extensibility.</span></span> <span data-ttu-id="a192a-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是 common language runtime (CLR) 2.0 版支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="a192a-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a192a-110">[out]包含的不透明的組件身分識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a192a-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="a192a-111">[in、 out]大小的指標`pwzBuffer`。</span><span class="sxs-lookup"><span data-stu-id="a192a-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a192a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="a192a-112">Return Value</span></span>  
  
|<span data-ttu-id="a192a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a192a-113">HRESULT</span></span>|<span data-ttu-id="a192a-114">描述</span><span class="sxs-lookup"><span data-stu-id="a192a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a192a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a192a-115">S_OK</span></span>|<span data-ttu-id="a192a-116">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a192a-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="a192a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a192a-117">E_INVALIDARG</span></span>|<span data-ttu-id="a192a-118">提供`pwzFilePath`為 null。</span><span class="sxs-lookup"><span data-stu-id="a192a-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="a192a-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a192a-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a192a-120">大小`pwzBuffer`太小。</span><span class="sxs-lookup"><span data-stu-id="a192a-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="a192a-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a192a-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a192a-122">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a192a-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a192a-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a192a-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a192a-124">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a192a-124">The call timed out.</span></span>|  
|<span data-ttu-id="a192a-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a192a-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a192a-126">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a192a-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a192a-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a192a-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a192a-128">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a192a-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a192a-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a192a-129">E_FAIL</span></span>|<span data-ttu-id="a192a-130">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a192a-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a192a-131">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a192a-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a192a-132">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a192a-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a192a-133">備註</span><span class="sxs-lookup"><span data-stu-id="a192a-133">Remarks</span></span>  
 <span data-ttu-id="a192a-134">`GetBindingIdentityFromFile` 通常會呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="a192a-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="a192a-135">第一次呼叫提供 null 值`pwzBuffer`，且此方法會傳回適當的大小，以`pcchBufferSize`。</span><span class="sxs-lookup"><span data-stu-id="a192a-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="a192a-136">第二個呼叫所提供的適當配置的緩衝區，此方法會傳回實際的緩衝區資料完成時。</span><span class="sxs-lookup"><span data-stu-id="a192a-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a192a-137">需求</span><span class="sxs-lookup"><span data-stu-id="a192a-137">Requirements</span></span>  
 <span data-ttu-id="a192a-138">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a192a-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a192a-139">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a192a-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a192a-140">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a192a-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a192a-141">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a192a-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a192a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a192a-142">See also</span></span>

- [<span data-ttu-id="a192a-143">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="a192a-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a192a-144">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="a192a-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a192a-145">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="a192a-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
