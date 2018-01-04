---
title: "ICLRValidator::FormatEventInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4178d92bea44be269df8a69a628b6cb1a53dae4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="23124-102">ICLRValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="23124-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="23124-103">取得有關指定之驗證錯誤的詳細的訊息。</span><span class="sxs-lookup"><span data-stu-id="23124-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23124-104">語法</span><span class="sxs-lookup"><span data-stu-id="23124-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23124-105">參數</span><span class="sxs-lookup"><span data-stu-id="23124-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="23124-106">[in]HRESULT 值傳遞給驗證的錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="23124-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="23124-107">[in]A`VEContext`執行個體，其中包含驗證錯誤的相關內容資訊。</span><span class="sxs-lookup"><span data-stu-id="23124-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="23124-108">[in、 out]易懂的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="23124-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="23124-109">[in]錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="23124-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="23124-110">[in]其他參數，以用於訊息的安全陣列。</span><span class="sxs-lookup"><span data-stu-id="23124-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23124-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="23124-111">Return Value</span></span>  
  
|<span data-ttu-id="23124-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23124-112">HRESULT</span></span>|<span data-ttu-id="23124-113">描述</span><span class="sxs-lookup"><span data-stu-id="23124-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23124-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="23124-114">S_OK</span></span>|<span data-ttu-id="23124-115">`FormatEventInfo`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="23124-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="23124-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23124-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23124-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="23124-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="23124-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23124-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="23124-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="23124-119">The call timed out.</span></span>|  
|<span data-ttu-id="23124-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="23124-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="23124-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="23124-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="23124-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="23124-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="23124-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="23124-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="23124-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23124-124">E_FAIL</span></span>|<span data-ttu-id="23124-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="23124-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="23124-126">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="23124-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="23124-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="23124-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23124-128">需求</span><span class="sxs-lookup"><span data-stu-id="23124-128">Requirements</span></span>  
 <span data-ttu-id="23124-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23124-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23124-130">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="23124-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="23124-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="23124-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23124-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23124-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23124-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="23124-133">See Also</span></span>  
 [<span data-ttu-id="23124-134">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="23124-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="23124-135">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="23124-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
