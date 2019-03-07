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
ms.openlocfilehash: 85f74eb3c6f159cf2c8c8cbd186695dc97489504
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469192"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="33c30-102">IHostAssemblyManager::GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="33c30-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="33c30-103">取得的介面指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)表示主機預期的 common language runtime (CLR) 載入的組件清單。</span><span class="sxs-lookup"><span data-stu-id="33c30-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c30-104">語法</span><span class="sxs-lookup"><span data-stu-id="33c30-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33c30-105">參數</span><span class="sxs-lookup"><span data-stu-id="33c30-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="33c30-106">[out]位址指標`ICLRAssemblyReferenceList`，其中包含一份主應用程式必須要有 CLR 載入的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="33c30-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33c30-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="33c30-107">Return Value</span></span>  
  
|<span data-ttu-id="33c30-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33c30-108">HRESULT</span></span>|<span data-ttu-id="33c30-109">描述</span><span class="sxs-lookup"><span data-stu-id="33c30-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33c30-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="33c30-110">S_OK</span></span>|<span data-ttu-id="33c30-111">`GetNonHostStoreAssemblies` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="33c30-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="33c30-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33c30-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33c30-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="33c30-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33c30-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33c30-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33c30-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="33c30-115">The call timed out.</span></span>|  
|<span data-ttu-id="33c30-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33c30-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33c30-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="33c30-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33c30-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33c30-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33c30-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="33c30-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33c30-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33c30-120">E_FAIL</span></span>|<span data-ttu-id="33c30-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="33c30-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33c30-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="33c30-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33c30-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="33c30-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="33c30-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="33c30-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="33c30-125">沒有足夠的記憶體可用來建立所要求之參考清單`ICLRAssemblyReferenceList`。</span><span class="sxs-lookup"><span data-stu-id="33c30-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33c30-126">備註</span><span class="sxs-lookup"><span data-stu-id="33c30-126">Remarks</span></span>  
 <span data-ttu-id="33c30-127">CLR 解析參考使用下列的指導方針：</span><span class="sxs-lookup"><span data-stu-id="33c30-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="33c30-128">首先，它會查詢所傳回的組件參考清單`GetNonHostStoreAssemblies`。</span><span class="sxs-lookup"><span data-stu-id="33c30-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="33c30-129">如果組件出現在清單中，CLR 繫結至它正常。</span><span class="sxs-lookup"><span data-stu-id="33c30-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="33c30-130">如果組件不會出現在清單中，而且主應用程式已提供實作[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)，CLR 會呼叫[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) ，讓主機提供要繫結至組件。</span><span class="sxs-lookup"><span data-stu-id="33c30-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="33c30-131">否則，CLR 就會繫結至組件失敗。</span><span class="sxs-lookup"><span data-stu-id="33c30-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="33c30-132">如果主應用程式設定`ppReferenceList`為 null，CLR 的第一個探查全域組件快取中，會呼叫`ProvideAssembly`，並接著會探查應用程式基底，解析組件參考。</span><span class="sxs-lookup"><span data-stu-id="33c30-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33c30-133">在啟動時，CLR 會呼叫`GetNonHostStoreAssemblies`一次。</span><span class="sxs-lookup"><span data-stu-id="33c30-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="33c30-134">不會再次呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="33c30-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c30-135">需求</span><span class="sxs-lookup"><span data-stu-id="33c30-135">Requirements</span></span>  
 <span data-ttu-id="33c30-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33c30-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33c30-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="33c30-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33c30-138">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="33c30-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33c30-139">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33c30-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c30-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33c30-140">See also</span></span>
- [<span data-ttu-id="33c30-141">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="33c30-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="33c30-142">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="33c30-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="33c30-143">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="33c30-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
