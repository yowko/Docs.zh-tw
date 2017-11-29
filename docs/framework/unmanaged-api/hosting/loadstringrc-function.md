---
title: "LoadStringRC 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc93adf575af7f2803b20f24a3261a447772ffd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrc-function"></a><span data-ttu-id="224b2-102">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="224b2-102">LoadStringRC Function</span></span>
<span data-ttu-id="224b2-103">使用目前執行緒的預設文化特性，將 HRESULT 值轉譯成錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="224b2-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="224b2-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="224b2-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="224b2-105">語法</span><span class="sxs-lookup"><span data-stu-id="224b2-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="224b2-106">參數</span><span class="sxs-lookup"><span data-stu-id="224b2-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="224b2-107">[in]HRESULT。</span><span class="sxs-lookup"><span data-stu-id="224b2-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="224b2-108">[out]包含成功完成時的錯誤訊息的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="224b2-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="224b2-109">[in]錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="224b2-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="224b2-110">[in]略過。</span><span class="sxs-lookup"><span data-stu-id="224b2-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="224b2-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="224b2-111">Return Value</span></span>  
 <span data-ttu-id="224b2-112">這個方法會傳回標準的元件物件模型 (COM) 的錯誤代碼，除了下列的值定義了 WinError.h 中。</span><span class="sxs-lookup"><span data-stu-id="224b2-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="224b2-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="224b2-113">Return code</span></span>|<span data-ttu-id="224b2-114">描述</span><span class="sxs-lookup"><span data-stu-id="224b2-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="224b2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="224b2-115">S_OK</span></span>|<span data-ttu-id="224b2-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="224b2-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="224b2-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="224b2-117">E_INVALIDARG</span></span>|<span data-ttu-id="224b2-118">`szBuffer`為 null 或`iMax`為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="224b2-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="224b2-119">備註</span><span class="sxs-lookup"><span data-stu-id="224b2-119">Remarks</span></span>  
 <span data-ttu-id="224b2-120">如果方法沒有成功完成`szBuffer`包含空字串。</span><span class="sxs-lookup"><span data-stu-id="224b2-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="224b2-121">需求</span><span class="sxs-lookup"><span data-stu-id="224b2-121">Requirements</span></span>  
 <span data-ttu-id="224b2-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="224b2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="224b2-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="224b2-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="224b2-124">**程式庫：** MSCorEE.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="224b2-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="224b2-125">使用而不是 Mscorwks.dll 的 MSCorEE.dll，以確保您設為目標的.NET framework 正確版本。</span><span class="sxs-lookup"><span data-stu-id="224b2-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="224b2-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="224b2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="224b2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="224b2-127">See Also</span></span>  
 [<span data-ttu-id="224b2-128">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="224b2-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [<span data-ttu-id="224b2-129">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="224b2-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
