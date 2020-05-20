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
ms.openlocfilehash: abba19600616cad8ba3377ae2ebb23459449d2a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615978"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="ae13e-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="ae13e-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="ae13e-103">取得指定資料流程中元件的標準元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="ae13e-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae13e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae13e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae13e-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae13e-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="ae13e-106">在要評估的元件資料流程。</span><span class="sxs-lookup"><span data-stu-id="ae13e-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ae13e-107">在提供供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="ae13e-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="ae13e-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime （CLR）所支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ae13e-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="ae13e-109">脫銷包含不透明元件識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ae13e-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="ae13e-110">[in、out]的大小 `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="ae13e-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae13e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae13e-111">Return Value</span></span>  
  
|<span data-ttu-id="ae13e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae13e-112">HRESULT</span></span>|<span data-ttu-id="ae13e-113">說明</span><span class="sxs-lookup"><span data-stu-id="ae13e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae13e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae13e-114">S_OK</span></span>|<span data-ttu-id="ae13e-115">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ae13e-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="ae13e-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ae13e-116">E_INVALIDARG</span></span>|<span data-ttu-id="ae13e-117">提供的 `pStream` 為 null。</span><span class="sxs-lookup"><span data-stu-id="ae13e-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="ae13e-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ae13e-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ae13e-119">的大小 `pwzBuffer` 太小。</span><span class="sxs-lookup"><span data-stu-id="ae13e-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="ae13e-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae13e-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae13e-121">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ae13e-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ae13e-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ae13e-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ae13e-123">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="ae13e-123">The call timed out.</span></span>|  
|<span data-ttu-id="ae13e-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ae13e-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ae13e-125">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ae13e-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ae13e-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ae13e-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ae13e-127">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="ae13e-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ae13e-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae13e-128">E_FAIL</span></span>|<span data-ttu-id="ae13e-129">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ae13e-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ae13e-130">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="ae13e-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ae13e-131">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ae13e-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae13e-132">需求</span><span class="sxs-lookup"><span data-stu-id="ae13e-132">Requirements</span></span>  
 <span data-ttu-id="ae13e-133">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae13e-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae13e-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ae13e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae13e-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ae13e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae13e-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae13e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae13e-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae13e-137">See also</span></span>

- [<span data-ttu-id="ae13e-138">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="ae13e-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ae13e-139">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="ae13e-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
