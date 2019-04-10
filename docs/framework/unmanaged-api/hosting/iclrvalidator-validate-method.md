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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 559c265c70c199e64782ba185d4925d293d6a778
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158687"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="745f4-102">ICLRValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="745f4-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="745f4-103">驗證的可攜式執行檔 (PE) 或 Microsoft intermediate language (MSIL)，在指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="745f4-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="745f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="745f4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="745f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="745f4-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="745f4-106">[in]指標`IVEHandler`處理驗證錯誤的執行個體。</span><span class="sxs-lookup"><span data-stu-id="745f4-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="745f4-107">[in]目前的識別項<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="745f4-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="745f4-108">[in]組合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，表示應該執行的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="745f4-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="745f4-109">[in]結束驗證之前允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="745f4-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="745f4-110">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="745f4-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="745f4-111">[in]要驗證之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="745f4-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="745f4-112">[in]檔案緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="745f4-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="745f4-113">[in]以位元組為單位，以驗證檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="745f4-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="745f4-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="745f4-114">Return Value</span></span>  
  
|<span data-ttu-id="745f4-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="745f4-115">HRESULT</span></span>|<span data-ttu-id="745f4-116">描述</span><span class="sxs-lookup"><span data-stu-id="745f4-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="745f4-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="745f4-117">S_OK</span></span>|`Validate` <span data-ttu-id="745f4-118">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="745f4-118">returned successfully.</span></span>|  
|<span data-ttu-id="745f4-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="745f4-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="745f4-120">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="745f4-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="745f4-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="745f4-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="745f4-122">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="745f4-122">The call timed out.</span></span>|  
|<span data-ttu-id="745f4-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="745f4-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="745f4-124">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="745f4-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="745f4-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="745f4-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="745f4-126">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="745f4-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="745f4-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="745f4-127">E_FAIL</span></span>|<span data-ttu-id="745f4-128">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="745f4-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="745f4-129">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="745f4-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="745f4-130">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="745f4-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="745f4-131">需求</span><span class="sxs-lookup"><span data-stu-id="745f4-131">Requirements</span></span>  
 <span data-ttu-id="745f4-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="745f4-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="745f4-133">**標頭：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="745f4-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="745f4-134">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="745f4-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="745f4-135">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="745f4-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="745f4-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="745f4-136">See also</span></span>

- [<span data-ttu-id="745f4-137">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="745f4-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
