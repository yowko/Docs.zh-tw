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
ms.openlocfilehash: 35805d277774e1de03bb7dee1740a2e1305a97c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732992"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="a2dd0-102">IHostAssemblyStore::ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="a2dd0-102">IHostAssemblyStore::ProvideModule Method</span></span>

<span data-ttu-id="a2dd0-103">解析元件或連結 (內的模組，但不是內嵌) 資源檔。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2dd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2dd0-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2dd0-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2dd0-105">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="a2dd0-106">在 [ModuleBindInfo](modulebindinfo-structure.md) 實例的指標，可描述所要求模組的 <xref:System.AppDomain> 、元件和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-106">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="a2dd0-107">擴展的唯一識別碼指標， `IStream` 包含載入的模組。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="a2dd0-108">擴展物件位址的指標 `IStream` ，其中包含要載入的可攜式可執行檔 (PE) 映射，如果找不到模組，則為 null。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="a2dd0-109">擴展物件位址的指標 `IStream` ，其中包含所要求模組的程式 debug (PDB) 資訊; 如果找不到 .pdb 檔案，則為 null。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2dd0-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2dd0-110">Return Value</span></span>  
  
|<span data-ttu-id="a2dd0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2dd0-111">HRESULT</span></span>|<span data-ttu-id="a2dd0-112">描述</span><span class="sxs-lookup"><span data-stu-id="a2dd0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2dd0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2dd0-113">S_OK</span></span>|<span data-ttu-id="a2dd0-114">`ProvideModule` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="a2dd0-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2dd0-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2dd0-116">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2dd0-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2dd0-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2dd0-118">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-118">The call timed out.</span></span>|  
|<span data-ttu-id="a2dd0-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2dd0-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2dd0-120">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2dd0-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2dd0-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2dd0-122">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2dd0-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2dd0-123">E_FAIL</span></span>|<span data-ttu-id="a2dd0-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2dd0-125">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2dd0-126">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2dd0-127">COR_E_FILENOTFOUND (0x80070002) </span><span class="sxs-lookup"><span data-stu-id="a2dd0-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="a2dd0-128">找不到要求的元件或連結的資源。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="a2dd0-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a2dd0-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a2dd0-130">`pdwModuleId` 不夠大，無法包含主機想要傳回的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2dd0-131">備註</span><span class="sxs-lookup"><span data-stu-id="a2dd0-131">Remarks</span></span>  

 <span data-ttu-id="a2dd0-132">傳回的識別值 `pdwModuleId` 是由主控制項所指定。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="a2dd0-133">識別碼在進程的存留期內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="a2dd0-134">CLR 會使用此值做為相關資料流程的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="a2dd0-135">它會針對 `pAssemblyId` [ProvideAssembly](ihostassemblystore-provideassembly-method.md) 的呼叫，以及對的其他呼叫所傳回的值，檢查每個值的值 `pdwModuleId` `ProvideModule` 。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="a2dd0-136">如果主機為另一個傳回相同的識別碼值 `IStream` ，則 CLR 會檢查該資料流程的內容是否已對應。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="a2dd0-137">若是如此，CLR 就會載入映射的現有複本，而不是對應新的映射。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="a2dd0-138">因此，識別碼也必須與從傳回的元件識別碼重迭 `ProvideAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2dd0-139">需求</span><span class="sxs-lookup"><span data-stu-id="a2dd0-139">Requirements</span></span>  

 <span data-ttu-id="a2dd0-140">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2dd0-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2dd0-141">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a2dd0-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2dd0-142">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a2dd0-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2dd0-143">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2dd0-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2dd0-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2dd0-144">See also</span></span>

- [<span data-ttu-id="a2dd0-145">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="a2dd0-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a2dd0-146">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2dd0-146">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="a2dd0-147">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="a2dd0-147">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
