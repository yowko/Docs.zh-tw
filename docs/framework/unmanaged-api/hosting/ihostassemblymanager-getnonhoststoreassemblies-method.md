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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccd73963302ae99c7d5d1a7201bc77c4544363f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937901"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="d08c5-102">IHostAssemblyManager::GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="d08c5-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="d08c5-103">取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)的介面指標, 表示主機預期會載入 common language RUNTIME (CLR) 的元件清單。</span><span class="sxs-lookup"><span data-stu-id="d08c5-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="d08c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d08c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="d08c5-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="d08c5-106">脫銷位址的`ICLRAssemblyReferenceList`指標, 其中包含主機預期 CLR 載入之元件的參考清單。</span><span class="sxs-lookup"><span data-stu-id="d08c5-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d08c5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d08c5-107">Return Value</span></span>  
  
|<span data-ttu-id="d08c5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d08c5-108">HRESULT</span></span>|<span data-ttu-id="d08c5-109">描述</span><span class="sxs-lookup"><span data-stu-id="d08c5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d08c5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d08c5-110">S_OK</span></span>|<span data-ttu-id="d08c5-111">`GetNonHostStoreAssemblies`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d08c5-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="d08c5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d08c5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d08c5-113">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d08c5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d08c5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d08c5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d08c5-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d08c5-115">The call timed out.</span></span>|  
|<span data-ttu-id="d08c5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d08c5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d08c5-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d08c5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d08c5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d08c5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d08c5-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d08c5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d08c5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d08c5-120">E_FAIL</span></span>|<span data-ttu-id="d08c5-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d08c5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d08c5-122">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d08c5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d08c5-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d08c5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d08c5-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d08c5-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d08c5-125">沒有足夠的記憶體可用來建立所要求`ICLRAssemblyReferenceList`的參考清單。</span><span class="sxs-lookup"><span data-stu-id="d08c5-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d08c5-126">備註</span><span class="sxs-lookup"><span data-stu-id="d08c5-126">Remarks</span></span>  
 <span data-ttu-id="d08c5-127">CLR 會使用下列一組指導方針來解析參考:</span><span class="sxs-lookup"><span data-stu-id="d08c5-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="d08c5-128">首先, 它會參考所傳回`GetNonHostStoreAssemblies`的元件參考清單。</span><span class="sxs-lookup"><span data-stu-id="d08c5-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="d08c5-129">如果元件出現在清單中, 則 CLR 會正常地系結至它。</span><span class="sxs-lookup"><span data-stu-id="d08c5-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="d08c5-130">如果元件未出現在清單中, 而且主機已提供[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)的執行, 則 CLR 會呼叫[IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) , 讓主機能夠提供要系結的元件。</span><span class="sxs-lookup"><span data-stu-id="d08c5-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="d08c5-131">否則, CLR 會無法系結至元件。</span><span class="sxs-lookup"><span data-stu-id="d08c5-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="d08c5-132">如果主機設定`ppReferenceList`為 null, CLR 會先探查全域組件快取、呼叫`ProvideAssembly`, 然後再探查應用程式基底, 以解析元件參考。</span><span class="sxs-lookup"><span data-stu-id="d08c5-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d08c5-133">在初始化之後, CLR 只`GetNonHostStoreAssemblies`會呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="d08c5-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="d08c5-134">不會再次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="d08c5-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d08c5-135">需求</span><span class="sxs-lookup"><span data-stu-id="d08c5-135">Requirements</span></span>  
 <span data-ttu-id="d08c5-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d08c5-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d08c5-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d08c5-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d08c5-138">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d08c5-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d08c5-139">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d08c5-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08c5-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d08c5-140">See also</span></span>

- [<span data-ttu-id="d08c5-141">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="d08c5-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d08c5-142">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="d08c5-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d08c5-143">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="d08c5-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
