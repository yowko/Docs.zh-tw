---
title: ICLRStrongName::GetHashFromFileW 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 553acc178bc5805b5afef5931fefc8ad74cbac39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135180"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="379cf-102">ICLRStrongName::GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="379cf-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="379cf-103">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="379cf-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="379cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="379cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="379cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="379cf-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="379cf-106">在要雜湊之檔案的 Unicode 名稱。</span><span class="sxs-lookup"><span data-stu-id="379cf-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="379cf-107">[in、out]產生雜湊時要使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="379cf-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="379cf-108">有效的演算法是由 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="379cf-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="379cf-109">如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。</span><span class="sxs-lookup"><span data-stu-id="379cf-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="379cf-110">脫銷包含所產生之雜湊的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="379cf-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="379cf-111">在`pbHash`所指向之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="379cf-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="379cf-112">脫銷`pbHash`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="379cf-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="379cf-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="379cf-113">Return Value</span></span>  
 <span data-ttu-id="379cf-114">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="379cf-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="379cf-115">備註</span><span class="sxs-lookup"><span data-stu-id="379cf-115">Remarks</span></span>  
 <span data-ttu-id="379cf-116">這個方法與[ICLRStrongName：： GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)方法相同，不同之處在于檔案名規格是 Unicode 而不是 ANSI。</span><span class="sxs-lookup"><span data-stu-id="379cf-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="379cf-117">需求</span><span class="sxs-lookup"><span data-stu-id="379cf-117">Requirements</span></span>  
 <span data-ttu-id="379cf-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="379cf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="379cf-119">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="379cf-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="379cf-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="379cf-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="379cf-121">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="379cf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="379cf-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="379cf-122">See also</span></span>

- [<span data-ttu-id="379cf-123">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="379cf-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="379cf-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="379cf-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
