---
title: "ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList 方法"
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
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eefe5ff68c7bd428c18729dcbd792b4c3cb64c2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="ce611-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="ce611-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="ce611-103">取得的介面指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)從提供的清單執行個體的部分組件識別。</span><span class="sxs-lookup"><span data-stu-id="ce611-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce611-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce611-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce611-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce611-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="ce611-106">[in]在表單中的 null 終止字串的陣列 」 名稱、 屬性 = 值...」 旗標會指定一份部分組件識別。</span><span class="sxs-lookup"><span data-stu-id="ce611-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="ce611-107">[in]中的項目數`ppwzAssemblyReferences`。</span><span class="sxs-lookup"><span data-stu-id="ce611-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="ce611-108">[out]介面指標`ICLRAssemblyReferenceList`物件，包含組件識別資料中指定的組件清單`ppwzAssemblyReferences`。</span><span class="sxs-lookup"><span data-stu-id="ce611-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce611-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ce611-109">Return Value</span></span>  
  
|<span data-ttu-id="ce611-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce611-110">HRESULT</span></span>|<span data-ttu-id="ce611-111">描述</span><span class="sxs-lookup"><span data-stu-id="ce611-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce611-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce611-112">S_OK</span></span>|<span data-ttu-id="ce611-113">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ce611-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="ce611-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ce611-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ce611-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ce611-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ce611-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ce611-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ce611-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="ce611-117">The call timed out.</span></span>|  
|<span data-ttu-id="ce611-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ce611-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ce611-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ce611-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ce611-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ce611-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ce611-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="ce611-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ce611-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ce611-122">E_FAIL</span></span>|<span data-ttu-id="ce611-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ce611-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ce611-124">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="ce611-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ce611-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ce611-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce611-126">需求</span><span class="sxs-lookup"><span data-stu-id="ce611-126">Requirements</span></span>  
 <span data-ttu-id="ce611-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce611-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce611-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce611-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce611-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ce611-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce611-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce611-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce611-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce611-131">See Also</span></span>  
 [<span data-ttu-id="ce611-132">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="ce611-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ce611-133">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="ce611-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
