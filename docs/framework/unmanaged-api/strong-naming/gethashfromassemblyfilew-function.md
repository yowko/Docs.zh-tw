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
ms.openlocfilehash: d4b748370ff1aff042923002ad827a0e39d99963
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799274"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="1ee79-102">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="1ee79-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="1ee79-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="1ee79-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="1ee79-104">元件檔的路徑必須指定為 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="1ee79-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="1ee79-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="1ee79-105">This function has been deprecated.</span></span> <span data-ttu-id="1ee79-106">請改用[ICLRStrongName：： GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1ee79-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee79-107">語法</span><span class="sxs-lookup"><span data-stu-id="1ee79-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ee79-108">參數</span><span class="sxs-lookup"><span data-stu-id="1ee79-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="1ee79-109">在要雜湊之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="1ee79-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="1ee79-110">這個參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="1ee79-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="1ee79-111">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="1ee79-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="1ee79-112">預設雜湊演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="1ee79-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="1ee79-113">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1ee79-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="1ee79-114">在要求的大小`pbHash`上限。</span><span class="sxs-lookup"><span data-stu-id="1ee79-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="1ee79-115">脫銷傳回的大小（以位元組為單位`pbHash`）。</span><span class="sxs-lookup"><span data-stu-id="1ee79-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee79-116">需求</span><span class="sxs-lookup"><span data-stu-id="1ee79-116">Requirements</span></span>  
 <span data-ttu-id="1ee79-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee79-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee79-118">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="1ee79-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1ee79-119">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ee79-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ee79-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee79-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee79-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ee79-121">See also</span></span>

- [<span data-ttu-id="1ee79-122">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="1ee79-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="1ee79-123">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="1ee79-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="1ee79-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1ee79-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
