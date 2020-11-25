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
ms.openlocfilehash: c5c89e0eda6e93e34775c00d5ec8fb4ff0940707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701012"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="971d8-102">IValidator::FormatEventInfo 方法</span><span class="sxs-lookup"><span data-stu-id="971d8-102">IValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="971d8-103">取得對應到指定之驗證錯誤的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="971d8-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="971d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="971d8-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="971d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="971d8-105">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="971d8-106">在傳遞給驗證錯誤處理常式的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="971d8-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="971d8-107">在 `VEContext` 實例，其中包含有關驗證錯誤的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="971d8-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="971d8-108">[in，out]包含傳回之錯誤訊息的字串。</span><span class="sxs-lookup"><span data-stu-id="971d8-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="971d8-109">在錯誤訊息的最大長度。</span><span class="sxs-lookup"><span data-stu-id="971d8-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="971d8-110">在安全陣列，包含描述錯誤的其他參數。</span><span class="sxs-lookup"><span data-stu-id="971d8-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="971d8-111">需求</span><span class="sxs-lookup"><span data-stu-id="971d8-111">Requirements</span></span>  

 <span data-ttu-id="971d8-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="971d8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="971d8-113">**標頭：** IValidator .idl、IValidator。h</span><span class="sxs-lookup"><span data-stu-id="971d8-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="971d8-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="971d8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="971d8-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="971d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
