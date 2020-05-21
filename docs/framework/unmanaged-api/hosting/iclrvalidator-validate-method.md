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
ms.openlocfilehash: 18492f3e95947a3a11da9d5d303651c04d764a8f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762626"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="4d237-102">ICLRValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="4d237-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="4d237-103">驗證指定檔案中的可移植執行檔（PE）或 Microsoft 中繼語言（MSIL）。</span><span class="sxs-lookup"><span data-stu-id="4d237-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d237-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d237-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4d237-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d237-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="4d237-106">在`IVEHandler`處理驗證錯誤之實例的指標。</span><span class="sxs-lookup"><span data-stu-id="4d237-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="4d237-107">在目前的識別碼 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="4d237-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="4d237-108">在[ValidatorFlags](validatorflags-enumeration.md)值的組合，表示應該執行的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="4d237-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="4d237-109">在結束驗證之前允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="4d237-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="4d237-110">在未使用.</span><span class="sxs-lookup"><span data-stu-id="4d237-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="4d237-111">在要驗證的檔案名。</span><span class="sxs-lookup"><span data-stu-id="4d237-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="4d237-112">在檔案緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="4d237-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="4d237-113">在要驗證之檔案的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="4d237-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d237-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="4d237-114">Return Value</span></span>  
  
|<span data-ttu-id="4d237-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d237-115">HRESULT</span></span>|<span data-ttu-id="4d237-116">Description</span><span class="sxs-lookup"><span data-stu-id="4d237-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d237-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d237-117">S_OK</span></span>|<span data-ttu-id="4d237-118">`Validate`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4d237-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="4d237-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4d237-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4d237-120">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4d237-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4d237-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4d237-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4d237-122">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="4d237-122">The call timed out.</span></span>|  
|<span data-ttu-id="4d237-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4d237-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4d237-124">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4d237-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4d237-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4d237-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4d237-126">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="4d237-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4d237-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4d237-127">E_FAIL</span></span>|<span data-ttu-id="4d237-128">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4d237-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4d237-129">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="4d237-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4d237-130">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4d237-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d237-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="4d237-131">Requirements</span></span>  
 <span data-ttu-id="4d237-132">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d237-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d237-133">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="4d237-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="4d237-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4d237-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d237-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d237-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d237-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d237-136">See also</span></span>

- [<span data-ttu-id="4d237-137">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="4d237-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
