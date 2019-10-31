---
title: ICLRHostProtectionManager::SetProtectedCategories 方法
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: e3f2429462b4454e87690d98ad9fb446574add91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141043"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="5e3d9-102">ICLRHostProtectionManager::SetProtectedCategories 方法</span><span class="sxs-lookup"><span data-stu-id="5e3d9-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="5e3d9-103">指定應該封鎖哪些類別的 managed 類型和成員，而不是在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e3d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e3d9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e3d9-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e3d9-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="5e3d9-106">在[EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)值的組合，表示應該封鎖哪些類別的 managed 類型和成員，而不是在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e3d9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e3d9-107">Return Value</span></span>  
  
|<span data-ttu-id="5e3d9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e3d9-108">HRESULT</span></span>|<span data-ttu-id="5e3d9-109">描述</span><span class="sxs-lookup"><span data-stu-id="5e3d9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e3d9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e3d9-110">S_OK</span></span>|<span data-ttu-id="5e3d9-111">已成功傳回 `SetProtectedCategories`。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="5e3d9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e3d9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e3d9-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e3d9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e3d9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e3d9-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-115">The call timed out.</span></span>|  
|<span data-ttu-id="5e3d9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e3d9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e3d9-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e3d9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e3d9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e3d9-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e3d9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e3d9-120">E_FAIL</span></span>|<span data-ttu-id="5e3d9-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e3d9-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e3d9-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e3d9-124">備註</span><span class="sxs-lookup"><span data-stu-id="5e3d9-124">Remarks</span></span>  
 <span data-ttu-id="5e3d9-125">每個 `EApiCategories` 值都會參考 managed 類型和成員的清單。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="5e3d9-126">`EApiCategories` 列舉和 `SetProtectedCategories` 方法與 managed <xref:System.Security.Permissions.HostProtectionAttribute> 類別直接相關，這是用來標記 managed 類型和成員，而這些類別會公開對應至 `EApiCategories`所描述之分類的功能。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="5e3d9-127">如需詳細資訊，請參閱 <xref:System.Security.Permissions.HostProtectionAttribute> 和 <xref:System.Security.Permissions.HostProtectionResource> 列舉，這會直接對應至 `EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e3d9-128">需求</span><span class="sxs-lookup"><span data-stu-id="5e3d9-128">Requirements</span></span>  
 <span data-ttu-id="5e3d9-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e3d9-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e3d9-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5e3d9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e3d9-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5e3d9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e3d9-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e3d9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3d9-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e3d9-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="5e3d9-134">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="5e3d9-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="5e3d9-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="5e3d9-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="5e3d9-136">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5e3d9-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
