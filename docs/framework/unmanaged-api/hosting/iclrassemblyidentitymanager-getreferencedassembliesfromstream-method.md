---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aae8c16430f8139601a5faa2bad42e285bceb84b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="8c90f-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="8c90f-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="8c90f-103">取得指標[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)物件，其中包含指定的資料流中的組件所參考之組件的組件識別資料。</span><span class="sxs-lookup"><span data-stu-id="8c90f-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c90f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c90f-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c90f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c90f-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="8c90f-106">[in]介面指標`IStream`包含要評估的組件。</span><span class="sxs-lookup"><span data-stu-id="8c90f-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8c90f-107">[in]供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="8c90f-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8c90f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是唯一的目前版本的 common language runtime (CLR) 支援的值。</span><span class="sxs-lookup"><span data-stu-id="8c90f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="8c90f-109">[in]指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)物件，其中包含要排除之組件的組件識別資料`ppReferenceEnum`。</span><span class="sxs-lookup"><span data-stu-id="8c90f-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="8c90f-110">[out]位址指標`ICLRReferenceAssemblyEnum`物件，包含組件識別資料中的組件所參考的組件`pStream`，但不包括中的組件`pExcludeAssembliesList`。</span><span class="sxs-lookup"><span data-stu-id="8c90f-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c90f-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8c90f-111">Return Value</span></span>  
  
|<span data-ttu-id="8c90f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c90f-112">HRESULT</span></span>|<span data-ttu-id="8c90f-113">描述</span><span class="sxs-lookup"><span data-stu-id="8c90f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c90f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c90f-114">S_OK</span></span>|<span data-ttu-id="8c90f-115">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8c90f-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8c90f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c90f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c90f-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8c90f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c90f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c90f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c90f-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="8c90f-119">The call timed out.</span></span>|  
|<span data-ttu-id="8c90f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c90f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c90f-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8c90f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c90f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c90f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c90f-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="8c90f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c90f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c90f-124">E_FAIL</span></span>|<span data-ttu-id="8c90f-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8c90f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c90f-126">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="8c90f-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c90f-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8c90f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c90f-128">備註</span><span class="sxs-lookup"><span data-stu-id="8c90f-128">Remarks</span></span>  
 <span data-ttu-id="8c90f-129">呼叫端可以選擇排除一組已知的組件參考從傳回的清單。</span><span class="sxs-lookup"><span data-stu-id="8c90f-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="8c90f-130">這個集合由定義`pExcludeAssembliesList`。</span><span class="sxs-lookup"><span data-stu-id="8c90f-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c90f-131">需求</span><span class="sxs-lookup"><span data-stu-id="8c90f-131">Requirements</span></span>  
 <span data-ttu-id="8c90f-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c90f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c90f-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c90f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c90f-134">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8c90f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c90f-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c90f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c90f-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c90f-136">See Also</span></span>  
 [<span data-ttu-id="8c90f-137">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="8c90f-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="8c90f-138">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="8c90f-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="8c90f-139">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8c90f-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
