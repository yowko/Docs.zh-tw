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
ms.openlocfilehash: a34b907514376927d8a1aa66b136916108b704d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681141"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="be48f-102">IHostAssemblyManager::GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="be48f-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>

<span data-ttu-id="be48f-103">取得 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 的介面指標，該指標表示主機預期 common language RUNTIME (CLR) 載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="be48f-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be48f-104">語法</span><span class="sxs-lookup"><span data-stu-id="be48f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be48f-105">參數</span><span class="sxs-lookup"><span data-stu-id="be48f-105">Parameters</span></span>  

 `ppReferenceList`  
 <span data-ttu-id="be48f-106">擴展的位址指標 `ICLRAssemblyReferenceList` ，其中包含主機預期 CLR 載入的元件參考清單。</span><span class="sxs-lookup"><span data-stu-id="be48f-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be48f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="be48f-107">Return Value</span></span>  
  
|<span data-ttu-id="be48f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be48f-108">HRESULT</span></span>|<span data-ttu-id="be48f-109">描述</span><span class="sxs-lookup"><span data-stu-id="be48f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be48f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="be48f-110">S_OK</span></span>|<span data-ttu-id="be48f-111">`GetNonHostStoreAssemblies` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="be48f-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="be48f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be48f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be48f-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="be48f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be48f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be48f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be48f-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="be48f-115">The call timed out.</span></span>|  
|<span data-ttu-id="be48f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be48f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be48f-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="be48f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be48f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be48f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be48f-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="be48f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be48f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be48f-120">E_FAIL</span></span>|<span data-ttu-id="be48f-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="be48f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be48f-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="be48f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be48f-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="be48f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="be48f-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="be48f-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="be48f-125">沒有足夠的記憶體可用來建立所要求的參考清單 `ICLRAssemblyReferenceList` 。</span><span class="sxs-lookup"><span data-stu-id="be48f-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be48f-126">備註</span><span class="sxs-lookup"><span data-stu-id="be48f-126">Remarks</span></span>  

 <span data-ttu-id="be48f-127">CLR 會使用下列一組指導方針來解析參考：</span><span class="sxs-lookup"><span data-stu-id="be48f-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="be48f-128">首先，它會查閱所傳回的元件參考清單 `GetNonHostStoreAssemblies` 。</span><span class="sxs-lookup"><span data-stu-id="be48f-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="be48f-129">如果元件出現在清單中，則 CLR 會正常地系結至該元件。</span><span class="sxs-lookup"><span data-stu-id="be48f-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="be48f-130">如果元件未出現在清單中，且主機已提供 [IHostAssemblyStore](ihostassemblystore-interface.md)的執行，則 CLR 會呼叫 [IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md) ，以允許主機提供要系結的元件。</span><span class="sxs-lookup"><span data-stu-id="be48f-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="be48f-131">否則，CLR 會無法系結至元件。</span><span class="sxs-lookup"><span data-stu-id="be48f-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="be48f-132">如果主機設 `ppReferenceList` 為 null，CLR 會先探查全域組件快取、呼叫 `ProvideAssembly` ，然後探查應用程式基底來解析元件參考。</span><span class="sxs-lookup"><span data-stu-id="be48f-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be48f-133">初始化時，CLR 只會呼叫 `GetNonHostStoreAssemblies` 一次。</span><span class="sxs-lookup"><span data-stu-id="be48f-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="be48f-134">未再次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="be48f-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be48f-135">需求</span><span class="sxs-lookup"><span data-stu-id="be48f-135">Requirements</span></span>  

 <span data-ttu-id="be48f-136">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be48f-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be48f-137">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="be48f-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be48f-138">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="be48f-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be48f-139">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be48f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be48f-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be48f-140">See also</span></span>

- [<span data-ttu-id="be48f-141">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="be48f-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="be48f-142">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="be48f-142">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="be48f-143">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="be48f-143">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
