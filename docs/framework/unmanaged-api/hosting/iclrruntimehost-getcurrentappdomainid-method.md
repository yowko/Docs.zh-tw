---
title: ICLRRuntimeHost::GetCurrentAppDomainId 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f262c416a6998ed182d0c42d7f00ea7dcb3f898
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768689"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="e3d15-102">ICLRRuntimeHost::GetCurrentAppDomainId 方法</span><span class="sxs-lookup"><span data-stu-id="e3d15-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="e3d15-103">取得的數值識別碼<xref:System.AppDomain>，目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="e3d15-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3d15-104">語法</span><span class="sxs-lookup"><span data-stu-id="e3d15-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3d15-105">參數</span><span class="sxs-lookup"><span data-stu-id="e3d15-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="e3d15-106">[out]數值識別碼<xref:System.AppDomain>，目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="e3d15-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3d15-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e3d15-107">Return Value</span></span>  
  
|<span data-ttu-id="e3d15-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3d15-108">HRESULT</span></span>|<span data-ttu-id="e3d15-109">描述</span><span class="sxs-lookup"><span data-stu-id="e3d15-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3d15-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3d15-110">S_OK</span></span>|<span data-ttu-id="e3d15-111">`GetCurrentAppDomainId` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e3d15-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="e3d15-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3d15-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3d15-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e3d15-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e3d15-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e3d15-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e3d15-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e3d15-115">The call timed out.</span></span>|  
|<span data-ttu-id="e3d15-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3d15-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e3d15-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e3d15-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e3d15-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e3d15-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e3d15-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e3d15-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e3d15-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3d15-120">E_FAIL</span></span>|<span data-ttu-id="e3d15-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3d15-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e3d15-122">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="e3d15-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e3d15-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e3d15-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3d15-124">備註</span><span class="sxs-lookup"><span data-stu-id="e3d15-124">Remarks</span></span>  
 <span data-ttu-id="e3d15-125">`pdwAppDomainId`參數設定的值為<xref:System.AppDomain.Id%2A>屬性<xref:System.AppDomain>中目前的執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="e3d15-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3d15-126">需求</span><span class="sxs-lookup"><span data-stu-id="e3d15-126">Requirements</span></span>  
 <span data-ttu-id="e3d15-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d15-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3d15-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3d15-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3d15-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e3d15-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3d15-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3d15-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d15-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3d15-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="e3d15-132">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e3d15-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
