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
ms.openlocfilehash: 002f4177f19c2aae99e91e3fe1029b81e17481dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805004"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="b5312-102">IHostAssemblyStore::ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="b5312-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="b5312-103">解析元件中的模組或連結的（但不是內嵌的）資源檔。</span><span class="sxs-lookup"><span data-stu-id="b5312-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5312-104">語法</span><span class="sxs-lookup"><span data-stu-id="b5312-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5312-105">參數</span><span class="sxs-lookup"><span data-stu-id="b5312-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="b5312-106">在[ModuleBindInfo](modulebindinfo-structure.md)實例的指標，其描述所要求的模組 <xref:System.AppDomain> 、元件和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="b5312-106">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="b5312-107">脫銷包含已載入模組之唯一識別碼的指標 `IStream` 。</span><span class="sxs-lookup"><span data-stu-id="b5312-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="b5312-108">脫銷物件位址的指標 `IStream` ，其中包含要載入的可移植執行檔（PE）影像，如果找不到模組，則為 null。</span><span class="sxs-lookup"><span data-stu-id="b5312-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="b5312-109">脫銷物件位址的指標 `IStream` ，其中包含所要求模組的程式 debug （PDB）資訊，如果找不到 .pdb 檔，則為 null。</span><span class="sxs-lookup"><span data-stu-id="b5312-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5312-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b5312-110">Return Value</span></span>  
  
|<span data-ttu-id="b5312-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5312-111">HRESULT</span></span>|<span data-ttu-id="b5312-112">描述</span><span class="sxs-lookup"><span data-stu-id="b5312-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5312-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5312-113">S_OK</span></span>|<span data-ttu-id="b5312-114">`ProvideModule`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b5312-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="b5312-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5312-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5312-116">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b5312-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5312-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5312-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5312-118">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b5312-118">The call timed out.</span></span>|  
|<span data-ttu-id="b5312-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5312-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5312-120">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b5312-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5312-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5312-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5312-122">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b5312-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5312-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5312-123">E_FAIL</span></span>|<span data-ttu-id="b5312-124">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b5312-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5312-125">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="b5312-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5312-126">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b5312-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b5312-127">COR_E_FILENOTFOUND （0x80070002）</span><span class="sxs-lookup"><span data-stu-id="b5312-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="b5312-128">找不到要求的元件或連結的資源。</span><span class="sxs-lookup"><span data-stu-id="b5312-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="b5312-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b5312-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b5312-130">`pdwModuleId`不夠大，無法包含主機想要傳回的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b5312-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5312-131">備註</span><span class="sxs-lookup"><span data-stu-id="b5312-131">Remarks</span></span>  
 <span data-ttu-id="b5312-132">為傳回的識別值 `pdwModuleId` 由主機指定。</span><span class="sxs-lookup"><span data-stu-id="b5312-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="b5312-133">識別碼在進程的存留期間內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="b5312-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="b5312-134">CLR 會使用此值做為相關聯資料流程的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="b5312-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="b5312-135">它會根據 ProvideAssembly 的呼叫所傳回的值 `pAssemblyId` ，以及[ProvideAssembly](ihostassemblystore-provideassembly-method.md)針對其他呼叫所傳回的值，檢查每個值 `pdwModuleId` `ProvideModule` 。</span><span class="sxs-lookup"><span data-stu-id="b5312-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="b5312-136">如果主機針對另一個傳回相同的識別碼值 `IStream` ，CLR 會檢查該資料流程的內容是否已對應。</span><span class="sxs-lookup"><span data-stu-id="b5312-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="b5312-137">若是如此，CLR 會載入影像的現有複本，而不是對應新的映射。</span><span class="sxs-lookup"><span data-stu-id="b5312-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="b5312-138">因此，此識別碼也不能與從傳回的元件識別碼重迭 `ProvideAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="b5312-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5312-139">規格需求</span><span class="sxs-lookup"><span data-stu-id="b5312-139">Requirements</span></span>  
 <span data-ttu-id="b5312-140">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5312-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5312-141">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b5312-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5312-142">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b5312-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5312-143">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5312-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5312-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5312-144">See also</span></span>

- [<span data-ttu-id="b5312-145">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="b5312-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b5312-146">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b5312-146">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="b5312-147">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="b5312-147">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
