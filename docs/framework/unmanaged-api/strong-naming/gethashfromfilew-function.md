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
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175079"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="e5f80-102">GetHashFromFileW 函式</span><span class="sxs-lookup"><span data-stu-id="e5f80-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="e5f80-103">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="e5f80-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="e5f80-104">此函數已被棄用。</span><span class="sxs-lookup"><span data-stu-id="e5f80-104">This function has been deprecated.</span></span> <span data-ttu-id="e5f80-105">使用[ICLR 強式名稱：：獲取雜湊弗羅瓦](../hosting/iclrstrongname-gethashfromfilew-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e5f80-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f80-106">語法</span><span class="sxs-lookup"><span data-stu-id="e5f80-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="e5f80-107">參數</span><span class="sxs-lookup"><span data-stu-id="e5f80-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e5f80-108">[在]要雜湊的檔的 Unicode 名稱。</span><span class="sxs-lookup"><span data-stu-id="e5f80-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e5f80-109">[進出]生成雜湊時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="e5f80-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e5f80-110">有效的演算法是由 Win32 加密 API 定義的演算法。</span><span class="sxs-lookup"><span data-stu-id="e5f80-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e5f80-111">如果`piHashAlg`設置為 0，則使用預設演算法CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="e5f80-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e5f80-112">[出]包含生成的雜湊的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="e5f80-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e5f80-113">[在]指向 的緩衝區的最大大小`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="e5f80-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e5f80-114">[出]的大小（以位元組為單位）的大小`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="e5f80-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5f80-115">備註</span><span class="sxs-lookup"><span data-stu-id="e5f80-115">Remarks</span></span>  
 <span data-ttu-id="e5f80-116">此函數與[GetHashFromFile](gethashfromfile-function.md)相同，只不過檔案名規範是 Unicode 而不是 ANSI。</span><span class="sxs-lookup"><span data-stu-id="e5f80-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f80-117">需求</span><span class="sxs-lookup"><span data-stu-id="e5f80-117">Requirements</span></span>  
 <span data-ttu-id="e5f80-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5f80-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5f80-119">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="e5f80-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e5f80-120">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e5f80-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5f80-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5f80-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f80-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5f80-122">See also</span></span>

- [<span data-ttu-id="e5f80-123">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="e5f80-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="e5f80-124">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="e5f80-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="e5f80-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="e5f80-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
