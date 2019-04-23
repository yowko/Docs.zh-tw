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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df9cc0cc86237b1ec439a4ec4fa6a75429c416d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111172"
---
# <a name="corvalidateimage-function"></a><span data-ttu-id="ade0e-102">_CorValidateImage 函式</span><span class="sxs-lookup"><span data-stu-id="ade0e-102">_CorValidateImage Function</span></span>
<span data-ttu-id="ade0e-103">驗證 managed 的模組映像，並載入後通知作業系統載入器。</span><span class="sxs-lookup"><span data-stu-id="ade0e-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade0e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ade0e-104">Syntax</span></span>  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ade0e-105">參數</span><span class="sxs-lookup"><span data-stu-id="ade0e-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="ade0e-106">[in]指向要驗證的映像的起始位置的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ade0e-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="ade0e-107">映像必須已被載入到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="ade0e-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="ade0e-108">[in]映像的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ade0e-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ade0e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ade0e-109">Return Value</span></span>  
 <span data-ttu-id="ade0e-110">此函數會傳回標準值`E_INVALIDARG`， `E_OUTOFMEMORY`， `E_UNEXPECTED`，和`E_FAIL`，以及下列的值。</span><span class="sxs-lookup"><span data-stu-id="ade0e-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="ade0e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ade0e-111">Return value</span></span>|<span data-ttu-id="ade0e-112">描述</span><span class="sxs-lookup"><span data-stu-id="ade0e-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="ade0e-113">映像無效。</span><span class="sxs-lookup"><span data-stu-id="ade0e-113">The image is invalid.</span></span> <span data-ttu-id="ade0e-114">此值沒有 HRESULT 0xC000007BL。</span><span class="sxs-lookup"><span data-stu-id="ade0e-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="ade0e-115">影像是有效的。</span><span class="sxs-lookup"><span data-stu-id="ade0e-115">The image is valid.</span></span> <span data-ttu-id="ade0e-116">此值沒有 HRESULT 0x00000000L。</span><span class="sxs-lookup"><span data-stu-id="ade0e-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ade0e-117">備註</span><span class="sxs-lookup"><span data-stu-id="ade0e-117">Remarks</span></span>  
 <span data-ttu-id="ade0e-118">在 Windows XP 和更新版本中，作業系統載入器會檢查 managed 模組藉由檢查 COM 描述元的目錄中的位元的通用物件檔案格式 (COFF) 標頭。</span><span class="sxs-lookup"><span data-stu-id="ade0e-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="ade0e-119">設定位元表示受管理的模組。</span><span class="sxs-lookup"><span data-stu-id="ade0e-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="ade0e-120">如果載入器偵測到受管理的模組，它會載入 MsCorEE.dll，並呼叫`_CorValidateImage`，會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ade0e-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
-   <span data-ttu-id="ade0e-121">確認映像都是有效的受管理的模組。</span><span class="sxs-lookup"><span data-stu-id="ade0e-121">Confirms that the image is a valid managed module.</span></span>  
  
-   <span data-ttu-id="ade0e-122">Common language runtime (CLR) 中的進入點變更映像中的進入點。</span><span class="sxs-lookup"><span data-stu-id="ade0e-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
-   <span data-ttu-id="ade0e-123">如需 64 位元版本的 Windows，修改的映像從 PE32 格式轉換成 PE32 + 格式是在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="ade0e-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
-   <span data-ttu-id="ade0e-124">載入器在載入 managed 的模組映像時傳回。</span><span class="sxs-lookup"><span data-stu-id="ade0e-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="ade0e-125">針對可執行檔映像，作業系統載入器接著會呼叫[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式，不論在可執行檔中指定的進入點。</span><span class="sxs-lookup"><span data-stu-id="ade0e-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="ade0e-126">DLL 組件映像，則載入器會呼叫[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="ade0e-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="ade0e-127">`_CorExeMain` 或`_CorDllMain`執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ade0e-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
-   <span data-ttu-id="ade0e-128">初始化 CLR。</span><span class="sxs-lookup"><span data-stu-id="ade0e-128">Initializes the CLR.</span></span>  
  
-   <span data-ttu-id="ade0e-129">找出組件的 CLR 標頭的 managed 的進入點。</span><span class="sxs-lookup"><span data-stu-id="ade0e-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
-   <span data-ttu-id="ade0e-130">開始執行。</span><span class="sxs-lookup"><span data-stu-id="ade0e-130">Begins execution.</span></span>  
  
 <span data-ttu-id="ade0e-131">載入器呼叫[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)函式時受管理模組映像，就會卸載。</span><span class="sxs-lookup"><span data-stu-id="ade0e-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="ade0e-132">不過，此函式不會執行任何動作;它只會傳回。</span><span class="sxs-lookup"><span data-stu-id="ade0e-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ade0e-133">需求</span><span class="sxs-lookup"><span data-stu-id="ade0e-133">Requirements</span></span>  
 <span data-ttu-id="ade0e-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ade0e-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade0e-135">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ade0e-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ade0e-136">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ade0e-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ade0e-137">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade0e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade0e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade0e-138">See also</span></span>

- [<span data-ttu-id="ade0e-139">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="ade0e-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
