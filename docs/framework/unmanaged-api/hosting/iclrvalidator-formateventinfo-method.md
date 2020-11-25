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
ms.openlocfilehash: a3f52deab4d0c8ca56fae2e65912217e51abe58a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715858"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="78840-102">ICLRValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="78840-102">ICLRValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="78840-103">取得有關指定之驗證錯誤的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="78840-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78840-104">語法</span><span class="sxs-lookup"><span data-stu-id="78840-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78840-105">參數</span><span class="sxs-lookup"><span data-stu-id="78840-105">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="78840-106">在傳遞給驗證錯誤處理常式的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="78840-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="78840-107">在 `VEContext` 實例，其中包含有關驗證錯誤的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="78840-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="78840-108">[in，out]易記的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="78840-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="78840-109">在錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="78840-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="78840-110">在要在訊息中使用之其他參數的安全陣列。</span><span class="sxs-lookup"><span data-stu-id="78840-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78840-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="78840-111">Return Value</span></span>  
  
|<span data-ttu-id="78840-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78840-112">HRESULT</span></span>|<span data-ttu-id="78840-113">描述</span><span class="sxs-lookup"><span data-stu-id="78840-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78840-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="78840-114">S_OK</span></span>|<span data-ttu-id="78840-115">`FormatEventInfo` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="78840-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="78840-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78840-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78840-117">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="78840-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78840-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78840-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78840-119">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="78840-119">The call timed out.</span></span>|  
|<span data-ttu-id="78840-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78840-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78840-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="78840-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78840-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78840-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78840-123">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="78840-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78840-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78840-124">E_FAIL</span></span>|<span data-ttu-id="78840-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="78840-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78840-126">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="78840-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78840-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="78840-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78840-128">需求</span><span class="sxs-lookup"><span data-stu-id="78840-128">Requirements</span></span>  

 <span data-ttu-id="78840-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78840-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78840-130">**標頭：** IValidator .idl、IValidator。h</span><span class="sxs-lookup"><span data-stu-id="78840-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="78840-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="78840-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78840-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78840-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78840-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78840-133">See also</span></span>

- [<span data-ttu-id="78840-134">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="78840-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="78840-135">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="78840-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
