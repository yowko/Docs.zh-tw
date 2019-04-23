---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e926fb2753367370e9aca726806eb8747e32048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153734"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="28ea6-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference 方法</span><span class="sxs-lookup"><span data-stu-id="28ea6-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="28ea6-103">取得[ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)具有指定的識別類型的組件所參考的組件身分識別的列舉值。</span><span class="sxs-lookup"><span data-stu-id="28ea6-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ea6-104">語法</span><span class="sxs-lookup"><span data-stu-id="28ea6-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28ea6-105">參數</span><span class="sxs-lookup"><span data-stu-id="28ea6-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="28ea6-106">[in]有效的值，指定處理器架構，因為在 WinNT.h 中定義。</span><span class="sxs-lookup"><span data-stu-id="28ea6-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="28ea6-107">[in]供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="28ea6-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="28ea6-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime (CLR) 支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="28ea6-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="28ea6-109">[in]不透明的組件繫結身分識別，通常從呼叫傳回[iclrassemblyidentitymanager:: Getbindingidentityfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)或[iclrassemblyidentitymanager:: Getbindingidentityfromstream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="28ea6-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="28ea6-110">[out]介面指標`ICLRProbingAssemblyEnum`列舉值，包含所識別的組件所參考的組件的參考`pwzReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="28ea6-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28ea6-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="28ea6-111">Return Value</span></span>  
  
|<span data-ttu-id="28ea6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28ea6-112">HRESULT</span></span>|<span data-ttu-id="28ea6-113">描述</span><span class="sxs-lookup"><span data-stu-id="28ea6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28ea6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="28ea6-114">S_OK</span></span>|<span data-ttu-id="28ea6-115">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="28ea6-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="28ea6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28ea6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28ea6-117">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="28ea6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28ea6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28ea6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28ea6-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="28ea6-119">The call timed out.</span></span>|  
|<span data-ttu-id="28ea6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28ea6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28ea6-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="28ea6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28ea6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28ea6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28ea6-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="28ea6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28ea6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28ea6-124">E_FAIL</span></span>|<span data-ttu-id="28ea6-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="28ea6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28ea6-126">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="28ea6-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28ea6-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="28ea6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28ea6-128">需求</span><span class="sxs-lookup"><span data-stu-id="28ea6-128">Requirements</span></span>  
 <span data-ttu-id="28ea6-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28ea6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ea6-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28ea6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28ea6-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="28ea6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28ea6-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ea6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ea6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28ea6-133">See also</span></span>

- [<span data-ttu-id="28ea6-134">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="28ea6-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="28ea6-135">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="28ea6-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="28ea6-136">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="28ea6-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
