---
title: "ICLRRuntimeHost::UnloadAppDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.UnloadAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec5e32ccc9311f2f89252c0db5849304f2186de2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="25bcd-102">ICLRRuntimeHost::UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="25bcd-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="25bcd-103">卸載 managed<xref:System.AppDomain>對應於指定的數值識別項。</span><span class="sxs-lookup"><span data-stu-id="25bcd-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25bcd-104">語法</span><span class="sxs-lookup"><span data-stu-id="25bcd-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25bcd-105">參數</span><span class="sxs-lookup"><span data-stu-id="25bcd-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="25bcd-106">[in]卸載的應用程式定義域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="25bcd-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="25bcd-107">[in]`true`表示 common language runtime (CLR) 必須等到完成之前嘗試卸載應用程式定義域中執行的應用程式目前的執行緒之前。</span><span class="sxs-lookup"><span data-stu-id="25bcd-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25bcd-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="25bcd-108">Return Value</span></span>  
  
|<span data-ttu-id="25bcd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25bcd-109">HRESULT</span></span>|<span data-ttu-id="25bcd-110">描述</span><span class="sxs-lookup"><span data-stu-id="25bcd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25bcd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="25bcd-111">S_OK</span></span>|<span data-ttu-id="25bcd-112">`UnloadAppDomain`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="25bcd-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="25bcd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25bcd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25bcd-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="25bcd-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25bcd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25bcd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25bcd-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="25bcd-116">The call timed out.</span></span>|  
|<span data-ttu-id="25bcd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25bcd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25bcd-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="25bcd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25bcd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25bcd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25bcd-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="25bcd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25bcd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25bcd-121">E_FAIL</span></span>|<span data-ttu-id="25bcd-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="25bcd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25bcd-123">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="25bcd-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25bcd-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="25bcd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25bcd-125">備註</span><span class="sxs-lookup"><span data-stu-id="25bcd-125">Remarks</span></span>  
 <span data-ttu-id="25bcd-126">您可以取得藉由呼叫目前執行緒正在執行的所在的應用程式定義域的數值識別碼[GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)。</span><span class="sxs-lookup"><span data-stu-id="25bcd-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="25bcd-127">這個識別碼會對應到<xref:System.AppDomain.Id%2A>managed 屬性<xref:System.AppDomain>型別。</span><span class="sxs-lookup"><span data-stu-id="25bcd-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25bcd-128">需求</span><span class="sxs-lookup"><span data-stu-id="25bcd-128">Requirements</span></span>  
 <span data-ttu-id="25bcd-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25bcd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25bcd-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25bcd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25bcd-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25bcd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25bcd-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25bcd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bcd-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25bcd-133">See Also</span></span>  
 [<span data-ttu-id="25bcd-134">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="25bcd-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
