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
ms.openlocfilehash: 721cf93f1edecfc347c5ab6efa056aebd4dc6f9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434157"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="d6c0f-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="d6c0f-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="d6c0f-103">取得[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)包含在指定的檔案路徑的組件所參考的組件清單的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c0f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6c0f-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6c0f-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6c0f-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="d6c0f-106">[in]要評估的組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d6c0f-107">[in]供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="d6c0f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是唯一的目前版本的 common language runtime (CLR) 支援的值。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="d6c0f-109">[in]指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)物件，表示組件時，應該排除`ppReferenceEnum`。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="d6c0f-110">[out]位址指標`ICLRReferenceAssemblyEnum`物件，包含在組件所參考的組件的組件識別資料`pwzFilePath`，但不包括組件由`pExcludeAssembliesList`。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6c0f-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d6c0f-111">Return Value</span></span>  
  
|<span data-ttu-id="d6c0f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6c0f-112">HRESULT</span></span>|<span data-ttu-id="d6c0f-113">描述</span><span class="sxs-lookup"><span data-stu-id="d6c0f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6c0f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6c0f-114">S_OK</span></span>|<span data-ttu-id="d6c0f-115">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="d6c0f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6c0f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6c0f-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6c0f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6c0f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6c0f-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-119">The call timed out.</span></span>|  
|<span data-ttu-id="d6c0f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6c0f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6c0f-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6c0f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6c0f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6c0f-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6c0f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6c0f-124">E_FAIL</span></span>|<span data-ttu-id="d6c0f-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6c0f-126">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6c0f-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6c0f-128">備註</span><span class="sxs-lookup"><span data-stu-id="d6c0f-128">Remarks</span></span>  
 <span data-ttu-id="d6c0f-129">呼叫端可以選擇排除一組已知的組件參考從傳回的清單。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="d6c0f-130">這個集合由定義`pExcludeAssembliesList`參數。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c0f-131">需求</span><span class="sxs-lookup"><span data-stu-id="d6c0f-131">Requirements</span></span>  
 <span data-ttu-id="d6c0f-132">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c0f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c0f-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6c0f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6c0f-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d6c0f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6c0f-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c0f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c0f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6c0f-136">See Also</span></span>  
 [<span data-ttu-id="d6c0f-137">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="d6c0f-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d6c0f-138">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="d6c0f-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d6c0f-139">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d6c0f-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
