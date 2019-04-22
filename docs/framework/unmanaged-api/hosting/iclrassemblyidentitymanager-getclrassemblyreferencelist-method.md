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
ms.openlocfilehash: de166a22350e49197ff6a5b5d6dc956cdcc2d1ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089506"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="89beb-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="89beb-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="89beb-103">取得的介面指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)提供的清單中的部分組件身分識別執行個體。</span><span class="sxs-lookup"><span data-stu-id="89beb-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89beb-104">語法</span><span class="sxs-lookup"><span data-stu-id="89beb-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89beb-105">參數</span><span class="sxs-lookup"><span data-stu-id="89beb-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="89beb-106">[in]在表單中的 null 終止字串的陣列 」 名稱、 屬性 = 值...」指定部分組件身分識別的清單。</span><span class="sxs-lookup"><span data-stu-id="89beb-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="89beb-107">[in]中的項目數`ppwzAssemblyReferences`。</span><span class="sxs-lookup"><span data-stu-id="89beb-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="89beb-108">[out]介面指標`ICLRAssemblyReferenceList`物件，包含組件身分識別資料中指定的組件清單的`ppwzAssemblyReferences`。</span><span class="sxs-lookup"><span data-stu-id="89beb-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89beb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="89beb-109">Return Value</span></span>  
  
|<span data-ttu-id="89beb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89beb-110">HRESULT</span></span>|<span data-ttu-id="89beb-111">描述</span><span class="sxs-lookup"><span data-stu-id="89beb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89beb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="89beb-112">S_OK</span></span>|<span data-ttu-id="89beb-113">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="89beb-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="89beb-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="89beb-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="89beb-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="89beb-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="89beb-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="89beb-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="89beb-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="89beb-117">The call timed out.</span></span>|  
|<span data-ttu-id="89beb-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="89beb-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="89beb-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="89beb-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="89beb-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="89beb-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="89beb-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="89beb-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="89beb-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="89beb-122">E_FAIL</span></span>|<span data-ttu-id="89beb-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="89beb-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="89beb-124">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="89beb-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="89beb-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="89beb-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89beb-126">需求</span><span class="sxs-lookup"><span data-stu-id="89beb-126">Requirements</span></span>  
 <span data-ttu-id="89beb-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89beb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89beb-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89beb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89beb-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="89beb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89beb-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89beb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89beb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89beb-131">See also</span></span>

- [<span data-ttu-id="89beb-132">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="89beb-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="89beb-133">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="89beb-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
