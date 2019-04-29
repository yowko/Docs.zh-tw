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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 697557463aa949036acb21e63b9a82b1fb84b415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765280"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="3f106-102">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="3f106-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="3f106-103">將 HRESULT 值轉譯成適當的錯誤訊息指定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="3f106-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="3f106-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f106-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f106-105">語法</span><span class="sxs-lookup"><span data-stu-id="3f106-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f106-106">參數</span><span class="sxs-lookup"><span data-stu-id="3f106-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="3f106-107">[in]文化特性識別項。</span><span class="sxs-lookup"><span data-stu-id="3f106-107">[in] A culture identifier.</span></span> <span data-ttu-id="3f106-108">傳遞 – 1`lcid`若要使用的預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="3f106-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="3f106-109">[in]HRESULT。</span><span class="sxs-lookup"><span data-stu-id="3f106-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="3f106-110">[out]這種緩衝區包含成功完成時的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3f106-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="3f106-111">[in]錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="3f106-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="3f106-112">[in]略過。</span><span class="sxs-lookup"><span data-stu-id="3f106-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="3f106-113">[out]錯誤訊息的長度指標。</span><span class="sxs-lookup"><span data-stu-id="3f106-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f106-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="3f106-114">Return Value</span></span>  
 <span data-ttu-id="3f106-115">中所定義 WinError.h，除了下列的值，這個方法會傳回標準的 COM 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="3f106-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="3f106-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="3f106-116">Return code</span></span>|<span data-ttu-id="3f106-117">描述</span><span class="sxs-lookup"><span data-stu-id="3f106-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3f106-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f106-118">S_OK</span></span>|<span data-ttu-id="3f106-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="3f106-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="3f106-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3f106-120">E_INVALIDARG</span></span>|<span data-ttu-id="3f106-121">`szBuffer` 為 null，或`iMax`為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="3f106-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f106-122">備註</span><span class="sxs-lookup"><span data-stu-id="3f106-122">Remarks</span></span>  
 <span data-ttu-id="3f106-123">如果方法未成功完成`szBuffer`包含空字串。</span><span class="sxs-lookup"><span data-stu-id="3f106-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f106-124">需求</span><span class="sxs-lookup"><span data-stu-id="3f106-124">Requirements</span></span>  
 <span data-ttu-id="3f106-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f106-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f106-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f106-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f106-127">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f106-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f106-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f106-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f106-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f106-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3f106-130">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="3f106-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="3f106-131">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="3f106-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
