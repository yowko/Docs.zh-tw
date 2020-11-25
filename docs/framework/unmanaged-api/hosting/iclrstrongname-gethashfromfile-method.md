---
title: ICLRStrongName::GetHashFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ff346d8f7ba321904a8d91079298b58039e6eb54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727597"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="457b7-102">ICLRStrongName::GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="457b7-102">ICLRStrongName::GetHashFromFile Method</span></span>

<span data-ttu-id="457b7-103">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="457b7-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="457b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="457b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="457b7-105">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="457b7-106">在要雜湊處理的檔案名。</span><span class="sxs-lookup"><span data-stu-id="457b7-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="457b7-107">[in，out]產生雜湊時要使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="457b7-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="457b7-108">有效的演算法是由 Win32 CryptoAPI 定義的演算法。</span><span class="sxs-lookup"><span data-stu-id="457b7-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="457b7-109">如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="457b7-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="457b7-110">擴展位元組陣列，其中包含產生的雜湊。</span><span class="sxs-lookup"><span data-stu-id="457b7-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="457b7-111">在指向的緩衝區大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="457b7-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="457b7-112">擴展傳回之的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="457b7-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="457b7-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="457b7-113">Return Value</span></span>  

 <span data-ttu-id="457b7-114">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="457b7-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="457b7-115">備註</span><span class="sxs-lookup"><span data-stu-id="457b7-115">Remarks</span></span>  

 <span data-ttu-id="457b7-116">這個方法與 [ICLRStrongName：： GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) 方法相同，不同之處在于檔案名規格是 ANSI 而不是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="457b7-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="457b7-117">需求</span><span class="sxs-lookup"><span data-stu-id="457b7-117">Requirements</span></span>  

 <span data-ttu-id="457b7-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="457b7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="457b7-119">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="457b7-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="457b7-120">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="457b7-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="457b7-121">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="457b7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457b7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="457b7-122">See also</span></span>

- [<span data-ttu-id="457b7-123">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="457b7-123">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="457b7-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="457b7-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
