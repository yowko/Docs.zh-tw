---
title: IValidator::FormatEventInfo 方法
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 875052ed26e83de50807e33e9c74dcf89f7ee679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440641"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="5d56d-102">IValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="5d56d-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="5d56d-103">取得對應至指定的驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5d56d-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d56d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d56d-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d56d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d56d-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="5d56d-106">[in]HRESULT 值傳遞給驗證的錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="5d56d-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="5d56d-107">[in]A`VEContext`執行個體，其中包含驗證錯誤的相關內容資訊。</span><span class="sxs-lookup"><span data-stu-id="5d56d-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="5d56d-108">[in、 out]字串，包含傳回的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5d56d-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="5d56d-109">[in]錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="5d56d-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="5d56d-110">[in]安全陣列，其中包含描述錯誤的其他參數。</span><span class="sxs-lookup"><span data-stu-id="5d56d-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d56d-111">需求</span><span class="sxs-lookup"><span data-stu-id="5d56d-111">Requirements</span></span>  
 <span data-ttu-id="5d56d-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d56d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d56d-113">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="5d56d-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="5d56d-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5d56d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d56d-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d56d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d56d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d56d-116">See Also</span></span>  
 
