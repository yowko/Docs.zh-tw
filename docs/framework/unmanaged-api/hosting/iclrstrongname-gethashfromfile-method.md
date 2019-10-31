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
ms.openlocfilehash: 798bb0585bfe4cc29afba2fbefae818301704613
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135186"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="aa21b-102">ICLRStrongName::GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="aa21b-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="aa21b-103">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="aa21b-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa21b-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa21b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa21b-105">參數</span><span class="sxs-lookup"><span data-stu-id="aa21b-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="aa21b-106">在要雜湊的檔案名。</span><span class="sxs-lookup"><span data-stu-id="aa21b-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="aa21b-107">[in、out]產生雜湊時要使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="aa21b-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="aa21b-108">有效的演算法是由 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="aa21b-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="aa21b-109">如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="aa21b-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="aa21b-110">脫銷包含所產生之雜湊的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="aa21b-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="aa21b-111">在`pbHash` 指向的緩衝區大小上限。</span><span class="sxs-lookup"><span data-stu-id="aa21b-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="aa21b-112">脫銷傳回之 `pbHash`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="aa21b-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa21b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="aa21b-113">Return Value</span></span>  
 <span data-ttu-id="aa21b-114">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="aa21b-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa21b-115">備註</span><span class="sxs-lookup"><span data-stu-id="aa21b-115">Remarks</span></span>  
 <span data-ttu-id="aa21b-116">這個方法與[ICLRStrongName：： GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)方法相同，不同之處在于檔案名規格是 ANSI，而不是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="aa21b-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa21b-117">需求</span><span class="sxs-lookup"><span data-stu-id="aa21b-117">Requirements</span></span>  
 <span data-ttu-id="aa21b-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa21b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa21b-119">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="aa21b-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aa21b-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="aa21b-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa21b-121">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa21b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa21b-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa21b-122">See also</span></span>

- [<span data-ttu-id="aa21b-123">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="aa21b-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="aa21b-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="aa21b-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
