---
title: "LoadStringRCEx 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRCEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRCEx
helpviewer_keywords: LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3467ebcd0b821c2313f3535c5b594ef664546e4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="8e864-102">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="8e864-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="8e864-103">HRESULT 值轉譯成適當的錯誤訊息指定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="8e864-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="8e864-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8e864-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e864-105">語法</span><span class="sxs-lookup"><span data-stu-id="8e864-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="8e864-106">參數</span><span class="sxs-lookup"><span data-stu-id="8e864-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="8e864-107">[in]文化特性識別項。</span><span class="sxs-lookup"><span data-stu-id="8e864-107">[in] A culture identifier.</span></span> <span data-ttu-id="8e864-108">傳遞 – 1`lcid`来使用的預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="8e864-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="8e864-109">[in]HRESULT。</span><span class="sxs-lookup"><span data-stu-id="8e864-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="8e864-110">[out]包含成功完成時的錯誤訊息的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8e864-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="8e864-111">[in]錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="8e864-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="8e864-112">[in]略過。</span><span class="sxs-lookup"><span data-stu-id="8e864-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="8e864-113">[out]錯誤訊息的長度指標。</span><span class="sxs-lookup"><span data-stu-id="8e864-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e864-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e864-114">Return Value</span></span>  
 <span data-ttu-id="8e864-115">這個方法會傳回標準的 COM 錯誤代碼，除了下列的值定義了 WinError.h 中。</span><span class="sxs-lookup"><span data-stu-id="8e864-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="8e864-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="8e864-116">Return code</span></span>|<span data-ttu-id="8e864-117">描述</span><span class="sxs-lookup"><span data-stu-id="8e864-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8e864-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e864-118">S_OK</span></span>|<span data-ttu-id="8e864-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="8e864-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="8e864-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8e864-120">E_INVALIDARG</span></span>|<span data-ttu-id="8e864-121">`szBuffer`為 null，或`iMax`為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="8e864-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e864-122">備註</span><span class="sxs-lookup"><span data-stu-id="8e864-122">Remarks</span></span>  
 <span data-ttu-id="8e864-123">如果方法沒有成功完成`szBuffer`包含空字串。</span><span class="sxs-lookup"><span data-stu-id="8e864-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e864-124">需求</span><span class="sxs-lookup"><span data-stu-id="8e864-124">Requirements</span></span>  
 <span data-ttu-id="8e864-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e864-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e864-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8e864-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e864-127">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e864-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e864-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e864-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e864-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e864-129">See Also</span></span>  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8e864-130">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="8e864-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [<span data-ttu-id="8e864-131">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="8e864-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
