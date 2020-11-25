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
ms.openlocfilehash: ee9f9cd9a9f35c6c54497ad382bb6f9817d186bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732368"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="4ee99-102">GetHashFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="4ee99-102">GetHashFromFile Function</span></span>

<span data-ttu-id="4ee99-103">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="4ee99-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="4ee99-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="4ee99-104">This function has been deprecated.</span></span> <span data-ttu-id="4ee99-105">請改用 [ICLRStrongName：： GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="4ee99-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ee99-106">語法</span><span class="sxs-lookup"><span data-stu-id="4ee99-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ee99-107">參數</span><span class="sxs-lookup"><span data-stu-id="4ee99-107">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="4ee99-108">在要雜湊處理的檔案名。</span><span class="sxs-lookup"><span data-stu-id="4ee99-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4ee99-109">[in，out]產生雜湊時要使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="4ee99-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="4ee99-110">有效的演算法是由 Win32 CryptoAPI 定義的演算法。</span><span class="sxs-lookup"><span data-stu-id="4ee99-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="4ee99-111">如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="4ee99-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4ee99-112">擴展位元組陣列，其中包含產生的雜湊。</span><span class="sxs-lookup"><span data-stu-id="4ee99-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4ee99-113">在指向的緩衝區大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="4ee99-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4ee99-114">擴展傳回之的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="4ee99-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ee99-115">備註</span><span class="sxs-lookup"><span data-stu-id="4ee99-115">Remarks</span></span>  

 <span data-ttu-id="4ee99-116">此函式與 [GetHashFromFileW](gethashfromfilew-function.md)相同，不同之處在于檔案名規格為 ANSI 而非 Unicode。</span><span class="sxs-lookup"><span data-stu-id="4ee99-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ee99-117">需求</span><span class="sxs-lookup"><span data-stu-id="4ee99-117">Requirements</span></span>  

 <span data-ttu-id="4ee99-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ee99-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ee99-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="4ee99-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4ee99-120">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="4ee99-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ee99-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ee99-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee99-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ee99-122">See also</span></span>

- [<span data-ttu-id="4ee99-123">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="4ee99-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="4ee99-124">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="4ee99-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="4ee99-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="4ee99-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
