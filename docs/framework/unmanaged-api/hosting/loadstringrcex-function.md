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
ms.openlocfilehash: 1aa5c9f5dd7dd63e69c2eed1f6dd8ad6f007f01f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727532"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="1ea5e-102">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="1ea5e-102">LoadStringRCEx Function</span></span>

<span data-ttu-id="1ea5e-103">針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="1ea5e-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea5e-105">語法</span><span class="sxs-lookup"><span data-stu-id="1ea5e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1ea5e-106">參數</span><span class="sxs-lookup"><span data-stu-id="1ea5e-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="1ea5e-107">在文化特性識別碼。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-107">[in] A culture identifier.</span></span> <span data-ttu-id="1ea5e-108">的傳遞-1 會 `lcid` 使用預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="1ea5e-109">在HRESULT。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="1ea5e-110">擴展在成功完成時包含錯誤訊息的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="1ea5e-111">在錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="1ea5e-112">在忽視。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="1ea5e-113">擴展錯誤訊息長度的指標。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ea5e-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ea5e-114">Return Value</span></span>  

 <span data-ttu-id="1ea5e-115">除了下列值以外，這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="1ea5e-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="1ea5e-116">Return code</span></span>|<span data-ttu-id="1ea5e-117">描述</span><span class="sxs-lookup"><span data-stu-id="1ea5e-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1ea5e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ea5e-118">S_OK</span></span>|<span data-ttu-id="1ea5e-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="1ea5e-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1ea5e-120">E_INVALIDARG</span></span>|<span data-ttu-id="1ea5e-121">`szBuffer` 為 null，或 `iMax` 為零 (0) 。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ea5e-122">備註</span><span class="sxs-lookup"><span data-stu-id="1ea5e-122">Remarks</span></span>  

 <span data-ttu-id="1ea5e-123">如果方法未順利完成，就會 `szBuffer` 包含空字串。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea5e-124">需求</span><span class="sxs-lookup"><span data-stu-id="1ea5e-124">Requirements</span></span>  

 <span data-ttu-id="1ea5e-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea5e-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea5e-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1ea5e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ea5e-127">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ea5e-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ea5e-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea5e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea5e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea5e-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1ea5e-130">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="1ea5e-130">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="1ea5e-131">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="1ea5e-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
