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
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140707"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="4a0c5-102">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="4a0c5-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="4a0c5-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="4a0c5-104">元件檔的路徑必須指定為 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="4a0c5-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-105">This function has been deprecated.</span></span> <span data-ttu-id="4a0c5-106">請改用[ICLRStrongName：： GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a0c5-107">語法</span><span class="sxs-lookup"><span data-stu-id="4a0c5-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a0c5-108">參數</span><span class="sxs-lookup"><span data-stu-id="4a0c5-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="4a0c5-109">在要雜湊之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="4a0c5-110">這個參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4a0c5-111">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="4a0c5-112">預設雜湊演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4a0c5-113">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4a0c5-114">在`pbHash`的要求大小上限。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4a0c5-115">脫銷傳回的大小，以位元組為單位，`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a0c5-116">需求</span><span class="sxs-lookup"><span data-stu-id="4a0c5-116">Requirements</span></span>  
 <span data-ttu-id="4a0c5-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a0c5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a0c5-118">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="4a0c5-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4a0c5-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4a0c5-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a0c5-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a0c5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0c5-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a0c5-121">See also</span></span>

- [<span data-ttu-id="4a0c5-122">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="4a0c5-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="4a0c5-123">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="4a0c5-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="4a0c5-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="4a0c5-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
