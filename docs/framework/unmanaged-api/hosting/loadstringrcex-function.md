---
title: LoadStringRCEx 函式
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177988"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="2cf42-102">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="2cf42-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="2cf42-103">將 HRESULT 值轉換為指定區域性的相應錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2cf42-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="2cf42-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="2cf42-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf42-105">語法</span><span class="sxs-lookup"><span data-stu-id="2cf42-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cf42-106">參數</span><span class="sxs-lookup"><span data-stu-id="2cf42-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="2cf42-107">[在]區域性識別碼。</span><span class="sxs-lookup"><span data-stu-id="2cf42-107">[in] A culture identifier.</span></span> <span data-ttu-id="2cf42-108">通過 -1`lcid`用於使用預設區域性。</span><span class="sxs-lookup"><span data-stu-id="2cf42-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="2cf42-109">[在]A HRESULT。</span><span class="sxs-lookup"><span data-stu-id="2cf42-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2cf42-110">[出]成功完成後包含錯誤訊息的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2cf42-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="2cf42-111">[在]錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="2cf42-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="2cf42-112">[在]忽視。</span><span class="sxs-lookup"><span data-stu-id="2cf42-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="2cf42-113">[出]指向錯誤訊息長度的指標。</span><span class="sxs-lookup"><span data-stu-id="2cf42-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cf42-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="2cf42-114">Return Value</span></span>  
 <span data-ttu-id="2cf42-115">此方法返回 WinError.h 中定義的標準 COM 錯誤代碼，以及以下值。</span><span class="sxs-lookup"><span data-stu-id="2cf42-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="2cf42-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="2cf42-116">Return code</span></span>|<span data-ttu-id="2cf42-117">描述</span><span class="sxs-lookup"><span data-stu-id="2cf42-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2cf42-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cf42-118">S_OK</span></span>|<span data-ttu-id="2cf42-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="2cf42-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="2cf42-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2cf42-120">E_INVALIDARG</span></span>|<span data-ttu-id="2cf42-121">`szBuffer`為空或`iMax`為零 （0）。</span><span class="sxs-lookup"><span data-stu-id="2cf42-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cf42-122">備註</span><span class="sxs-lookup"><span data-stu-id="2cf42-122">Remarks</span></span>  
 <span data-ttu-id="2cf42-123">如果方法未成功完成，`szBuffer`則包含一個空字串。</span><span class="sxs-lookup"><span data-stu-id="2cf42-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf42-124">需求</span><span class="sxs-lookup"><span data-stu-id="2cf42-124">Requirements</span></span>  
 <span data-ttu-id="2cf42-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cf42-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf42-126">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cf42-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cf42-127">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cf42-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cf42-128">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf42-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf42-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cf42-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2cf42-130">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="2cf42-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="2cf42-131">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2cf42-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
