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
ms.openlocfilehash: 65dc330e88cb2457cc34f9994313373ab1ab84aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126707"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="cc949-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="cc949-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="cc949-103">取得[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)實例，其中包含元件在指定檔案路徑中參考的元件清單。</span><span class="sxs-lookup"><span data-stu-id="cc949-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc949-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc949-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc949-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc949-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="cc949-106">在要評估之元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="cc949-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cc949-107">在提供供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="cc949-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="cc949-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime （CLR）所支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="cc949-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="cc949-109">在[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)物件的指標，表示應該從 `ppReferenceEnum`排除的元件。</span><span class="sxs-lookup"><span data-stu-id="cc949-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="cc949-110">脫銷`ICLRReferenceAssemblyEnum` 物件位址的指標，其中包含元件在 `pwzFilePath`的元件識別資料，但不包括 `pExcludeAssembliesList`所代表的元件。</span><span class="sxs-lookup"><span data-stu-id="cc949-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc949-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="cc949-111">Return Value</span></span>  
  
|<span data-ttu-id="cc949-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc949-112">HRESULT</span></span>|<span data-ttu-id="cc949-113">描述</span><span class="sxs-lookup"><span data-stu-id="cc949-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc949-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc949-114">S_OK</span></span>|<span data-ttu-id="cc949-115">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="cc949-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="cc949-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc949-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc949-117">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="cc949-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc949-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc949-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc949-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="cc949-119">The call timed out.</span></span>|  
|<span data-ttu-id="cc949-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc949-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc949-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc949-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc949-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc949-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc949-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="cc949-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc949-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc949-124">E_FAIL</span></span>|<span data-ttu-id="cc949-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="cc949-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc949-126">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="cc949-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc949-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cc949-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc949-128">備註</span><span class="sxs-lookup"><span data-stu-id="cc949-128">Remarks</span></span>  
 <span data-ttu-id="cc949-129">呼叫端可以選擇從傳回的清單中排除一組已知的元件參考。</span><span class="sxs-lookup"><span data-stu-id="cc949-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="cc949-130">這個集合是由 `pExcludeAssembliesList` 參數所定義。</span><span class="sxs-lookup"><span data-stu-id="cc949-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc949-131">需求</span><span class="sxs-lookup"><span data-stu-id="cc949-131">Requirements</span></span>  
 <span data-ttu-id="cc949-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc949-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc949-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="cc949-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc949-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cc949-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc949-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc949-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc949-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc949-136">See also</span></span>

- [<span data-ttu-id="cc949-137">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="cc949-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="cc949-138">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="cc949-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="cc949-139">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="cc949-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
