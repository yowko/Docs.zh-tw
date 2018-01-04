---
title: "ICLRValidator::Validate 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7328fe62276de6c33464ab8cfc6d6a5f39ee710e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="8a29c-102">ICLRValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="8a29c-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="8a29c-103">驗證的可攜式執行檔 (PE) 或 Microsoft 中繼語言 (MSIL)，在指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="8a29c-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a29c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a29c-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="8a29c-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a29c-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="8a29c-106">[in]指標`IVEHandler`處理驗證錯誤的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8a29c-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="8a29c-107">[in]目前的識別項<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="8a29c-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="8a29c-108">[in]組合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，表示應該執行的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8a29c-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="8a29c-109">[in]結束驗證前，允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="8a29c-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="8a29c-110">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="8a29c-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="8a29c-111">[in]要驗證檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="8a29c-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="8a29c-112">[in]檔案緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="8a29c-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="8a29c-113">[in]以位元組為單位來驗證檔案大小。</span><span class="sxs-lookup"><span data-stu-id="8a29c-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a29c-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a29c-114">Return Value</span></span>  
  
|<span data-ttu-id="8a29c-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a29c-115">HRESULT</span></span>|<span data-ttu-id="8a29c-116">描述</span><span class="sxs-lookup"><span data-stu-id="8a29c-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a29c-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a29c-117">S_OK</span></span>|<span data-ttu-id="8a29c-118">`Validate`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8a29c-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="8a29c-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8a29c-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8a29c-120">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8a29c-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8a29c-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8a29c-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8a29c-122">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="8a29c-122">The call timed out.</span></span>|  
|<span data-ttu-id="8a29c-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a29c-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8a29c-124">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8a29c-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8a29c-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8a29c-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8a29c-126">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="8a29c-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8a29c-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a29c-127">E_FAIL</span></span>|<span data-ttu-id="8a29c-128">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8a29c-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8a29c-129">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="8a29c-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8a29c-130">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8a29c-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a29c-131">需求</span><span class="sxs-lookup"><span data-stu-id="8a29c-131">Requirements</span></span>  
 <span data-ttu-id="8a29c-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a29c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a29c-133">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="8a29c-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="8a29c-134">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8a29c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a29c-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a29c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a29c-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a29c-136">See Also</span></span>  
 [<span data-ttu-id="8a29c-137">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="8a29c-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
