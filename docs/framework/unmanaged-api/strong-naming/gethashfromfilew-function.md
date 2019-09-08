---
title: GetHashFromFileW 函式
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd96b5acb22f63b6e06c981119186680d6593a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799194"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="203ea-102">GetHashFromFileW 函式</span><span class="sxs-lookup"><span data-stu-id="203ea-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="203ea-103">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="203ea-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="203ea-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="203ea-104">This function has been deprecated.</span></span> <span data-ttu-id="203ea-105">請改用[ICLRStrongName：： GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="203ea-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203ea-106">語法</span><span class="sxs-lookup"><span data-stu-id="203ea-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="203ea-107">參數</span><span class="sxs-lookup"><span data-stu-id="203ea-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="203ea-108">在要雜湊之檔案的 Unicode 名稱。</span><span class="sxs-lookup"><span data-stu-id="203ea-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="203ea-109">[in、out]產生雜湊時要使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="203ea-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="203ea-110">有效的演算法是由 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="203ea-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="203ea-111">如果`piHashAlg`設定為0，則會使用預設演算法 CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="203ea-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="203ea-112">脫銷包含所產生之雜湊的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="203ea-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="203ea-113">在所指向`pbHash`之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="203ea-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="203ea-114">脫銷的大小（以位元組為單位`pbHash`）。</span><span class="sxs-lookup"><span data-stu-id="203ea-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="203ea-115">備註</span><span class="sxs-lookup"><span data-stu-id="203ea-115">Remarks</span></span>  
 <span data-ttu-id="203ea-116">此函式與[GetHashFromFile](gethashfromfile-function.md)相同，不同之處在于檔案名規格是 Unicode 而不是 ANSI。</span><span class="sxs-lookup"><span data-stu-id="203ea-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="203ea-117">需求</span><span class="sxs-lookup"><span data-stu-id="203ea-117">Requirements</span></span>  
 <span data-ttu-id="203ea-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="203ea-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="203ea-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="203ea-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="203ea-120">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="203ea-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="203ea-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="203ea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203ea-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="203ea-122">See also</span></span>

- [<span data-ttu-id="203ea-123">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="203ea-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="203ea-124">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="203ea-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="203ea-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="203ea-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
