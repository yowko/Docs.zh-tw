---
title: IHostAssemblyManager::GetNonHostStoreAssemblies 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: eb715e1a4f9a210a1440874a9a8cea2d85345d33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124582"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="2f0f3-102">IHostAssemblyManager::GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="2f0f3-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="2f0f3-103">取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)的介面指標，表示主機預期會載入 common language RUNTIME （CLR）的元件清單。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f0f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f0f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f0f3-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="2f0f3-106">脫銷`ICLRAssemblyReferenceList` 位址的指標，其中包含主機預期 CLR 載入之元件的參考清單。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f0f3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2f0f3-107">Return Value</span></span>  
  
|<span data-ttu-id="2f0f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f0f3-108">HRESULT</span></span>|<span data-ttu-id="2f0f3-109">描述</span><span class="sxs-lookup"><span data-stu-id="2f0f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f0f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f0f3-110">S_OK</span></span>|<span data-ttu-id="2f0f3-111">已成功傳回 `GetNonHostStoreAssemblies`。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="2f0f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f0f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f0f3-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f0f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f0f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f0f3-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="2f0f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f0f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f0f3-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f0f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f0f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f0f3-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f0f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f0f3-120">E_FAIL</span></span>|<span data-ttu-id="2f0f3-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f0f3-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f0f3-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2f0f3-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2f0f3-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2f0f3-125">記憶體不足，無法建立所要求之 `ICLRAssemblyReferenceList`的參考清單。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f0f3-126">備註</span><span class="sxs-lookup"><span data-stu-id="2f0f3-126">Remarks</span></span>  
 <span data-ttu-id="2f0f3-127">CLR 會使用下列一組指導方針來解析參考：</span><span class="sxs-lookup"><span data-stu-id="2f0f3-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="2f0f3-128">首先，它會參考 `GetNonHostStoreAssemblies`所傳回的元件參考清單。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="2f0f3-129">如果元件出現在清單中，則 CLR 會正常地系結至它。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="2f0f3-130">如果元件未出現在清單中，而且主機已提供[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)的執行，則 CLR 會呼叫[IHostAssemblyStore：:P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) ，讓主機能夠提供要系結的元件。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="2f0f3-131">否則，CLR 會無法系結至元件。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="2f0f3-132">如果主機將 `ppReferenceList` 設為 null，則 CLR 會先探查全域組件快取、呼叫 `ProvideAssembly`，然後再探查應用程式基底，以解析元件參考。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f0f3-133">在初始化時，CLR 只會呼叫一次 `GetNonHostStoreAssemblies`。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="2f0f3-134">不會再次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f0f3-135">需求</span><span class="sxs-lookup"><span data-stu-id="2f0f3-135">Requirements</span></span>  
 <span data-ttu-id="2f0f3-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f0f3-137">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2f0f3-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f0f3-138">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2f0f3-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f0f3-139">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f0f3-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0f3-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f0f3-140">See also</span></span>

- [<span data-ttu-id="2f0f3-141">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="2f0f3-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2f0f3-142">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="2f0f3-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="2f0f3-143">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="2f0f3-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
