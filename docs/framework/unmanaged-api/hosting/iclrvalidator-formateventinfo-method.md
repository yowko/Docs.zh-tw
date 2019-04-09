---
title: ICLRValidator::FormatEventInfo 方法
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9117a82dff48dcda8d96f0feb7b8c4a001fa17f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205871"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="a1565-102">ICLRValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a1565-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="a1565-103">取得有關指定之驗證錯誤的詳細的訊息。</span><span class="sxs-lookup"><span data-stu-id="a1565-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1565-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1565-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1565-105">參數</span><span class="sxs-lookup"><span data-stu-id="a1565-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="a1565-106">[in]HRESULT 值傳遞給驗證的錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="a1565-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="a1565-107">[in]A`VEContext`包含驗證錯誤相關的內容資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a1565-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="a1565-108">[in、 out]易懂的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a1565-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="a1565-109">[in]錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="a1565-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="a1565-110">[in]使用訊息中的其他參數的安全陣列。</span><span class="sxs-lookup"><span data-stu-id="a1565-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1565-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a1565-111">Return Value</span></span>  
  
|<span data-ttu-id="a1565-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1565-112">HRESULT</span></span>|<span data-ttu-id="a1565-113">描述</span><span class="sxs-lookup"><span data-stu-id="a1565-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1565-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1565-114">S_OK</span></span>|`FormatEventInfo` <span data-ttu-id="a1565-115">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a1565-115">returned successfully.</span></span>|  
|<span data-ttu-id="a1565-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1565-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1565-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a1565-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1565-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1565-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1565-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a1565-119">The call timed out.</span></span>|  
|<span data-ttu-id="a1565-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1565-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1565-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a1565-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1565-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1565-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1565-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a1565-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1565-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1565-124">E_FAIL</span></span>|<span data-ttu-id="a1565-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1565-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1565-126">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="a1565-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1565-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a1565-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1565-128">需求</span><span class="sxs-lookup"><span data-stu-id="a1565-128">Requirements</span></span>  
 <span data-ttu-id="a1565-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1565-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1565-130">**標頭：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="a1565-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a1565-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a1565-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a1565-132">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="a1565-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1565-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1565-133">See also</span></span>

- [<span data-ttu-id="a1565-134">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="a1565-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="a1565-135">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="a1565-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
