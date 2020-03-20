---
title: _CorValidateImage 函式
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178221"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="f1484-102">_CorValidateImage 函式</span><span class="sxs-lookup"><span data-stu-id="f1484-102">_CorValidateImage Function</span></span>
<span data-ttu-id="f1484-103">驗證託管模組映射，並在載入作業系統載入器後通知它們。</span><span class="sxs-lookup"><span data-stu-id="f1484-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1484-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1484-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1484-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1484-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="f1484-106">[在]指向映射的起始位置的指標，以驗證為託管代碼。</span><span class="sxs-lookup"><span data-stu-id="f1484-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="f1484-107">圖像必須已載入到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="f1484-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="f1484-108">[在]圖像的檔案名。</span><span class="sxs-lookup"><span data-stu-id="f1484-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1484-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1484-109">Return Value</span></span>  
 <span data-ttu-id="f1484-110">此函數返回標準`E_INVALIDARG`值`E_OUTOFMEMORY`、和`E_UNEXPECTED` `E_FAIL`，以及以下值。</span><span class="sxs-lookup"><span data-stu-id="f1484-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="f1484-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1484-111">Return value</span></span>|<span data-ttu-id="f1484-112">描述</span><span class="sxs-lookup"><span data-stu-id="f1484-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="f1484-113">圖像無效。</span><span class="sxs-lookup"><span data-stu-id="f1484-113">The image is invalid.</span></span> <span data-ttu-id="f1484-114">此值具有 HRESULT 0xC000007BL。</span><span class="sxs-lookup"><span data-stu-id="f1484-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="f1484-115">圖像有效。</span><span class="sxs-lookup"><span data-stu-id="f1484-115">The image is valid.</span></span> <span data-ttu-id="f1484-116">此值具有 HRESULT 0x0000000L。</span><span class="sxs-lookup"><span data-stu-id="f1484-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1484-117">備註</span><span class="sxs-lookup"><span data-stu-id="f1484-117">Remarks</span></span>  
 <span data-ttu-id="f1484-118">在 Windows XP 和更高版本中，作業系統載入程式通過檢查公共物件檔案格式 （COFF） 標頭中的 COM 描述項目錄位來檢查託管模組。</span><span class="sxs-lookup"><span data-stu-id="f1484-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="f1484-119">設置位表示託管模組。</span><span class="sxs-lookup"><span data-stu-id="f1484-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="f1484-120">如果載入程式檢測到託管模組，它將載入 MsCorEE.dll 和調用`_CorValidateImage`，這將執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f1484-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="f1484-121">確認映射是有效的託管模組。</span><span class="sxs-lookup"><span data-stu-id="f1484-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="f1484-122">將圖像中的進入點更改為通用語言運行時 （CLR） 中的進入點。</span><span class="sxs-lookup"><span data-stu-id="f1484-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="f1484-123">對於 64 位版本的 Windows，通過將映射從 PE32 轉換為 PE32+ 格式來修改記憶體中的圖像。</span><span class="sxs-lookup"><span data-stu-id="f1484-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="f1484-124">載入託管模組映射時返回載入程式。</span><span class="sxs-lookup"><span data-stu-id="f1484-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="f1484-125">對於可執行映射，作業系統載入程式然後調用[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函數，而不考慮可執行檔中指定的進入點。</span><span class="sxs-lookup"><span data-stu-id="f1484-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="f1484-126">對於 DLL 裝配體映射，載入程式調用[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f1484-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="f1484-127">`_CorExeMain`或`_CorDllMain`執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f1484-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="f1484-128">初始化 CLR。</span><span class="sxs-lookup"><span data-stu-id="f1484-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="f1484-129">從程式集的 CLR 標頭中查找託管進入點。</span><span class="sxs-lookup"><span data-stu-id="f1484-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="f1484-130">開始執行。</span><span class="sxs-lookup"><span data-stu-id="f1484-130">Begins execution.</span></span>  
  
 <span data-ttu-id="f1484-131">卸載託管模組映射時，載入程式調用[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f1484-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="f1484-132">但是，此函數不執行任何操作;因此，此操作不會執行任何操作。它只是返回。</span><span class="sxs-lookup"><span data-stu-id="f1484-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1484-133">需求</span><span class="sxs-lookup"><span data-stu-id="f1484-133">Requirements</span></span>  
 <span data-ttu-id="f1484-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1484-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1484-135">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="f1484-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1484-136">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f1484-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1484-137">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1484-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1484-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1484-138">See also</span></span>

- [<span data-ttu-id="f1484-139">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="f1484-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
