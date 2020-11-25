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
ms.openlocfilehash: 16f95f8fce20f2cf46d4cda214e4494bd288bf60
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727545"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="308b2-102">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="308b2-102">LoadStringRC Function</span></span>

<span data-ttu-id="308b2-103">使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="308b2-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="308b2-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="308b2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="308b2-105">語法</span><span class="sxs-lookup"><span data-stu-id="308b2-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="308b2-106">參數</span><span class="sxs-lookup"><span data-stu-id="308b2-106">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="308b2-107">在HRESULT。</span><span class="sxs-lookup"><span data-stu-id="308b2-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="308b2-108">擴展在成功完成時包含錯誤訊息的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="308b2-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="308b2-109">在錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="308b2-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="308b2-110">在忽視。</span><span class="sxs-lookup"><span data-stu-id="308b2-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="308b2-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="308b2-111">Return Value</span></span>  

 <span data-ttu-id="308b2-112">除了下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。</span><span class="sxs-lookup"><span data-stu-id="308b2-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="308b2-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="308b2-113">Return code</span></span>|<span data-ttu-id="308b2-114">描述</span><span class="sxs-lookup"><span data-stu-id="308b2-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="308b2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="308b2-115">S_OK</span></span>|<span data-ttu-id="308b2-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="308b2-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="308b2-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="308b2-117">E_INVALIDARG</span></span>|<span data-ttu-id="308b2-118">`szBuffer` 為 null 或 `iMax` 為零 (0) 。</span><span class="sxs-lookup"><span data-stu-id="308b2-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="308b2-119">備註</span><span class="sxs-lookup"><span data-stu-id="308b2-119">Remarks</span></span>  

 <span data-ttu-id="308b2-120">如果方法未順利完成，就會 `szBuffer` 包含空字串。</span><span class="sxs-lookup"><span data-stu-id="308b2-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="308b2-121">需求</span><span class="sxs-lookup"><span data-stu-id="308b2-121">Requirements</span></span>  

 <span data-ttu-id="308b2-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="308b2-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="308b2-123">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="308b2-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="308b2-124">連結 **庫：** MSCorEE.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="308b2-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="308b2-125">使用 MSCorEE.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="308b2-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="308b2-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="308b2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308b2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="308b2-127">See also</span></span>

- [<span data-ttu-id="308b2-128">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="308b2-128">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)
- [<span data-ttu-id="308b2-129">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="308b2-129">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
