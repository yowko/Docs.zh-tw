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
ms.openlocfilehash: 42da5bb761ba8ce388bd41d46e8fdc4561ad0290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136876"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="bc242-102">_CorValidateImage 函式</span><span class="sxs-lookup"><span data-stu-id="bc242-102">_CorValidateImage Function</span></span>
<span data-ttu-id="bc242-103">驗證受管理的模組映射，並在載入作業系統載入器之後通知它。</span><span class="sxs-lookup"><span data-stu-id="bc242-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc242-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc242-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc242-105">參數</span><span class="sxs-lookup"><span data-stu-id="bc242-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="bc242-106">在要驗證為 managed 程式碼之影像起始位置的指標。</span><span class="sxs-lookup"><span data-stu-id="bc242-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="bc242-107">映射必須已經載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="bc242-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="bc242-108">在影像的檔案名。</span><span class="sxs-lookup"><span data-stu-id="bc242-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc242-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc242-109">Return Value</span></span>  
 <span data-ttu-id="bc242-110">此函數會傳回標準值 `E_INVALIDARG`、`E_OUTOFMEMORY`、`E_UNEXPECTED`和 `E_FAIL`，以及下列值。</span><span class="sxs-lookup"><span data-stu-id="bc242-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="bc242-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc242-111">Return value</span></span>|<span data-ttu-id="bc242-112">描述</span><span class="sxs-lookup"><span data-stu-id="bc242-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="bc242-113">映射無效。</span><span class="sxs-lookup"><span data-stu-id="bc242-113">The image is invalid.</span></span> <span data-ttu-id="bc242-114">此值具有 HRESULT 0xC000007BL。</span><span class="sxs-lookup"><span data-stu-id="bc242-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="bc242-115">此映射有效。</span><span class="sxs-lookup"><span data-stu-id="bc242-115">The image is valid.</span></span> <span data-ttu-id="bc242-116">此值具有 HRESULT 0x00000000L。</span><span class="sxs-lookup"><span data-stu-id="bc242-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc242-117">備註</span><span class="sxs-lookup"><span data-stu-id="bc242-117">Remarks</span></span>  
 <span data-ttu-id="bc242-118">在 Windows XP 和更新版本中，作業系統載入器會藉由檢查通用物件檔案格式（COFF）標頭中的 COM 描述專案錄位來檢查受控模組。</span><span class="sxs-lookup"><span data-stu-id="bc242-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="bc242-119">設定的位表示受控模組。</span><span class="sxs-lookup"><span data-stu-id="bc242-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="bc242-120">如果載入器偵測到受管理的模組，它會載入 Mscoree.dll，並呼叫 `_CorValidateImage`，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bc242-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="bc242-121">確認映射是有效的受控模組。</span><span class="sxs-lookup"><span data-stu-id="bc242-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="bc242-122">將影像中的進入點變更為 common language runtime （CLR）中的進入點。</span><span class="sxs-lookup"><span data-stu-id="bc242-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="bc242-123">若是64位版本的 Windows，請將記憶體中的影像從 PE32 轉換為 PE32 + 格式，以修改該映射。</span><span class="sxs-lookup"><span data-stu-id="bc242-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="bc242-124">載入 managed 模組映射時，返回載入器。</span><span class="sxs-lookup"><span data-stu-id="bc242-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="bc242-125">對於可執行映射，作業系統載入器會接著呼叫[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式，而不論可執行檔中所指定的進入點為何。</span><span class="sxs-lookup"><span data-stu-id="bc242-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="bc242-126">對於 DLL 元件影像，載入器會呼叫[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="bc242-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="bc242-127">`_CorExeMain` 或 `_CorDllMain` 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bc242-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="bc242-128">初始化 CLR。</span><span class="sxs-lookup"><span data-stu-id="bc242-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="bc242-129">從元件的 CLR 標頭尋找 managed 進入點。</span><span class="sxs-lookup"><span data-stu-id="bc242-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="bc242-130">開始執行。</span><span class="sxs-lookup"><span data-stu-id="bc242-130">Begins execution.</span></span>  
  
 <span data-ttu-id="bc242-131">卸載 managed 模組映射時，載入器會呼叫[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="bc242-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="bc242-132">不過，此函數不會執行任何動作;它只會傳回。</span><span class="sxs-lookup"><span data-stu-id="bc242-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc242-133">需求</span><span class="sxs-lookup"><span data-stu-id="bc242-133">Requirements</span></span>  
 <span data-ttu-id="bc242-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc242-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc242-135">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="bc242-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc242-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bc242-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc242-137">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc242-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc242-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc242-138">See also</span></span>

- [<span data-ttu-id="bc242-139">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="bc242-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
