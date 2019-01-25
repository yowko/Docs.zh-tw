---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b3c727b49b7df48baa4f5084106f0586419133e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625689"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="8324e-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="8324e-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="8324e-103">取得[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)包含一份在指定的檔案路徑組件所參考的組件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8324e-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8324e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8324e-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8324e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8324e-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="8324e-106">[in]要評估的組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="8324e-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8324e-107">[in]供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="8324e-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8324e-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime (CLR) 支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="8324e-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="8324e-109">[in]指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)物件，表示要排除的組件`ppReferenceEnum`。</span><span class="sxs-lookup"><span data-stu-id="8324e-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="8324e-110">[out]位址指標`ICLRReferenceAssemblyEnum`包含在組件所參考的組件的組件身分識別資料的物件`pwzFilePath`，但不包括所表示的組件`pExcludeAssembliesList`。</span><span class="sxs-lookup"><span data-stu-id="8324e-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8324e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8324e-111">Return Value</span></span>  
  
|<span data-ttu-id="8324e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8324e-112">HRESULT</span></span>|<span data-ttu-id="8324e-113">描述</span><span class="sxs-lookup"><span data-stu-id="8324e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8324e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8324e-114">S_OK</span></span>|<span data-ttu-id="8324e-115">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="8324e-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8324e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8324e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8324e-117">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="8324e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8324e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8324e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8324e-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="8324e-119">The call timed out.</span></span>|  
|<span data-ttu-id="8324e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8324e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8324e-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8324e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8324e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8324e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8324e-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="8324e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8324e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8324e-124">E_FAIL</span></span>|<span data-ttu-id="8324e-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="8324e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8324e-126">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="8324e-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8324e-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8324e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8324e-128">備註</span><span class="sxs-lookup"><span data-stu-id="8324e-128">Remarks</span></span>  
 <span data-ttu-id="8324e-129">呼叫者可以選擇要傳回的清單中排除一組已知的組件參考。</span><span class="sxs-lookup"><span data-stu-id="8324e-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="8324e-130">此集合由定義`pExcludeAssembliesList`參數。</span><span class="sxs-lookup"><span data-stu-id="8324e-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8324e-131">需求</span><span class="sxs-lookup"><span data-stu-id="8324e-131">Requirements</span></span>  
 <span data-ttu-id="8324e-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8324e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8324e-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8324e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8324e-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8324e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8324e-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8324e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8324e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8324e-136">See also</span></span>
- [<span data-ttu-id="8324e-137">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="8324e-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8324e-138">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="8324e-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8324e-139">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8324e-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
