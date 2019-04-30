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
ms.openlocfilehash: 5774b7cdcfedfc407b626ab5052f5b4a77461e9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049384"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="097c4-102">GetHashFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="097c4-102">GetHashFromFile Function</span></span>
<span data-ttu-id="097c4-103">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="097c4-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="097c4-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="097c4-104">This function has been deprecated.</span></span> <span data-ttu-id="097c4-105">使用[iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="097c4-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="097c4-106">語法</span><span class="sxs-lookup"><span data-stu-id="097c4-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="097c4-107">參數</span><span class="sxs-lookup"><span data-stu-id="097c4-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="097c4-108">[in]要雜湊之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="097c4-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="097c4-109">[in、 out]要產生的雜湊時所使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="097c4-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="097c4-110">有效的演算法為 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="097c4-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="097c4-111">如果`piHashAlg`設為 0，CALG_SHA-1 會使用預設演算法。</span><span class="sxs-lookup"><span data-stu-id="097c4-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="097c4-112">[out]位元組陣列，包含產生的雜湊。</span><span class="sxs-lookup"><span data-stu-id="097c4-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="097c4-113">[in]緩衝區的大小上限，`pbHash`指向。</span><span class="sxs-lookup"><span data-stu-id="097c4-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="097c4-114">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="097c4-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="097c4-115">備註</span><span class="sxs-lookup"><span data-stu-id="097c4-115">Remarks</span></span>  
 <span data-ttu-id="097c4-116">此函式是相同[GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)，不同之處在於其檔案名稱規格的 ANSI，而非 Unicode。</span><span class="sxs-lookup"><span data-stu-id="097c4-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="097c4-117">需求</span><span class="sxs-lookup"><span data-stu-id="097c4-117">Requirements</span></span>  
 <span data-ttu-id="097c4-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="097c4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="097c4-119">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="097c4-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="097c4-120">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="097c4-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="097c4-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="097c4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097c4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="097c4-122">See also</span></span>

- [<span data-ttu-id="097c4-123">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="097c4-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="097c4-124">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="097c4-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="097c4-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="097c4-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
