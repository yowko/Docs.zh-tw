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
ms.openlocfilehash: 4ce50f7706583f291d2e6a141d40ab6dd3e4b3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674381"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="81fbb-102">ICLRValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="81fbb-102">ICLRValidator::Validate Method</span></span>

<span data-ttu-id="81fbb-103">在指定的檔案中驗證可攜式可執行檔 (PE) 或 Microsoft 中繼語言 (MSIL) 。</span><span class="sxs-lookup"><span data-stu-id="81fbb-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81fbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="81fbb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="81fbb-105">參數</span><span class="sxs-lookup"><span data-stu-id="81fbb-105">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="81fbb-106">在 `IVEHandler` 處理驗證錯誤之實例的指標。</span><span class="sxs-lookup"><span data-stu-id="81fbb-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="81fbb-107">在目前的識別碼 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="81fbb-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="81fbb-108">在 [ValidatorFlags](validatorflags-enumeration.md) 值的組合，表示應該執行的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="81fbb-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="81fbb-109">在結束驗證之前允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="81fbb-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="81fbb-110">在閒置。</span><span class="sxs-lookup"><span data-stu-id="81fbb-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="81fbb-111">在要驗證之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="81fbb-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="81fbb-112">在檔案緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="81fbb-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="81fbb-113">在要驗證之檔案的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="81fbb-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81fbb-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="81fbb-114">Return Value</span></span>  
  
|<span data-ttu-id="81fbb-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81fbb-115">HRESULT</span></span>|<span data-ttu-id="81fbb-116">描述</span><span class="sxs-lookup"><span data-stu-id="81fbb-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81fbb-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="81fbb-117">S_OK</span></span>|<span data-ttu-id="81fbb-118">`Validate` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="81fbb-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="81fbb-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81fbb-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81fbb-120">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="81fbb-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81fbb-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81fbb-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81fbb-122">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="81fbb-122">The call timed out.</span></span>|  
|<span data-ttu-id="81fbb-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81fbb-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81fbb-124">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="81fbb-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81fbb-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81fbb-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81fbb-126">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="81fbb-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81fbb-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81fbb-127">E_FAIL</span></span>|<span data-ttu-id="81fbb-128">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="81fbb-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81fbb-129">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="81fbb-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81fbb-130">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="81fbb-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81fbb-131">需求</span><span class="sxs-lookup"><span data-stu-id="81fbb-131">Requirements</span></span>  

 <span data-ttu-id="81fbb-132">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81fbb-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81fbb-133">**標頭：** IValidator .idl、IValidator。h</span><span class="sxs-lookup"><span data-stu-id="81fbb-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="81fbb-134">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="81fbb-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81fbb-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81fbb-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fbb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81fbb-136">See also</span></span>

- [<span data-ttu-id="81fbb-137">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="81fbb-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
