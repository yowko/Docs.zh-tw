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
ms.openlocfilehash: 54c11e78438ae97e1fc0c715c9161361784b3be6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126724"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="88f76-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="88f76-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="88f76-103">從提供的部分元件識別清單中，取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="88f76-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f76-104">語法</span><span class="sxs-lookup"><span data-stu-id="88f76-104">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88f76-105">參數</span><span class="sxs-lookup"><span data-stu-id="88f76-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="88f76-106">在以 null 結束的字串陣列，格式為 "name，property = value ..."，指定部分元件身分識別的清單。</span><span class="sxs-lookup"><span data-stu-id="88f76-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="88f76-107">在`ppwzAssemblyReferences`中的專案數。</span><span class="sxs-lookup"><span data-stu-id="88f76-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="88f76-108">脫銷`ICLRAssemblyReferenceList` 物件的介面指標，其中包含 `ppwzAssemblyReferences`中指定之元件清單的元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="88f76-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88f76-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="88f76-109">Return Value</span></span>  
  
|<span data-ttu-id="88f76-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88f76-110">HRESULT</span></span>|<span data-ttu-id="88f76-111">描述</span><span class="sxs-lookup"><span data-stu-id="88f76-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88f76-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="88f76-112">S_OK</span></span>|<span data-ttu-id="88f76-113">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="88f76-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="88f76-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88f76-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88f76-115">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="88f76-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88f76-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88f76-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88f76-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="88f76-117">The call timed out.</span></span>|  
|<span data-ttu-id="88f76-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88f76-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88f76-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="88f76-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88f76-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88f76-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88f76-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="88f76-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88f76-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88f76-122">E_FAIL</span></span>|<span data-ttu-id="88f76-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="88f76-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88f76-124">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="88f76-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88f76-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="88f76-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88f76-126">需求</span><span class="sxs-lookup"><span data-stu-id="88f76-126">Requirements</span></span>  
 <span data-ttu-id="88f76-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88f76-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88f76-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="88f76-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88f76-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="88f76-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88f76-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88f76-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f76-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="88f76-131">See also</span></span>

- [<span data-ttu-id="88f76-132">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="88f76-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="88f76-133">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="88f76-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
