---
title: "ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80ffc1cb4c1387aae673ec757b846c7075e20b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="fc5ea-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference 方法</span><span class="sxs-lookup"><span data-stu-id="fc5ea-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="fc5ea-103">取得[ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)具有指定的身分識別類型的組件所參考的組件識別的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc5ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc5ea-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc5ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc5ea-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="fc5ea-106">[in]有效的值，指定的處理器架構，因為在 WinNT.h 中定義。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fc5ea-107">[in]供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="fc5ea-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是唯一的目前版本的 common language runtime (CLR) 支援的值。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="fc5ea-109">[in]一個不透明的組件繫結的身分識別通常是從呼叫傳回[iclrassemblyidentitymanager:: Getbindingidentityfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)或[iclrassemblyidentitymanager:: Getbindingidentityfromstream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="fc5ea-110">[out]介面指標`ICLRProbingAssemblyEnum`列舉值，包含組件參考所識別的組件的參考`pwzReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc5ea-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc5ea-111">Return Value</span></span>  
  
|<span data-ttu-id="fc5ea-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc5ea-112">HRESULT</span></span>|<span data-ttu-id="fc5ea-113">描述</span><span class="sxs-lookup"><span data-stu-id="fc5ea-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc5ea-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc5ea-114">S_OK</span></span>|<span data-ttu-id="fc5ea-115">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="fc5ea-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc5ea-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc5ea-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc5ea-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc5ea-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc5ea-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-119">The call timed out.</span></span>|  
|<span data-ttu-id="fc5ea-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc5ea-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc5ea-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc5ea-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc5ea-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc5ea-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc5ea-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc5ea-124">E_FAIL</span></span>|<span data-ttu-id="fc5ea-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc5ea-126">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc5ea-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc5ea-128">需求</span><span class="sxs-lookup"><span data-stu-id="fc5ea-128">Requirements</span></span>  
 <span data-ttu-id="fc5ea-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5ea-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc5ea-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc5ea-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc5ea-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fc5ea-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc5ea-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc5ea-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5ea-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc5ea-133">See Also</span></span>  
 [<span data-ttu-id="fc5ea-134">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="fc5ea-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="fc5ea-135">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="fc5ea-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="fc5ea-136">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="fc5ea-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
