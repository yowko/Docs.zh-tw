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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1d61e7495a3d95b5326e5051775e23e19cb1b45
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503082"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="8df09-102">IHostAssemblyStore::ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="8df09-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="8df09-103">解析組件或連結 （但非內嵌） 內的模組資源檔案。</span><span class="sxs-lookup"><span data-stu-id="8df09-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8df09-104">語法</span><span class="sxs-lookup"><span data-stu-id="8df09-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8df09-105">參數</span><span class="sxs-lookup"><span data-stu-id="8df09-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="8df09-106">[in]指標[ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)執行個體，描述要求的模組<xref:System.AppDomain>，組件，以及模組名稱。</span><span class="sxs-lookup"><span data-stu-id="8df09-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="8df09-107">[out]唯一識別碼的指標`IStream`包含載入的模組。</span><span class="sxs-lookup"><span data-stu-id="8df09-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="8df09-108">[out]位址指標`IStream`物件，其中包含要載入，可攜式執行檔 (PE) 映像，或如果找不到模組，則為 null。</span><span class="sxs-lookup"><span data-stu-id="8df09-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="8df09-109">[out]位址指標`IStream`物件，其中包含程式的偵錯 (PDB) 資訊要求的模組，或如果找不到.pdb 檔案，則為 null。</span><span class="sxs-lookup"><span data-stu-id="8df09-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8df09-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8df09-110">Return Value</span></span>  
  
|<span data-ttu-id="8df09-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8df09-111">HRESULT</span></span>|<span data-ttu-id="8df09-112">描述</span><span class="sxs-lookup"><span data-stu-id="8df09-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8df09-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8df09-113">S_OK</span></span>|<span data-ttu-id="8df09-114">`ProvideModule` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8df09-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="8df09-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8df09-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8df09-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="8df09-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8df09-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8df09-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8df09-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="8df09-118">The call timed out.</span></span>|  
|<span data-ttu-id="8df09-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8df09-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8df09-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8df09-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8df09-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8df09-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8df09-122">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="8df09-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8df09-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8df09-123">E_FAIL</span></span>|<span data-ttu-id="8df09-124">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="8df09-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8df09-125">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="8df09-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8df09-126">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8df09-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8df09-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="8df09-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="8df09-128">要求的組件或連結的資源找不到。</span><span class="sxs-lookup"><span data-stu-id="8df09-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="8df09-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8df09-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8df09-130">`pdwModuleId` 不能夠容納主機想要傳回的識別項。</span><span class="sxs-lookup"><span data-stu-id="8df09-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8df09-131">備註</span><span class="sxs-lookup"><span data-stu-id="8df09-131">Remarks</span></span>  
 <span data-ttu-id="8df09-132">針對傳回的識別值`pdwModuleId`由主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8df09-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="8df09-133">在處理序的存留期內，識別碼必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8df09-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="8df09-134">CLR 會使用此值的唯一識別碼做為相關聯的資料流。</span><span class="sxs-lookup"><span data-stu-id="8df09-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="8df09-135">它會檢查每個值的值對`pAssemblyId`呼叫所傳回[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)而的值是針對`pdwModuleId`傳回的其他呼叫`ProvideModule`。</span><span class="sxs-lookup"><span data-stu-id="8df09-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="8df09-136">如果主應用程式會傳回相同的識別碼值的另一個`IStream`，CLR 會檢查該資料流的內容是否已經對應。</span><span class="sxs-lookup"><span data-stu-id="8df09-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="8df09-137">如果是的話，則 CLR 會載入而不是一個新的映像的現有副本。</span><span class="sxs-lookup"><span data-stu-id="8df09-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="8df09-138">因此，識別項也不能重疊與從傳回的組件識別碼`ProvideAssembly`。</span><span class="sxs-lookup"><span data-stu-id="8df09-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8df09-139">需求</span><span class="sxs-lookup"><span data-stu-id="8df09-139">Requirements</span></span>  
 <span data-ttu-id="8df09-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8df09-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8df09-141">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8df09-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8df09-142">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8df09-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8df09-143">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8df09-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df09-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8df09-144">See also</span></span>
- [<span data-ttu-id="8df09-145">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="8df09-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8df09-146">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8df09-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="8df09-147">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="8df09-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
