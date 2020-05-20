---
title: ICLRControl::SetAppDomainManagerType 方法
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: e62f9fd6b8421ea131eff0e6b36523718589c921
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615822"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="c2185-102">ICLRControl::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="c2185-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="c2185-103">將衍生自的類型設定 <xref:System.AppDomainManager> 為應用程式域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="c2185-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2185-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2185-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2185-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2185-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="c2185-106">在實作為衍生自之要求類型的元件名稱 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="c2185-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="c2185-107">在實作為參數的名稱，該類型 `pwzAppDomainManagerAssembly` 會執行的功能 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="c2185-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2185-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c2185-108">Return Value</span></span>  
  
|<span data-ttu-id="c2185-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2185-109">HRESULT</span></span>|<span data-ttu-id="c2185-110">說明</span><span class="sxs-lookup"><span data-stu-id="c2185-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2185-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2185-111">S_OK</span></span>|<span data-ttu-id="c2185-112">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c2185-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="c2185-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2185-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2185-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c2185-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2185-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2185-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2185-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="c2185-116">The call timed out.</span></span>|  
|<span data-ttu-id="c2185-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2185-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2185-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c2185-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2185-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2185-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2185-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="c2185-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2185-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2185-121">E_FAIL</span></span>|<span data-ttu-id="c2185-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c2185-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2185-123">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="c2185-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2185-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c2185-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2185-125">需求</span><span class="sxs-lookup"><span data-stu-id="c2185-125">Requirements</span></span>  
 <span data-ttu-id="c2185-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2185-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2185-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c2185-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2185-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c2185-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2185-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2185-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2185-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2185-130">See also</span></span>

- [<span data-ttu-id="c2185-131">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="c2185-131">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c2185-132">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="c2185-132">IHostControl Interface</span></span>](ihostcontrol-interface.md)
