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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176977"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="8ca04-102">GetHashFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="8ca04-102">GetHashFromFile Function</span></span>
<span data-ttu-id="8ca04-103">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="8ca04-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="8ca04-104">此函數已被棄用。</span><span class="sxs-lookup"><span data-stu-id="8ca04-104">This function has been deprecated.</span></span> <span data-ttu-id="8ca04-105">改用[ICLR 強式名稱：：獲取雜湊檔](../hosting/iclrstrongname-gethashfromfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8ca04-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca04-106">語法</span><span class="sxs-lookup"><span data-stu-id="8ca04-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ca04-107">參數</span><span class="sxs-lookup"><span data-stu-id="8ca04-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="8ca04-108">[在]要雜湊的檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ca04-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="8ca04-109">[進出]生成雜湊時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="8ca04-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="8ca04-110">有效的演算法是由 Win32 加密 API 定義的演算法。</span><span class="sxs-lookup"><span data-stu-id="8ca04-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="8ca04-111">如果`piHashAlg`設置為 0，則使用預設演算法CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="8ca04-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="8ca04-112">[出]包含生成的雜湊的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="8ca04-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="8ca04-113">[在]`pbHash`指向的緩衝區的最大大小。</span><span class="sxs-lookup"><span data-stu-id="8ca04-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="8ca04-114">[出]返回`pbHash`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8ca04-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca04-115">備註</span><span class="sxs-lookup"><span data-stu-id="8ca04-115">Remarks</span></span>  
 <span data-ttu-id="8ca04-116">此函數與[GetHashFromFileW](gethashfromfilew-function.md)相同，只不過檔案名規範是 ANSI 而不是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="8ca04-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca04-117">需求</span><span class="sxs-lookup"><span data-stu-id="8ca04-117">Requirements</span></span>  
 <span data-ttu-id="8ca04-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ca04-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca04-119">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="8ca04-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8ca04-120">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8ca04-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ca04-121">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca04-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca04-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ca04-122">See also</span></span>

- [<span data-ttu-id="8ca04-123">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="8ca04-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="8ca04-124">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="8ca04-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="8ca04-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8ca04-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
