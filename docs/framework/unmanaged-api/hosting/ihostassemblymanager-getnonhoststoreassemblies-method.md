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
ms.openlocfilehash: b0da548d5d5cc22eb6754859a802afa4d82fac89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438385"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="b2498-102">IHostAssemblyManager::GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="b2498-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="b2498-103">取得的介面指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)代表主應用程式所預期的 common language runtime (CLR) 載入的組件清單。</span><span class="sxs-lookup"><span data-stu-id="b2498-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2498-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2498-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2498-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2498-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="b2498-106">[out]位址指標`ICLRAssemblyReferenceList`，其中包含一份主應用程式必須要有 CLR 載入的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b2498-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2498-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b2498-107">Return Value</span></span>  
  
|<span data-ttu-id="b2498-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2498-108">HRESULT</span></span>|<span data-ttu-id="b2498-109">描述</span><span class="sxs-lookup"><span data-stu-id="b2498-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2498-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2498-110">S_OK</span></span>|<span data-ttu-id="b2498-111">`GetNonHostStoreAssemblies` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b2498-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="b2498-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2498-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2498-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2498-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2498-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2498-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2498-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b2498-115">The call timed out.</span></span>|  
|<span data-ttu-id="b2498-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2498-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2498-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b2498-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2498-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2498-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2498-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b2498-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2498-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2498-120">E_FAIL</span></span>|<span data-ttu-id="b2498-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b2498-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2498-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="b2498-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2498-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b2498-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b2498-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b2498-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b2498-125">沒有足夠的記憶體可用來建立要求的參考清單`ICLRAssemblyReferenceList`。</span><span class="sxs-lookup"><span data-stu-id="b2498-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2498-126">備註</span><span class="sxs-lookup"><span data-stu-id="b2498-126">Remarks</span></span>  
 <span data-ttu-id="b2498-127">CLR 會解析參考使用下列的指導方針：</span><span class="sxs-lookup"><span data-stu-id="b2498-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="b2498-128">首先，它會參照組件參考所傳回的清單`GetNonHostStoreAssemblies`。</span><span class="sxs-lookup"><span data-stu-id="b2498-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="b2498-129">如果組件出現在清單中，CLR 繫結到它正常。</span><span class="sxs-lookup"><span data-stu-id="b2498-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="b2498-130">如果組件不會出現在清單中，而且主機所提供的實作[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)，CLR 會呼叫[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) ，讓主機提供要繫結至組件。</span><span class="sxs-lookup"><span data-stu-id="b2498-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="b2498-131">否則，CLR 就會將繫結至組件失敗。</span><span class="sxs-lookup"><span data-stu-id="b2498-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="b2498-132">如果主機設定`ppReferenceList`全域組件快取中，會呼叫為 null，CLR 的第一個探查`ProvideAssembly`，然後探查來解析組件參考的應用程式基底。</span><span class="sxs-lookup"><span data-stu-id="b2498-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2498-133">在啟動時，CLR 會呼叫`GetNonHostStoreAssemblies`一次。</span><span class="sxs-lookup"><span data-stu-id="b2498-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="b2498-134">不會再次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b2498-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2498-135">需求</span><span class="sxs-lookup"><span data-stu-id="b2498-135">Requirements</span></span>  
 <span data-ttu-id="b2498-136">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2498-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2498-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2498-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2498-138">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b2498-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2498-139">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2498-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2498-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2498-140">See Also</span></span>  
 [<span data-ttu-id="b2498-141">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="b2498-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="b2498-142">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b2498-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="b2498-143">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="b2498-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
