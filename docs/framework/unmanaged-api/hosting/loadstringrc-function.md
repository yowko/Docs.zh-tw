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
ms.openlocfilehash: 66d4c14234c7929af443922f86098b46a4aa6eb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122010"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="31fec-102">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="31fec-102">LoadStringRC Function</span></span>
<span data-ttu-id="31fec-103">使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="31fec-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="31fec-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="31fec-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fec-105">語法</span><span class="sxs-lookup"><span data-stu-id="31fec-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31fec-106">參數</span><span class="sxs-lookup"><span data-stu-id="31fec-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="31fec-107">在HRESULT。</span><span class="sxs-lookup"><span data-stu-id="31fec-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="31fec-108">脫銷一個緩衝區，其中包含成功完成時的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="31fec-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="31fec-109">在錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="31fec-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="31fec-110">在忽略.</span><span class="sxs-lookup"><span data-stu-id="31fec-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31fec-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="31fec-111">Return Value</span></span>  
 <span data-ttu-id="31fec-112">這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。</span><span class="sxs-lookup"><span data-stu-id="31fec-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="31fec-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="31fec-113">Return code</span></span>|<span data-ttu-id="31fec-114">描述</span><span class="sxs-lookup"><span data-stu-id="31fec-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="31fec-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="31fec-115">S_OK</span></span>|<span data-ttu-id="31fec-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="31fec-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="31fec-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="31fec-117">E_INVALIDARG</span></span>|<span data-ttu-id="31fec-118">`szBuffer` 為 null 或 `iMax` 為零（0）。</span><span class="sxs-lookup"><span data-stu-id="31fec-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31fec-119">備註</span><span class="sxs-lookup"><span data-stu-id="31fec-119">Remarks</span></span>  
 <span data-ttu-id="31fec-120">如果方法未順利完成，`szBuffer` 會包含空字串。</span><span class="sxs-lookup"><span data-stu-id="31fec-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31fec-121">需求</span><span class="sxs-lookup"><span data-stu-id="31fec-121">Requirements</span></span>  
 <span data-ttu-id="31fec-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31fec-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31fec-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="31fec-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31fec-124">連結**庫：** Mscoree.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="31fec-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="31fec-125">請使用 Mscoree.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="31fec-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="31fec-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31fec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fec-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="31fec-127">See also</span></span>

- [<span data-ttu-id="31fec-128">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="31fec-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="31fec-129">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="31fec-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
