---
title: LoadStringRC 函式
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176236"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="47eac-102">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="47eac-102">LoadStringRC Function</span></span>
<span data-ttu-id="47eac-103">使用當前執行緒的預設區域性將 HRESULT 值轉換為錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="47eac-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="47eac-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="47eac-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47eac-105">語法</span><span class="sxs-lookup"><span data-stu-id="47eac-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47eac-106">參數</span><span class="sxs-lookup"><span data-stu-id="47eac-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="47eac-107">[在]A HRESULT。</span><span class="sxs-lookup"><span data-stu-id="47eac-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="47eac-108">[出]成功完成後包含錯誤訊息的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="47eac-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="47eac-109">[在]錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="47eac-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="47eac-110">[在]忽視。</span><span class="sxs-lookup"><span data-stu-id="47eac-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47eac-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="47eac-111">Return Value</span></span>  
 <span data-ttu-id="47eac-112">此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及以下值。</span><span class="sxs-lookup"><span data-stu-id="47eac-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="47eac-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="47eac-113">Return code</span></span>|<span data-ttu-id="47eac-114">描述</span><span class="sxs-lookup"><span data-stu-id="47eac-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="47eac-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="47eac-115">S_OK</span></span>|<span data-ttu-id="47eac-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="47eac-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="47eac-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="47eac-117">E_INVALIDARG</span></span>|<span data-ttu-id="47eac-118">`szBuffer`為空或`iMax`為零 （0）。</span><span class="sxs-lookup"><span data-stu-id="47eac-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47eac-119">備註</span><span class="sxs-lookup"><span data-stu-id="47eac-119">Remarks</span></span>  
 <span data-ttu-id="47eac-120">如果方法未成功完成，`szBuffer`則包含一個空字串。</span><span class="sxs-lookup"><span data-stu-id="47eac-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47eac-121">需求</span><span class="sxs-lookup"><span data-stu-id="47eac-121">Requirements</span></span>  
 <span data-ttu-id="47eac-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47eac-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47eac-123">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47eac-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47eac-124">**庫：** MSCorE.dll 和 Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="47eac-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="47eac-125">使用 MSCorEE.dll 而不是 mscorwks.dll 來確保針對 .NET 框架的正確版本。</span><span class="sxs-lookup"><span data-stu-id="47eac-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="47eac-126">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47eac-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47eac-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47eac-127">See also</span></span>

- [<span data-ttu-id="47eac-128">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="47eac-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="47eac-129">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="47eac-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
