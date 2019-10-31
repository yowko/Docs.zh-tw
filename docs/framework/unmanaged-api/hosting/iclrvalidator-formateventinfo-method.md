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
ms.openlocfilehash: 935d8e9fa3ed15be03c6cd05b1bc3c4919d0cc2b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127860"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="5aa9e-102">ICLRValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="5aa9e-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="5aa9e-103">取得有關指定之驗證錯誤的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5aa9e-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aa9e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5aa9e-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="5aa9e-106">在已傳遞至驗證錯誤處理常式的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="5aa9e-107">在`VEContext` 實例，其中包含有關驗證錯誤的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="5aa9e-108">[in、out]易記的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="5aa9e-109">在錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="5aa9e-110">在要在訊息中使用之其他參數的安全陣列。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aa9e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="5aa9e-111">Return Value</span></span>  
  
|<span data-ttu-id="5aa9e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5aa9e-112">HRESULT</span></span>|<span data-ttu-id="5aa9e-113">描述</span><span class="sxs-lookup"><span data-stu-id="5aa9e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5aa9e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5aa9e-114">S_OK</span></span>|<span data-ttu-id="5aa9e-115">已成功傳回 `FormatEventInfo`。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="5aa9e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5aa9e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5aa9e-117">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5aa9e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5aa9e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5aa9e-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-119">The call timed out.</span></span>|  
|<span data-ttu-id="5aa9e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5aa9e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5aa9e-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5aa9e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5aa9e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5aa9e-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5aa9e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5aa9e-124">E_FAIL</span></span>|<span data-ttu-id="5aa9e-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5aa9e-126">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5aa9e-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5aa9e-128">需求</span><span class="sxs-lookup"><span data-stu-id="5aa9e-128">Requirements</span></span>  
 <span data-ttu-id="5aa9e-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5aa9e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aa9e-130">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="5aa9e-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="5aa9e-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5aa9e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5aa9e-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aa9e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa9e-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="5aa9e-133">See also</span></span>

- [<span data-ttu-id="5aa9e-134">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="5aa9e-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="5aa9e-135">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="5aa9e-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
