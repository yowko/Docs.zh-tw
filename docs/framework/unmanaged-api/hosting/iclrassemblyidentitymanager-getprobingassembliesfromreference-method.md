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
ms.openlocfilehash: 21ebd0c64d6c8bbdac327258ad4c7ffec83a1ce9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504312"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="e67e4-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference 方法</span><span class="sxs-lookup"><span data-stu-id="e67e4-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="e67e4-103">取得具有指定之識別類型之元件所參考之元件識別的[ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="e67e4-103">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e67e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="e67e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e67e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="e67e4-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="e67e4-106">在指定處理器架構的有效值，如 WinNT. h 中所定義。</span><span class="sxs-lookup"><span data-stu-id="e67e4-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e67e4-107">在提供供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="e67e4-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="e67e4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime （CLR）所支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="e67e4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="e67e4-109">在不透明的元件系結識別，通常是從呼叫[ICLRAssemblyIdentityManager：： GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)或[ICLRAssemblyIdentityManager：： GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)方法傳回。</span><span class="sxs-lookup"><span data-stu-id="e67e4-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="e67e4-110">脫銷列舉值的介面指標 `ICLRProbingAssemblyEnum` ，其中包含由所識別之元件所參考的元件參考 `pwzReferenceIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="e67e4-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e67e4-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e67e4-111">Return Value</span></span>  
  
|<span data-ttu-id="e67e4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e67e4-112">HRESULT</span></span>|<span data-ttu-id="e67e4-113">說明</span><span class="sxs-lookup"><span data-stu-id="e67e4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e67e4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e67e4-114">S_OK</span></span>|<span data-ttu-id="e67e4-115">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e67e4-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="e67e4-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e67e4-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e67e4-117">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e67e4-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e67e4-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e67e4-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e67e4-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e67e4-119">The call timed out.</span></span>|  
|<span data-ttu-id="e67e4-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e67e4-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e67e4-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e67e4-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e67e4-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e67e4-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e67e4-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e67e4-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e67e4-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e67e4-124">E_FAIL</span></span>|<span data-ttu-id="e67e4-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e67e4-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e67e4-126">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="e67e4-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e67e4-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e67e4-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e67e4-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="e67e4-128">Requirements</span></span>  
 <span data-ttu-id="e67e4-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e67e4-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e67e4-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e67e4-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e67e4-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e67e4-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e67e4-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e67e4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67e4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e67e4-133">See also</span></span>

- [<span data-ttu-id="e67e4-134">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="e67e4-134">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e67e4-135">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="e67e4-135">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e67e4-136">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e67e4-136">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
