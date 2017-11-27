---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd16f13bd77127953bdd17b258c7be518088f899
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="f17ff-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="f17ff-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="f17ff-103">取得指定的資料流中的組件的標準的組件識別資料。</span><span class="sxs-lookup"><span data-stu-id="f17ff-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="f17ff-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f17ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="f17ff-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="f17ff-106">[in]要評估的組件資料流。</span><span class="sxs-lookup"><span data-stu-id="f17ff-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f17ff-107">[in]供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="f17ff-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="f17ff-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是唯一的目前版本的 common language runtime (CLR) 支援的值。</span><span class="sxs-lookup"><span data-stu-id="f17ff-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f17ff-109">[out]包含的不透明的組件識別資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f17ff-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="f17ff-110">[in、 out]大小`pwzBuffer`。</span><span class="sxs-lookup"><span data-stu-id="f17ff-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f17ff-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f17ff-111">Return Value</span></span>  
  
|<span data-ttu-id="f17ff-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f17ff-112">HRESULT</span></span>|<span data-ttu-id="f17ff-113">描述</span><span class="sxs-lookup"><span data-stu-id="f17ff-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f17ff-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f17ff-114">S_OK</span></span>|<span data-ttu-id="f17ff-115">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f17ff-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="f17ff-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f17ff-116">E_INVALIDARG</span></span>|<span data-ttu-id="f17ff-117">提供`pStream`為 null。</span><span class="sxs-lookup"><span data-stu-id="f17ff-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="f17ff-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f17ff-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f17ff-119">大小`pwzBuffer`太小。</span><span class="sxs-lookup"><span data-stu-id="f17ff-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="f17ff-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f17ff-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f17ff-121">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f17ff-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f17ff-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f17ff-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f17ff-123">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f17ff-123">The call timed out.</span></span>|  
|<span data-ttu-id="f17ff-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f17ff-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f17ff-125">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f17ff-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f17ff-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f17ff-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f17ff-127">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f17ff-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f17ff-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f17ff-128">E_FAIL</span></span>|<span data-ttu-id="f17ff-129">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f17ff-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f17ff-130">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="f17ff-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f17ff-131">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f17ff-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f17ff-132">需求</span><span class="sxs-lookup"><span data-stu-id="f17ff-132">Requirements</span></span>  
 <span data-ttu-id="f17ff-133">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f17ff-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f17ff-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f17ff-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f17ff-135">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f17ff-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f17ff-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f17ff-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17ff-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f17ff-137">See Also</span></span>  
 [<span data-ttu-id="f17ff-138">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="f17ff-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f17ff-139">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="f17ff-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
