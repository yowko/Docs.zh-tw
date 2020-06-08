---
title: IHostAssemblyStore::ProvideAssembly 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 162def0d703ea81efc3df3ea5ee08b58e34822e6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501569"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="1dd89-102">IHostAssemblyStore::ProvideAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="1dd89-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="1dd89-103">取得從[IHostAssemblyManager：： GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)傳回之[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)未參考的元件參考。</span><span class="sxs-lookup"><span data-stu-id="1dd89-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="1dd89-104">不 `ProvideAssembly` 會出現在清單中的每個元件的 common language runtime （CLR）呼叫。</span><span class="sxs-lookup"><span data-stu-id="1dd89-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd89-105">語法</span><span class="sxs-lookup"><span data-stu-id="1dd89-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd89-106">參數</span><span class="sxs-lookup"><span data-stu-id="1dd89-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="1dd89-107">在[AssemblyBindInfo](assemblybindinfo-structure.md)實例的指標，可供主機用來判斷特定系結特性，包括是否有任何版本設定原則，以及要系結至哪個元件。</span><span class="sxs-lookup"><span data-stu-id="1dd89-107">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="1dd89-108">脫銷這個之所要求元件的唯一識別碼指標 `IStream` 。</span><span class="sxs-lookup"><span data-stu-id="1dd89-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="1dd89-109">脫銷主機特定資料的指標，用來判斷所要求元件的辨識項，而不需要平台叫用呼叫。</span><span class="sxs-lookup"><span data-stu-id="1dd89-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="1dd89-110">`pHostContext`對應至 <xref:System.Reflection.Assembly.HostContext%2A> managed 類別的屬性 <xref:System.Reflection.Assembly> 。</span><span class="sxs-lookup"><span data-stu-id="1dd89-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="1dd89-111">脫銷位址的指標， `IStream` 其中包含要載入的可移植執行檔（PE）影像，如果找不到元件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="1dd89-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="1dd89-112">脫銷`IStream`包含程式 debug （PDB）資訊之位址的指標，如果找不到 .pdb 檔，則為 null。</span><span class="sxs-lookup"><span data-stu-id="1dd89-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dd89-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="1dd89-113">Return Value</span></span>  
  
|<span data-ttu-id="1dd89-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dd89-114">HRESULT</span></span>|<span data-ttu-id="1dd89-115">說明</span><span class="sxs-lookup"><span data-stu-id="1dd89-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dd89-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dd89-116">S_OK</span></span>|<span data-ttu-id="1dd89-117">`ProvideAssembly`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1dd89-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="1dd89-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1dd89-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1dd89-119">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1dd89-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1dd89-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1dd89-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1dd89-121">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="1dd89-121">The call timed out.</span></span>|  
|<span data-ttu-id="1dd89-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1dd89-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1dd89-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1dd89-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1dd89-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1dd89-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1dd89-125">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="1dd89-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1dd89-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1dd89-126">E_FAIL</span></span>|<span data-ttu-id="1dd89-127">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1dd89-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1dd89-128">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="1dd89-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1dd89-129">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1dd89-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1dd89-130">COR_E_FILENOTFOUND （0x80070002）</span><span class="sxs-lookup"><span data-stu-id="1dd89-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="1dd89-131">找不到要求的元件。</span><span class="sxs-lookup"><span data-stu-id="1dd89-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="1dd89-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1dd89-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1dd89-133">所指定的緩衝區大小不夠 `pAssemblyId` 大，無法容納主機想要傳回的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1dd89-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dd89-134">備註</span><span class="sxs-lookup"><span data-stu-id="1dd89-134">Remarks</span></span>  
 <span data-ttu-id="1dd89-135">為傳回的識別值 `pAssemblyId` 由主機指定。</span><span class="sxs-lookup"><span data-stu-id="1dd89-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="1dd89-136">識別碼在進程的存留期間內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1dd89-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="1dd89-137">CLR 會使用此值做為資料流程的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1dd89-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="1dd89-138">它會針對其他呼叫所傳回的值，檢查每個值 `pAssemblyId` `ProvideAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="1dd89-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="1dd89-139">如果主機 `pAssemblyId` 針對另一個傳回相同的值 `IStream` ，CLR 會檢查該資料流程的內容是否已對應。</span><span class="sxs-lookup"><span data-stu-id="1dd89-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="1dd89-140">若是如此，執行時間就會載入影像的現有複本，而不是對應新的映射。</span><span class="sxs-lookup"><span data-stu-id="1dd89-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd89-141">規格需求</span><span class="sxs-lookup"><span data-stu-id="1dd89-141">Requirements</span></span>  
 <span data-ttu-id="1dd89-142">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd89-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd89-143">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1dd89-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dd89-144">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1dd89-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd89-145">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd89-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd89-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd89-146">See also</span></span>

- [<span data-ttu-id="1dd89-147">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="1dd89-147">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1dd89-148">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="1dd89-148">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="1dd89-149">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="1dd89-149">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
