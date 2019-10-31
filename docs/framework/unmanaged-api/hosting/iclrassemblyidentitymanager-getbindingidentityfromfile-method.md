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
ms.openlocfilehash: 19d6a76d62680be91a7b9721912ca528edde7511
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126748"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="336ee-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="336ee-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="336ee-103">取得位於指定檔案路徑之元件的元件識別系結資料。</span><span class="sxs-lookup"><span data-stu-id="336ee-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="336ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="336ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="336ee-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="336ee-106">在要評估之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="336ee-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="336ee-107">在[ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)列舉的值，表示元件的識別類型。</span><span class="sxs-lookup"><span data-stu-id="336ee-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="336ee-108">提供供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="336ee-108">Provided for future extensibility.</span></span> <span data-ttu-id="336ee-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是 common language runtime （CLR）2.0 版支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="336ee-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="336ee-110">脫銷包含不透明元件識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="336ee-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="336ee-111">[in、out]`pwzBuffer`大小的指標。</span><span class="sxs-lookup"><span data-stu-id="336ee-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="336ee-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="336ee-112">Return Value</span></span>  
  
|<span data-ttu-id="336ee-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="336ee-113">HRESULT</span></span>|<span data-ttu-id="336ee-114">描述</span><span class="sxs-lookup"><span data-stu-id="336ee-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="336ee-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="336ee-115">S_OK</span></span>|<span data-ttu-id="336ee-116">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="336ee-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="336ee-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="336ee-117">E_INVALIDARG</span></span>|<span data-ttu-id="336ee-118">提供的 `pwzFilePath` 為 null。</span><span class="sxs-lookup"><span data-stu-id="336ee-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="336ee-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="336ee-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="336ee-120">`pwzBuffer` 的大小太小。</span><span class="sxs-lookup"><span data-stu-id="336ee-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="336ee-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="336ee-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="336ee-122">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="336ee-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="336ee-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="336ee-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="336ee-124">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="336ee-124">The call timed out.</span></span>|  
|<span data-ttu-id="336ee-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="336ee-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="336ee-126">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="336ee-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="336ee-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="336ee-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="336ee-128">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="336ee-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="336ee-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="336ee-129">E_FAIL</span></span>|<span data-ttu-id="336ee-130">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="336ee-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="336ee-131">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="336ee-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="336ee-132">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="336ee-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="336ee-133">備註</span><span class="sxs-lookup"><span data-stu-id="336ee-133">Remarks</span></span>  
 <span data-ttu-id="336ee-134">`GetBindingIdentityFromFile` 通常會被呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="336ee-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="336ee-135">第一個呼叫會為 `pwzBuffer`提供 null 值，而方法會在 `pcchBufferSize`中傳回適當的大小。</span><span class="sxs-lookup"><span data-stu-id="336ee-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="336ee-136">第二個呼叫會提供適當配置的緩衝區，而且方法會在完成時以實際的緩衝區資料傳回。</span><span class="sxs-lookup"><span data-stu-id="336ee-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="336ee-137">需求</span><span class="sxs-lookup"><span data-stu-id="336ee-137">Requirements</span></span>  
 <span data-ttu-id="336ee-138">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="336ee-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336ee-139">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="336ee-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="336ee-140">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="336ee-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="336ee-141">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336ee-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336ee-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="336ee-142">See also</span></span>

- [<span data-ttu-id="336ee-143">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="336ee-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="336ee-144">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="336ee-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="336ee-145">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="336ee-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
