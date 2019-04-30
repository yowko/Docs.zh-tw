---
title: GetHashFromBlob 函式
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d9e7b52c9061a1a7b470f9d4abf735e605087dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000528"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="bda53-102">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="bda53-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="bda53-103">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="bda53-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="bda53-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="bda53-104">This function has been deprecated.</span></span> <span data-ttu-id="bda53-105">使用[iclrstrongname:: Gethashfromblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="bda53-105">Use the [ICLRStrongName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="bda53-106">語法</span><span class="sxs-lookup"><span data-stu-id="bda53-106">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="bda53-107">參數</span><span class="sxs-lookup"><span data-stu-id="bda53-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="bda53-108">[in]要雜湊的記憶體區塊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="bda53-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="bda53-109">[in]記憶體區塊的長度，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="bda53-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="bda53-110">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="bda53-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="bda53-111">使用零的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="bda53-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="bda53-112">[out]傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bda53-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="bda53-113">[in]要求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="bda53-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="bda53-114">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="bda53-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="bda53-115">需求</span><span class="sxs-lookup"><span data-stu-id="bda53-115">Requirements</span></span>

<span data-ttu-id="bda53-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bda53-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="bda53-117">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="bda53-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="bda53-118">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bda53-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="bda53-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda53-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bda53-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bda53-120">See also</span></span>

- [<span data-ttu-id="bda53-121">GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="bda53-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="bda53-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="bda53-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)