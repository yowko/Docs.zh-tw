---
title: IHostAssemblyStore::ProvideModule 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: eed09a8149a21140ad61133f29391f86cb0fb929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124478"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="525d8-102">IHostAssemblyStore::ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="525d8-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="525d8-103">解析元件中的模組或連結的（但不是內嵌的）資源檔。</span><span class="sxs-lookup"><span data-stu-id="525d8-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="525d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="525d8-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="525d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="525d8-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="525d8-106">在[ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)實例的指標，其描述所要求模組的 <xref:System.AppDomain>、元件和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="525d8-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="525d8-107">脫銷包含已載入模組之 `IStream` 唯一識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="525d8-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="525d8-108">脫銷`IStream` 物件的位址指標，其中包含要載入的可移植執行檔（PE）影像，如果找不到模組，則為 null。</span><span class="sxs-lookup"><span data-stu-id="525d8-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="525d8-109">脫銷`IStream` 物件的位址指標，其中包含所要求模組的程式 debug （PDB）資訊，如果找不到 .pdb 檔，則為 null。</span><span class="sxs-lookup"><span data-stu-id="525d8-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="525d8-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="525d8-110">Return Value</span></span>  
  
|<span data-ttu-id="525d8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="525d8-111">HRESULT</span></span>|<span data-ttu-id="525d8-112">描述</span><span class="sxs-lookup"><span data-stu-id="525d8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="525d8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="525d8-113">S_OK</span></span>|<span data-ttu-id="525d8-114">已成功傳回 `ProvideModule`。</span><span class="sxs-lookup"><span data-stu-id="525d8-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="525d8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="525d8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="525d8-116">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="525d8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="525d8-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="525d8-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="525d8-118">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="525d8-118">The call timed out.</span></span>|  
|<span data-ttu-id="525d8-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="525d8-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="525d8-120">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="525d8-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="525d8-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="525d8-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="525d8-122">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="525d8-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="525d8-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="525d8-123">E_FAIL</span></span>|<span data-ttu-id="525d8-124">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="525d8-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="525d8-125">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="525d8-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="525d8-126">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="525d8-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="525d8-127">COR_E_FILENOTFOUND （0x80070002）</span><span class="sxs-lookup"><span data-stu-id="525d8-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="525d8-128">找不到要求的元件或連結的資源。</span><span class="sxs-lookup"><span data-stu-id="525d8-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="525d8-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="525d8-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="525d8-130">`pdwModuleId` 不夠大，無法包含主機想要傳回的識別碼。</span><span class="sxs-lookup"><span data-stu-id="525d8-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="525d8-131">備註</span><span class="sxs-lookup"><span data-stu-id="525d8-131">Remarks</span></span>  
 <span data-ttu-id="525d8-132">針對 `pdwModuleId` 所傳回的識別值是由主機指定。</span><span class="sxs-lookup"><span data-stu-id="525d8-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="525d8-133">識別碼在進程的存留期間內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="525d8-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="525d8-134">CLR 會使用此值做為相關聯資料流程的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="525d8-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="525d8-135">它會根據[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)的呼叫 `pAssemblyId` 所傳回的值，以及針對 `ProvideModule`的其他呼叫所傳回的 `pdwModuleId` 值，檢查每個值。</span><span class="sxs-lookup"><span data-stu-id="525d8-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="525d8-136">如果主機針對另一個 `IStream`傳回相同的識別碼值，則 CLR 會檢查該資料流程的內容是否已對應。</span><span class="sxs-lookup"><span data-stu-id="525d8-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="525d8-137">若是如此，CLR 會載入影像的現有複本，而不是對應新的映射。</span><span class="sxs-lookup"><span data-stu-id="525d8-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="525d8-138">因此，此識別碼也不能與 `ProvideAssembly`傳回的元件識別碼重迭。</span><span class="sxs-lookup"><span data-stu-id="525d8-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="525d8-139">需求</span><span class="sxs-lookup"><span data-stu-id="525d8-139">Requirements</span></span>  
 <span data-ttu-id="525d8-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="525d8-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="525d8-141">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="525d8-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="525d8-142">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="525d8-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="525d8-143">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="525d8-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="525d8-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="525d8-144">See also</span></span>

- [<span data-ttu-id="525d8-145">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="525d8-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="525d8-146">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="525d8-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="525d8-147">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="525d8-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
