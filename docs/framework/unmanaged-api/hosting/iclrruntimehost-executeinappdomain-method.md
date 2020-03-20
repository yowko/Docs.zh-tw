---
title: ICLRRuntimeHost::ExecuteInAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176418"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="f4eb7-102">ICLRRuntimeHost::ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="f4eb7-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="f4eb7-103">指定<xref:System.AppDomain>在其中執行指定託管代碼的用中。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4eb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4eb7-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4eb7-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4eb7-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="f4eb7-106">[在]要在<xref:System.AppDomain>其中執行指定方法的數位 ID。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="f4eb7-107">[在]指向要在指定<xref:System.AppDomain>時間內執行的函數的指標。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="f4eb7-108">[在]指向不透明調用方分配的記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="f4eb7-109">此參數由通用語言運行時 （CLR） 傳遞給域回檔。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="f4eb7-110">它不是運行時管理的堆記憶體;它不是運行時管理的堆記憶體。此記憶體的分配和存留期都由調用方控制。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4eb7-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4eb7-111">Return Value</span></span>  
  
|<span data-ttu-id="f4eb7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4eb7-112">HRESULT</span></span>|<span data-ttu-id="f4eb7-113">描述</span><span class="sxs-lookup"><span data-stu-id="f4eb7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4eb7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4eb7-114">S_OK</span></span>|<span data-ttu-id="f4eb7-115">`ExecuteInAppDomain`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="f4eb7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4eb7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4eb7-117">CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4eb7-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4eb7-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4eb7-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-119">The call timed out.</span></span>|  
|<span data-ttu-id="f4eb7-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4eb7-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4eb7-121">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4eb7-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4eb7-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4eb7-123">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4eb7-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4eb7-124">E_FAIL</span></span>|<span data-ttu-id="f4eb7-125">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4eb7-126">如果方法返回E_FAIL，則 CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4eb7-127">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4eb7-128">備註</span><span class="sxs-lookup"><span data-stu-id="f4eb7-128">Remarks</span></span>  
 <span data-ttu-id="f4eb7-129">`ExecuteInAppDomain`允許主機控制應執行指定託管方法的<xref:System.AppDomain>託管方法。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="f4eb7-130">通過調用[GetCurrentAppDomainId 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)，可以獲取應用程式域識別碼的值，該識別碼<xref:System.AppDomain.Id%2A>對應于屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4eb7-131">需求</span><span class="sxs-lookup"><span data-stu-id="f4eb7-131">Requirements</span></span>  
 <span data-ttu-id="f4eb7-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4eb7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4eb7-133">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4eb7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4eb7-134">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f4eb7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4eb7-135">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4eb7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4eb7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4eb7-136">See also</span></span>

- [<span data-ttu-id="f4eb7-137">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="f4eb7-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
