---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: b30f6f5ce22290dc3750cef0171349ec5ff2f76a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126743"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="8165d-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="8165d-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="8165d-103">取得指定資料流程中元件的標準元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="8165d-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8165d-104">語法</span><span class="sxs-lookup"><span data-stu-id="8165d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8165d-105">參數</span><span class="sxs-lookup"><span data-stu-id="8165d-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="8165d-106">在要評估的元件資料流程。</span><span class="sxs-lookup"><span data-stu-id="8165d-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8165d-107">在提供供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="8165d-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8165d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime （CLR）所支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="8165d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="8165d-109">脫銷包含不透明元件識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8165d-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="8165d-110">[in、out]`pwzBuffer`的大小。</span><span class="sxs-lookup"><span data-stu-id="8165d-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8165d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8165d-111">Return Value</span></span>  
  
|<span data-ttu-id="8165d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8165d-112">HRESULT</span></span>|<span data-ttu-id="8165d-113">描述</span><span class="sxs-lookup"><span data-stu-id="8165d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8165d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8165d-114">S_OK</span></span>|<span data-ttu-id="8165d-115">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="8165d-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8165d-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8165d-116">E_INVALIDARG</span></span>|<span data-ttu-id="8165d-117">提供的 `pStream` 為 null。</span><span class="sxs-lookup"><span data-stu-id="8165d-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="8165d-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8165d-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8165d-119">`pwzBuffer` 的大小太小。</span><span class="sxs-lookup"><span data-stu-id="8165d-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="8165d-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8165d-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8165d-121">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8165d-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8165d-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8165d-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8165d-123">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8165d-123">The call timed out.</span></span>|  
|<span data-ttu-id="8165d-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8165d-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8165d-125">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8165d-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8165d-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8165d-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8165d-127">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8165d-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8165d-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8165d-128">E_FAIL</span></span>|<span data-ttu-id="8165d-129">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8165d-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8165d-130">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="8165d-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8165d-131">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8165d-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8165d-132">需求</span><span class="sxs-lookup"><span data-stu-id="8165d-132">Requirements</span></span>  
 <span data-ttu-id="8165d-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8165d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8165d-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8165d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8165d-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8165d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8165d-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8165d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8165d-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="8165d-137">See also</span></span>

- [<span data-ttu-id="8165d-138">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="8165d-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8165d-139">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="8165d-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
