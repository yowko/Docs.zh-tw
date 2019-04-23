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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f17ecfe683de0739e4e1e063d38836eecf949336
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146990"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="a2bfc-102">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="a2bfc-102">LoadStringRC Function</span></span>
<span data-ttu-id="a2bfc-103">使用目前執行緒的預設文化特性，將 HRESULT 值轉譯成錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="a2bfc-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2bfc-105">語法</span><span class="sxs-lookup"><span data-stu-id="a2bfc-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2bfc-106">參數</span><span class="sxs-lookup"><span data-stu-id="a2bfc-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="a2bfc-107">[in]HRESULT。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="a2bfc-108">[out]這種緩衝區包含成功完成時的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="a2bfc-109">[in]錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="a2bfc-110">[in]略過。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2bfc-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2bfc-111">Return Value</span></span>  
 <span data-ttu-id="a2bfc-112">中所定義 WinError.h，除了下列的值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a2bfc-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="a2bfc-113">Return code</span></span>|<span data-ttu-id="a2bfc-114">描述</span><span class="sxs-lookup"><span data-stu-id="a2bfc-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a2bfc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2bfc-115">S_OK</span></span>|<span data-ttu-id="a2bfc-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a2bfc-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a2bfc-117">E_INVALIDARG</span></span>|<span data-ttu-id="a2bfc-118">`szBuffer` 為 null 或`iMax`為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2bfc-119">備註</span><span class="sxs-lookup"><span data-stu-id="a2bfc-119">Remarks</span></span>  
 <span data-ttu-id="a2bfc-120">如果方法未成功完成`szBuffer`包含空字串。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2bfc-121">需求</span><span class="sxs-lookup"><span data-stu-id="a2bfc-121">Requirements</span></span>  
 <span data-ttu-id="a2bfc-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2bfc-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2bfc-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2bfc-124">**LIBRARY:** MSCorEE.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="a2bfc-125">使用 MSCorEE.dll，而不是以確保您設為目標的.NET framework 的正確版本的 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a2bfc-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2bfc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2bfc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2bfc-127">See also</span></span>

- [<span data-ttu-id="a2bfc-128">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="a2bfc-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="a2bfc-129">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="a2bfc-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
