---
title: IHostSecurityManager::ImpersonateLoggedOnUser 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ceb199e027b111c8e29166d3b91027a3df2d534e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658607"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="d4fe7-102">IHostSecurityManager::ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="d4fe7-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="d4fe7-103">要求執行程式碼會使用目前的使用者身分識別的認證。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fe7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4fe7-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4fe7-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4fe7-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="d4fe7-106">[in]語彙基元，代表要模擬之使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4fe7-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4fe7-107">Return Value</span></span>  
  
|<span data-ttu-id="d4fe7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4fe7-108">HRESULT</span></span>|<span data-ttu-id="d4fe7-109">描述</span><span class="sxs-lookup"><span data-stu-id="d4fe7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4fe7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4fe7-110">S_OK</span></span>|<span data-ttu-id="d4fe7-111">`ImpersonateLoggedOnUser` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="d4fe7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4fe7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4fe7-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4fe7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4fe7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4fe7-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-115">The call timed out.</span></span>|  
|<span data-ttu-id="d4fe7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4fe7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4fe7-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4fe7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4fe7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4fe7-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4fe7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4fe7-120">E_FAIL</span></span>|<span data-ttu-id="d4fe7-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4fe7-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4fe7-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4fe7-124">備註</span><span class="sxs-lookup"><span data-stu-id="d4fe7-124">Remarks</span></span>  
 <span data-ttu-id="d4fe7-125">呼叫`LogonUser`或相關的 Win32 函式，可取得目前的使用者身分識別的認證的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="d4fe7-126">`HANDLE`類型不是 COM 相容，也就是它的大小是特定作業系統，而且需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="d4fe7-127">因此，此權杖是只在處理序中，CLR 和主機之間使用。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4fe7-128">需求</span><span class="sxs-lookup"><span data-stu-id="d4fe7-128">Requirements</span></span>  
 <span data-ttu-id="d4fe7-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4fe7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4fe7-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4fe7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4fe7-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d4fe7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4fe7-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4fe7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fe7-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4fe7-133">See also</span></span>
- [<span data-ttu-id="d4fe7-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="d4fe7-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d4fe7-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="d4fe7-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="d4fe7-136">RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="d4fe7-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
