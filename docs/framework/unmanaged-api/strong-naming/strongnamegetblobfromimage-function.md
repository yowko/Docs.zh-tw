---
title: StrongNameGetBlobFromImage 函式
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b136e1fa480e53bcacfd9ea832d1dc4d1bd69f74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162772"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="ebfc8-102">StrongNameGetBlobFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="ebfc8-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="ebfc8-103">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="ebfc8-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-104">This function has been deprecated.</span></span> <span data-ttu-id="ebfc8-105">使用[iclrstrongname:: Strongnamegetblobfromimage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfc8-106">語法</span><span class="sxs-lookup"><span data-stu-id="ebfc8-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebfc8-107">參數</span><span class="sxs-lookup"><span data-stu-id="ebfc8-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="ebfc8-108">[in]對應的組件資訊清單的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ebfc8-109">[in]大小 （位元組），在映像的`pbBase`。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="ebfc8-110">[in]包含影像的二進位表示法的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="ebfc8-111">[in、 out]所要求大小上限，以位元組為單位， `pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="ebfc8-112">傳回時，實際的大小，以位元組為單位的`pbBlob`。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebfc8-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ebfc8-113">Return Value</span></span>  
 <span data-ttu-id="ebfc8-114">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebfc8-115">備註</span><span class="sxs-lookup"><span data-stu-id="ebfc8-115">Remarks</span></span>  
 <span data-ttu-id="ebfc8-116">如果`StrongNameGetBlobFromImage`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebfc8-117">需求</span><span class="sxs-lookup"><span data-stu-id="ebfc8-117">Requirements</span></span>  
 <span data-ttu-id="ebfc8-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebfc8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebfc8-119">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ebfc8-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ebfc8-120">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ebfc8-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebfc8-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebfc8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfc8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebfc8-122">See also</span></span>

- [<span data-ttu-id="ebfc8-123">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="ebfc8-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="ebfc8-124">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="ebfc8-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="ebfc8-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ebfc8-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
