---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
ms.openlocfilehash: f4c200ad23ff7a71298e84fda857912da53978a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126688"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="b911c-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="b911c-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="b911c-103">取得[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)物件的指標，其中包含指定的資料流程中元件所參考之元件的元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="b911c-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b911c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b911c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b911c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b911c-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="b911c-106">在`IStream` 的介面指標，其中包含要評估的元件。</span><span class="sxs-lookup"><span data-stu-id="b911c-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b911c-107">在提供供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="b911c-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="b911c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime （CLR）所支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="b911c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="b911c-109">在[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)物件的指標，其中包含要從 `ppReferenceEnum`中排除之元件的元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="b911c-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="b911c-110">脫銷`ICLRReferenceAssemblyEnum` 物件的位址指標，其中包含 `pStream`中元件所參考元件的元件識別資料，但不包括 `pExcludeAssembliesList`中的元件。</span><span class="sxs-lookup"><span data-stu-id="b911c-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b911c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="b911c-111">Return Value</span></span>  
  
|<span data-ttu-id="b911c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b911c-112">HRESULT</span></span>|<span data-ttu-id="b911c-113">描述</span><span class="sxs-lookup"><span data-stu-id="b911c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b911c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b911c-114">S_OK</span></span>|<span data-ttu-id="b911c-115">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="b911c-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="b911c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b911c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b911c-117">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b911c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b911c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b911c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b911c-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b911c-119">The call timed out.</span></span>|  
|<span data-ttu-id="b911c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b911c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b911c-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b911c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b911c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b911c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b911c-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b911c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b911c-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b911c-124">E_FAIL</span></span>|<span data-ttu-id="b911c-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b911c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b911c-126">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b911c-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b911c-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b911c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b911c-128">備註</span><span class="sxs-lookup"><span data-stu-id="b911c-128">Remarks</span></span>  
 <span data-ttu-id="b911c-129">呼叫端可以選擇從傳回的清單中排除一組已知的元件參考。</span><span class="sxs-lookup"><span data-stu-id="b911c-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="b911c-130">這個集合是由 `pExcludeAssembliesList`所定義。</span><span class="sxs-lookup"><span data-stu-id="b911c-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b911c-131">需求</span><span class="sxs-lookup"><span data-stu-id="b911c-131">Requirements</span></span>  
 <span data-ttu-id="b911c-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b911c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b911c-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b911c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b911c-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b911c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b911c-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b911c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b911c-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="b911c-136">See also</span></span>

- [<span data-ttu-id="b911c-137">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="b911c-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b911c-138">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="b911c-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b911c-139">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b911c-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
