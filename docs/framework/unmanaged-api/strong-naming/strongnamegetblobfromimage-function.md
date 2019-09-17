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
ms.openlocfilehash: 86b99b29a85f498a6bfa0363a446bf589876bff9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799094"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="60f81-102">StrongNameGetBlobFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="60f81-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="60f81-103">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="60f81-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="60f81-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="60f81-104">This function has been deprecated.</span></span> <span data-ttu-id="60f81-105">請改用[ICLRStrongName：： StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="60f81-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f81-106">語法</span><span class="sxs-lookup"><span data-stu-id="60f81-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f81-107">參數</span><span class="sxs-lookup"><span data-stu-id="60f81-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="60f81-108">在對應的組件資訊清單的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="60f81-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="60f81-109">在影像的大小（以位元組為單位） `pbBase`。</span><span class="sxs-lookup"><span data-stu-id="60f81-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="60f81-110">在包含影像之二進位表示的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="60f81-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="60f81-111">[in、out]要求的大小上限（以位元組為單位`pbBlob`）。</span><span class="sxs-lookup"><span data-stu-id="60f81-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="60f81-112">傳回時，為的實際大小（以位元組為`pbBlob`單位）。</span><span class="sxs-lookup"><span data-stu-id="60f81-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60f81-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="60f81-113">Return Value</span></span>  
 <span data-ttu-id="60f81-114">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="60f81-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60f81-115">備註</span><span class="sxs-lookup"><span data-stu-id="60f81-115">Remarks</span></span>  
 <span data-ttu-id="60f81-116">如果函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。`StrongNameGetBlobFromImage`</span><span class="sxs-lookup"><span data-stu-id="60f81-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f81-117">需求</span><span class="sxs-lookup"><span data-stu-id="60f81-117">Requirements</span></span>  
 <span data-ttu-id="60f81-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60f81-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f81-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="60f81-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="60f81-120">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="60f81-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60f81-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f81-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f81-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60f81-122">See also</span></span>

- [<span data-ttu-id="60f81-123">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="60f81-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="60f81-124">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="60f81-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="60f81-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="60f81-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
