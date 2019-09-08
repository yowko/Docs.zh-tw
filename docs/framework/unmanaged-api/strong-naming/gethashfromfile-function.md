---
title: GetHashFromFile 函式
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799224"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="1b4f0-102">GetHashFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="1b4f0-102">GetHashFromFile Function</span></span>
<span data-ttu-id="1b4f0-103">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="1b4f0-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-104">This function has been deprecated.</span></span> <span data-ttu-id="1b4f0-105">請改用[ICLRStrongName：： GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b4f0-106">語法</span><span class="sxs-lookup"><span data-stu-id="1b4f0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b4f0-107">參數</span><span class="sxs-lookup"><span data-stu-id="1b4f0-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="1b4f0-108">在要雜湊的檔案名。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="1b4f0-109">[in、out]產生雜湊時要使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="1b4f0-110">有效的演算法是由 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="1b4f0-111">如果`piHashAlg`設定為0，則會使用預設演算法 CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="1b4f0-112">脫銷包含所產生之雜湊的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="1b4f0-113">在`pbHash`指向的緩衝區大小上限。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="1b4f0-114">脫銷傳回`pbHash`之的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b4f0-115">備註</span><span class="sxs-lookup"><span data-stu-id="1b4f0-115">Remarks</span></span>  
 <span data-ttu-id="1b4f0-116">此函式與[GetHashFromFileW](gethashfromfilew-function.md)相同，不同之處在于檔案名規格是 ANSI，而不是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b4f0-117">需求</span><span class="sxs-lookup"><span data-stu-id="1b4f0-117">Requirements</span></span>  
 <span data-ttu-id="1b4f0-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b4f0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b4f0-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="1b4f0-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1b4f0-120">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1b4f0-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b4f0-121">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b4f0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b4f0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b4f0-122">See also</span></span>

- [<span data-ttu-id="1b4f0-123">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="1b4f0-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="1b4f0-124">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="1b4f0-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="1b4f0-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1b4f0-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
