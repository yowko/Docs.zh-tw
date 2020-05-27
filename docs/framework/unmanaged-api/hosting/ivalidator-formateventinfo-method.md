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
ms.openlocfilehash: 0c60631b5e034bc46d74412440d35d526359d043
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008569"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="64d0a-102">IValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="64d0a-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="64d0a-103">取得對應于指定驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="64d0a-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="64d0a-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="64d0a-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="64d0a-106">在已傳遞至驗證錯誤處理常式的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="64d0a-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="64d0a-107">在`VEContext`實例，其中包含有關驗證錯誤的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="64d0a-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="64d0a-108">[in、out]包含傳回之錯誤訊息的字串。</span><span class="sxs-lookup"><span data-stu-id="64d0a-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="64d0a-109">在錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="64d0a-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="64d0a-110">在安全陣列，其中包含描述錯誤的其他參數。</span><span class="sxs-lookup"><span data-stu-id="64d0a-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d0a-111">需求</span><span class="sxs-lookup"><span data-stu-id="64d0a-111">Requirements</span></span>  
 <span data-ttu-id="64d0a-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64d0a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d0a-113">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="64d0a-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="64d0a-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="64d0a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64d0a-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d0a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
