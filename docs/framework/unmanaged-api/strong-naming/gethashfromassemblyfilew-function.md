---
title: GetHashFromAssemblyFileW 函式
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d034f15db8f3d452a055c127bb7095667c089ffe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772045"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="52f31-102">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="52f31-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="52f31-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="52f31-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="52f31-104">組件檔案的路徑必須指定為 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="52f31-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="52f31-105">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="52f31-105">This function has been deprecated.</span></span> <span data-ttu-id="52f31-106">使用[iclrstrongname:: Gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="52f31-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f31-107">語法</span><span class="sxs-lookup"><span data-stu-id="52f31-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52f31-108">參數</span><span class="sxs-lookup"><span data-stu-id="52f31-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="52f31-109">[in]要雜湊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="52f31-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="52f31-110">這個參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="52f31-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="52f31-111">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="52f31-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="52f31-112">使用預設雜湊演算法的零。</span><span class="sxs-lookup"><span data-stu-id="52f31-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="52f31-113">[out]傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="52f31-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="52f31-114">[in]要求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="52f31-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="52f31-115">[out]傳回大小，以位元組為單位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="52f31-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f31-116">需求</span><span class="sxs-lookup"><span data-stu-id="52f31-116">Requirements</span></span>  
 <span data-ttu-id="52f31-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52f31-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f31-118">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="52f31-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="52f31-119">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="52f31-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52f31-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f31-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f31-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52f31-121">See also</span></span>

- [<span data-ttu-id="52f31-122">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="52f31-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="52f31-123">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="52f31-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="52f31-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="52f31-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
