---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bfb3e07504570f8cedceddb43410b48691c4695
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595756"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="74665-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="74665-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="74665-103">取得的介面指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)提供的清單中的部分組件身分識別執行個體。</span><span class="sxs-lookup"><span data-stu-id="74665-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74665-104">語法</span><span class="sxs-lookup"><span data-stu-id="74665-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74665-105">參數</span><span class="sxs-lookup"><span data-stu-id="74665-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="74665-106">[in]形式的 null 終止字串的陣列 」 名稱、 屬性 = 值...」，以指定的部分組件身分識別清單。</span><span class="sxs-lookup"><span data-stu-id="74665-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="74665-107">[in]中的項目數`ppwzAssemblyReferences`。</span><span class="sxs-lookup"><span data-stu-id="74665-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="74665-108">[out]介面指標`ICLRAssemblyReferenceList`物件，包含組件身分識別資料中指定的組件清單的`ppwzAssemblyReferences`。</span><span class="sxs-lookup"><span data-stu-id="74665-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74665-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="74665-109">Return Value</span></span>  
  
|<span data-ttu-id="74665-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74665-110">HRESULT</span></span>|<span data-ttu-id="74665-111">描述</span><span class="sxs-lookup"><span data-stu-id="74665-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74665-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="74665-112">S_OK</span></span>|<span data-ttu-id="74665-113">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="74665-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="74665-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74665-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74665-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="74665-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74665-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74665-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74665-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="74665-117">The call timed out.</span></span>|  
|<span data-ttu-id="74665-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74665-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74665-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="74665-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74665-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74665-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74665-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="74665-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74665-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74665-122">E_FAIL</span></span>|<span data-ttu-id="74665-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="74665-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74665-124">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="74665-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74665-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="74665-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74665-126">需求</span><span class="sxs-lookup"><span data-stu-id="74665-126">Requirements</span></span>  
 <span data-ttu-id="74665-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74665-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74665-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74665-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74665-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="74665-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74665-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74665-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74665-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74665-131">See also</span></span>
- [<span data-ttu-id="74665-132">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="74665-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="74665-133">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="74665-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
