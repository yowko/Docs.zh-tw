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
ms.openlocfilehash: db65519579104dd01816bb6d7cacaec947f24f53
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680861"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="8b8d4-102">IHostAssemblyStore::ProvideAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="8b8d4-102">IHostAssemblyStore::ProvideAssembly Method</span></span>

<span data-ttu-id="8b8d4-103">取得從[IHostAssemblyManager：： GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)傳回的[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)未參考之元件的參考。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="8b8d4-104">Common language runtime (CLR) 呼叫 `ProvideAssembly` 未出現在清單中的每個元件。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b8d4-105">語法</span><span class="sxs-lookup"><span data-stu-id="8b8d4-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b8d4-106">參數</span><span class="sxs-lookup"><span data-stu-id="8b8d4-106">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="8b8d4-107">在 [AssemblyBindInfo](assemblybindinfo-structure.md) 實例的指標，主機會使用此實例來判斷特定系結特性，包括是否存在任何版本控制原則，以及要系結至哪個元件。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-107">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="8b8d4-108">擴展所要求元件的唯一識別碼指標 `IStream` 。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="8b8d4-109">擴展主機特定資料的指標，可用來判斷所要求元件的辨識項，而不需要平台叫用呼叫。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="8b8d4-110">`pHostContext` 對應至 <xref:System.Reflection.Assembly.HostContext%2A> managed 類別的屬性 <xref:System.Reflection.Assembly> 。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="8b8d4-111">擴展的位址指標， `IStream` 其中包含要載入的可攜式可執行檔 (PE) 映射，如果找不到元件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="8b8d4-112">擴展的位址指標， `IStream` 其中包含程式 debug (PDB) 資訊; 如果找不到 .pdb 檔案，則為 null。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b8d4-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="8b8d4-113">Return Value</span></span>  
  
|<span data-ttu-id="8b8d4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b8d4-114">HRESULT</span></span>|<span data-ttu-id="8b8d4-115">描述</span><span class="sxs-lookup"><span data-stu-id="8b8d4-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b8d4-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b8d4-116">S_OK</span></span>|<span data-ttu-id="8b8d4-117">`ProvideAssembly` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="8b8d4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b8d4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b8d4-119">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b8d4-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b8d4-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b8d4-121">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-121">The call timed out.</span></span>|  
|<span data-ttu-id="8b8d4-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b8d4-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b8d4-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b8d4-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b8d4-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b8d4-125">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b8d4-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8b8d4-126">E_FAIL</span></span>|<span data-ttu-id="8b8d4-127">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b8d4-128">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b8d4-129">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8b8d4-130">COR_E_FILENOTFOUND (0x80070002) </span><span class="sxs-lookup"><span data-stu-id="8b8d4-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="8b8d4-131">找不到要求的元件。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="8b8d4-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8b8d4-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8b8d4-133">指定的緩衝區大小不夠 `pAssemblyId` 大，無法容納主機想要傳回的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b8d4-134">備註</span><span class="sxs-lookup"><span data-stu-id="8b8d4-134">Remarks</span></span>  

 <span data-ttu-id="8b8d4-135">傳回的識別值 `pAssemblyId` 是由主控制項所指定。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="8b8d4-136">識別碼在進程的存留期內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="8b8d4-137">CLR 會使用此值做為資料流程的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="8b8d4-138">它會根據的其他呼叫所傳回的值來檢查每個值 `pAssemblyId` `ProvideAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="8b8d4-139">如果主機 `pAssemblyId` 針對另一個傳回相同的值 `IStream` ，則 CLR 會檢查是否已對應該資料流程的內容。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="8b8d4-140">如果是，執行時間會載入映射的現有複本，而不是對應新的映射。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b8d4-141">需求</span><span class="sxs-lookup"><span data-stu-id="8b8d4-141">Requirements</span></span>  

 <span data-ttu-id="8b8d4-142">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b8d4-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b8d4-143">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8b8d4-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b8d4-144">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8b8d4-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b8d4-145">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b8d4-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8d4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b8d4-146">See also</span></span>

- [<span data-ttu-id="8b8d4-147">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="8b8d4-147">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8b8d4-148">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8b8d4-148">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="8b8d4-149">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="8b8d4-149">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
