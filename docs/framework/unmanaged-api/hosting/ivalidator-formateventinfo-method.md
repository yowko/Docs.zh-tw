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
ms.openlocfilehash: 9b3a6bab8672f3ef3fca5f89c60b03a43477cce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123304"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="62fed-102">IValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="62fed-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="62fed-103">取得對應于指定驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="62fed-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62fed-104">語法</span><span class="sxs-lookup"><span data-stu-id="62fed-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62fed-105">參數</span><span class="sxs-lookup"><span data-stu-id="62fed-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="62fed-106">在已傳遞至驗證錯誤處理常式的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="62fed-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="62fed-107">在`VEContext` 實例，其中包含有關驗證錯誤的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="62fed-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="62fed-108">[in、out]包含傳回之錯誤訊息的字串。</span><span class="sxs-lookup"><span data-stu-id="62fed-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="62fed-109">在錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="62fed-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="62fed-110">在安全陣列，其中包含描述錯誤的其他參數。</span><span class="sxs-lookup"><span data-stu-id="62fed-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62fed-111">需求</span><span class="sxs-lookup"><span data-stu-id="62fed-111">Requirements</span></span>  
 <span data-ttu-id="62fed-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62fed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62fed-113">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="62fed-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="62fed-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="62fed-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62fed-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62fed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
