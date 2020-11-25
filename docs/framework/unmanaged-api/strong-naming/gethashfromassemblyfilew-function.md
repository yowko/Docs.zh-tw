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
ms.openlocfilehash: b895c77850c0457fd2a152c1128c016093599f76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730977"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="30456-102">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="30456-102">GetHashFromAssemblyFileW Function</span></span>

<span data-ttu-id="30456-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="30456-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="30456-104">元件檔的路徑必須指定為 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="30456-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="30456-105">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="30456-105">This function has been deprecated.</span></span> <span data-ttu-id="30456-106">請改用 [ICLRStrongName：： GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="30456-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30456-107">語法</span><span class="sxs-lookup"><span data-stu-id="30456-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30456-108">參數</span><span class="sxs-lookup"><span data-stu-id="30456-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="30456-109">在要雜湊處理之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="30456-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="30456-110">此參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="30456-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="30456-111">[in，out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="30456-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="30456-112">使用零作為預設雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="30456-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="30456-113">擴展傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="30456-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="30456-114">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="30456-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="30456-115">擴展傳回的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="30456-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30456-116">需求</span><span class="sxs-lookup"><span data-stu-id="30456-116">Requirements</span></span>  

 <span data-ttu-id="30456-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30456-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30456-118">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="30456-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="30456-119">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="30456-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30456-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30456-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30456-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30456-121">See also</span></span>

- [<span data-ttu-id="30456-122">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="30456-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="30456-123">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="30456-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="30456-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="30456-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
