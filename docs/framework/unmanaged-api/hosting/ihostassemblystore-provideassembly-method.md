---
title: "IHostAssemblyStore::ProvideAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2097c1ea64e5e9a2a09e0ec57243624b05eeea65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="d4e17-102">IHostAssemblyStore::ProvideAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="d4e17-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="d4e17-103">取得未被參考的組件的參考[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)從傳回[ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d4e17-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="d4e17-104">Common language runtime (CLR) 呼叫`ProvideAssembly`不會出現在清單中每一個組件。</span><span class="sxs-lookup"><span data-stu-id="d4e17-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e17-105">語法</span><span class="sxs-lookup"><span data-stu-id="d4e17-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4e17-106">參數</span><span class="sxs-lookup"><span data-stu-id="d4e17-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="d4e17-107">[in]指標[AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)主機用來判斷特定繫結的特性，包括任何版本設定的原則，是否存在的執行個體和要繫結至哪個組件。</span><span class="sxs-lookup"><span data-stu-id="d4e17-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="d4e17-108">[out]這個要求的組件的唯一識別碼的指標`IStream`。</span><span class="sxs-lookup"><span data-stu-id="d4e17-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="d4e17-109">[out]用來判斷要求的組件，而不需要為平台的辨識項的主應用程式特定資料的指標叫用呼叫。</span><span class="sxs-lookup"><span data-stu-id="d4e17-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="d4e17-110">`pHostContext`對應至<xref:System.Reflection.Assembly.HostContext%2A>managed 屬性<xref:System.Reflection.Assembly>類別。</span><span class="sxs-lookup"><span data-stu-id="d4e17-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="d4e17-111">[out]位址指標`IStream`其中包含要載入，或者如果找不到組件，則為 null 的可攜式執行檔 (PE) 映像。</span><span class="sxs-lookup"><span data-stu-id="d4e17-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="d4e17-112">[out]位址指標`IStream`如果找不到.pdb 檔案包含的程式 (PDB) 偵錯資訊或為 null。</span><span class="sxs-lookup"><span data-stu-id="d4e17-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4e17-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4e17-113">Return Value</span></span>  
  
|<span data-ttu-id="d4e17-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4e17-114">HRESULT</span></span>|<span data-ttu-id="d4e17-115">描述</span><span class="sxs-lookup"><span data-stu-id="d4e17-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4e17-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4e17-116">S_OK</span></span>|<span data-ttu-id="d4e17-117">`ProvideAssembly`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d4e17-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="d4e17-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4e17-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4e17-119">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d4e17-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4e17-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4e17-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4e17-121">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d4e17-121">The call timed out.</span></span>|  
|<span data-ttu-id="d4e17-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4e17-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4e17-123">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d4e17-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4e17-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4e17-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4e17-125">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d4e17-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4e17-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4e17-126">E_FAIL</span></span>|<span data-ttu-id="d4e17-127">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d4e17-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4e17-128">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d4e17-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4e17-129">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d4e17-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d4e17-130">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="d4e17-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="d4e17-131">找不到要求的組件。</span><span class="sxs-lookup"><span data-stu-id="d4e17-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="d4e17-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d4e17-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d4e17-133">所指定的緩衝區大小`pAssemblyId`不夠大，無法保存主應用程式想要傳回的識別項。</span><span class="sxs-lookup"><span data-stu-id="d4e17-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4e17-134">備註</span><span class="sxs-lookup"><span data-stu-id="d4e17-134">Remarks</span></span>  
 <span data-ttu-id="d4e17-135">傳回識別值`pAssemblyId`由主應用程式所指定。</span><span class="sxs-lookup"><span data-stu-id="d4e17-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="d4e17-136">處理序的存留期內，識別項必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d4e17-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="d4e17-137">資料流，CLR 會使用此值做為唯一的識別項。</span><span class="sxs-lookup"><span data-stu-id="d4e17-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="d4e17-138">它會檢查每個值的值對`pAssemblyId`其他呼叫所傳回`ProvideAssembly`。</span><span class="sxs-lookup"><span data-stu-id="d4e17-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="d4e17-139">如果主機傳回相同`pAssemblyId`另一個值`IStream`，CLR 會檢查是否已經對應資料流的內容。</span><span class="sxs-lookup"><span data-stu-id="d4e17-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="d4e17-140">如果是這樣，執行階段載入而不是一個新的映像的現有複本。</span><span class="sxs-lookup"><span data-stu-id="d4e17-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e17-141">需求</span><span class="sxs-lookup"><span data-stu-id="d4e17-141">Requirements</span></span>  
 <span data-ttu-id="d4e17-142">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4e17-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e17-143">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4e17-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4e17-144">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d4e17-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4e17-145">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e17-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e17-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4e17-146">See Also</span></span>  
 [<span data-ttu-id="d4e17-147">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="d4e17-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d4e17-148">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="d4e17-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="d4e17-149">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="d4e17-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
