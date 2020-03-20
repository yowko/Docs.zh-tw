---
title: ICLRValidator::Validate 方法
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178054"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="6af74-102">ICLRValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="6af74-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="6af74-103">驗證指定檔中的可移植可執行 （PE） 或 Microsoft 中間語言 （MSIL）。</span><span class="sxs-lookup"><span data-stu-id="6af74-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af74-104">語法</span><span class="sxs-lookup"><span data-stu-id="6af74-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="6af74-105">參數</span><span class="sxs-lookup"><span data-stu-id="6af74-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="6af74-106">[在]指向處理驗證錯誤的`IVEHandler`實例的指標。</span><span class="sxs-lookup"><span data-stu-id="6af74-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="6af74-107">[在]當前<xref:System.AppDomain>的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6af74-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="6af74-108">[在][驗證器標誌](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值的組合，指示應執行的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="6af74-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="6af74-109">[在]退出驗證之前要允許的最大錯誤數。</span><span class="sxs-lookup"><span data-stu-id="6af74-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="6af74-110">[在]閒置。</span><span class="sxs-lookup"><span data-stu-id="6af74-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="6af74-111">[在]要驗證的檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="6af74-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="6af74-112">[在]指向檔案緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="6af74-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="6af74-113">[在]要驗證的檔的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6af74-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6af74-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="6af74-114">Return Value</span></span>  
  
|<span data-ttu-id="6af74-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6af74-115">HRESULT</span></span>|<span data-ttu-id="6af74-116">描述</span><span class="sxs-lookup"><span data-stu-id="6af74-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6af74-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="6af74-117">S_OK</span></span>|<span data-ttu-id="6af74-118">`Validate`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="6af74-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="6af74-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6af74-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6af74-120">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="6af74-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6af74-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6af74-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6af74-122">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="6af74-122">The call timed out.</span></span>|  
|<span data-ttu-id="6af74-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6af74-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6af74-124">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="6af74-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6af74-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6af74-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6af74-126">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="6af74-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6af74-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6af74-127">E_FAIL</span></span>|<span data-ttu-id="6af74-128">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="6af74-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6af74-129">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="6af74-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6af74-130">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6af74-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6af74-131">需求</span><span class="sxs-lookup"><span data-stu-id="6af74-131">Requirements</span></span>  
 <span data-ttu-id="6af74-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6af74-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af74-133">**標題：** I 驗證器.idl， I 驗證器.h</span><span class="sxs-lookup"><span data-stu-id="6af74-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6af74-134">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6af74-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6af74-135">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af74-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af74-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af74-136">See also</span></span>

- [<span data-ttu-id="6af74-137">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="6af74-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
