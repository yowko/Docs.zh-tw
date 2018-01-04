---
title: "IHostAssemblyStore::ProvideModule 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore.ProvideModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b29f19933ae985d15627d1eba2622f350a52e72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="5b70f-102">IHostAssemblyStore::ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="5b70f-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="5b70f-103">解析組件或連結 （但非內嵌） 內模組資源檔案。</span><span class="sxs-lookup"><span data-stu-id="5b70f-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b70f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b70f-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b70f-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b70f-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="5b70f-106">[in]指標[ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)說明要求的模組的執行個體<xref:System.AppDomain>，組件和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="5b70f-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="5b70f-107">[out]唯一識別碼的指標`IStream`包含載入的模組。</span><span class="sxs-lookup"><span data-stu-id="5b70f-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="5b70f-108">[out]位址指標`IStream`物件，其中包含要載入的可攜式執行檔 (PE) 影像，或如果找不到模組，則為 null。</span><span class="sxs-lookup"><span data-stu-id="5b70f-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="5b70f-109">[out]位址指標`IStream`物件，其中包含程式的偵錯 (PDB) 資訊要求的模組，或如果找不到.pdb 檔案，則為 null。</span><span class="sxs-lookup"><span data-stu-id="5b70f-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b70f-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="5b70f-110">Return Value</span></span>  
  
|<span data-ttu-id="5b70f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b70f-111">HRESULT</span></span>|<span data-ttu-id="5b70f-112">描述</span><span class="sxs-lookup"><span data-stu-id="5b70f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b70f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b70f-113">S_OK</span></span>|<span data-ttu-id="5b70f-114">`ProvideModule`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5b70f-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="5b70f-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b70f-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b70f-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5b70f-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b70f-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b70f-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b70f-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5b70f-118">The call timed out.</span></span>|  
|<span data-ttu-id="5b70f-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b70f-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b70f-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5b70f-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b70f-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b70f-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b70f-122">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5b70f-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b70f-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b70f-123">E_FAIL</span></span>|<span data-ttu-id="5b70f-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5b70f-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b70f-125">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="5b70f-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b70f-126">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5b70f-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5b70f-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="5b70f-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="5b70f-128">已連結之資源的要求的組件找不到。</span><span class="sxs-lookup"><span data-stu-id="5b70f-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="5b70f-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5b70f-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5b70f-130">`pdwModuleId`不大小足以包含主應用程式想要傳回的識別項。</span><span class="sxs-lookup"><span data-stu-id="5b70f-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b70f-131">備註</span><span class="sxs-lookup"><span data-stu-id="5b70f-131">Remarks</span></span>  
 <span data-ttu-id="5b70f-132">傳回識別值`pdwModuleId`由主應用程式所指定。</span><span class="sxs-lookup"><span data-stu-id="5b70f-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="5b70f-133">處理序的存留期內，識別項必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5b70f-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="5b70f-134">CLR 會使用此值的唯一識別碼做為相關聯的資料流。</span><span class="sxs-lookup"><span data-stu-id="5b70f-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="5b70f-135">它會檢查每個值的值對`pAssemblyId`呼叫所傳回[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)針對值和`pdwModuleId`其他呼叫所傳回`ProvideModule`。</span><span class="sxs-lookup"><span data-stu-id="5b70f-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="5b70f-136">如果主應用程式會傳回相同的識別碼值的另一個`IStream`，CLR 會檢查是否已經對應資料流的內容。</span><span class="sxs-lookup"><span data-stu-id="5b70f-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="5b70f-137">如果是這樣，CLR 載入而不是一個新的映像的現有複本。</span><span class="sxs-lookup"><span data-stu-id="5b70f-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="5b70f-138">因此，識別項也不能重疊從傳回的組件識別項`ProvideAssembly`。</span><span class="sxs-lookup"><span data-stu-id="5b70f-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b70f-139">需求</span><span class="sxs-lookup"><span data-stu-id="5b70f-139">Requirements</span></span>  
 <span data-ttu-id="5b70f-140">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b70f-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b70f-141">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b70f-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b70f-142">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5b70f-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b70f-143">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b70f-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b70f-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b70f-144">See Also</span></span>  
 [<span data-ttu-id="5b70f-145">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="5b70f-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="5b70f-146">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="5b70f-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="5b70f-147">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="5b70f-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
