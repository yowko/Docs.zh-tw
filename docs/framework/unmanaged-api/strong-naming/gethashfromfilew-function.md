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
ms.openlocfilehash: 77b164cdec0dd224042e4de3265d14a4991d60ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771899"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="5a4b4-102">GetHashFromFileW 函式</span><span class="sxs-lookup"><span data-stu-id="5a4b4-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="5a4b4-103">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="5a4b4-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-104">This function has been deprecated.</span></span> <span data-ttu-id="5a4b4-105">使用[iclrstrongname:: Gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4b4-106">語法</span><span class="sxs-lookup"><span data-stu-id="5a4b4-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="5a4b4-107">參數</span><span class="sxs-lookup"><span data-stu-id="5a4b4-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5a4b4-108">[in]要雜湊之檔案的 Unicode 名稱。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5a4b4-109">[in、 out]要產生的雜湊時所使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="5a4b4-110">有效的演算法為 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="5a4b4-111">如果`piHashAlg`設為 0，CALG_SHA-1 會使用預設演算法。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5a4b4-112">[out]位元組陣列，包含產生的雜湊。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5a4b4-113">[in]所指向的緩衝區大小上限`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5a4b4-114">[out]大小，以位元組為單位的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a4b4-115">備註</span><span class="sxs-lookup"><span data-stu-id="5a4b4-115">Remarks</span></span>  
 <span data-ttu-id="5a4b4-116">此函式是相同[GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)，不同之處在於，檔案名稱規格會是 Unicode，而不是 ANSI。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4b4-117">需求</span><span class="sxs-lookup"><span data-stu-id="5a4b4-117">Requirements</span></span>  
 <span data-ttu-id="5a4b4-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a4b4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4b4-119">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="5a4b4-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5a4b4-120">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5a4b4-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a4b4-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a4b4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4b4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a4b4-122">See also</span></span>

- [<span data-ttu-id="5a4b4-123">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="5a4b4-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="5a4b4-124">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="5a4b4-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="5a4b4-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5a4b4-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
