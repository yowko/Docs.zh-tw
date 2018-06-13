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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57cf4e9f79be8e705869cf986a586fcfb3359584
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435335"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="6ebfe-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="6ebfe-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="6ebfe-103">取得指定的資料流中的組件的標準的組件識別資料。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ebfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ebfe-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ebfe-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ebfe-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="6ebfe-106">[in]要評估的組件資料流。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6ebfe-107">[in]供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="6ebfe-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是唯一的目前版本的 common language runtime (CLR) 支援的值。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="6ebfe-109">[out]包含的不透明的組件識別資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="6ebfe-110">[in、 out]大小`pwzBuffer`。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ebfe-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6ebfe-111">Return Value</span></span>  
  
|<span data-ttu-id="6ebfe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ebfe-112">HRESULT</span></span>|<span data-ttu-id="6ebfe-113">描述</span><span class="sxs-lookup"><span data-stu-id="6ebfe-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ebfe-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ebfe-114">S_OK</span></span>|<span data-ttu-id="6ebfe-115">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="6ebfe-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6ebfe-116">E_INVALIDARG</span></span>|<span data-ttu-id="6ebfe-117">提供`pStream`為 null。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="6ebfe-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6ebfe-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6ebfe-119">大小`pwzBuffer`太小。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="6ebfe-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ebfe-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ebfe-121">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ebfe-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ebfe-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ebfe-123">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-123">The call timed out.</span></span>|  
|<span data-ttu-id="6ebfe-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ebfe-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ebfe-125">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ebfe-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ebfe-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ebfe-127">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ebfe-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ebfe-128">E_FAIL</span></span>|<span data-ttu-id="6ebfe-129">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ebfe-130">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ebfe-131">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ebfe-132">需求</span><span class="sxs-lookup"><span data-stu-id="6ebfe-132">Requirements</span></span>  
 <span data-ttu-id="6ebfe-133">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ebfe-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ebfe-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ebfe-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ebfe-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6ebfe-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ebfe-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ebfe-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebfe-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ebfe-137">See Also</span></span>  
 [<span data-ttu-id="6ebfe-138">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="6ebfe-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="6ebfe-139">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="6ebfe-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
