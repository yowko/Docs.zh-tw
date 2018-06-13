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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87600781c90fe5e6e049af74a68859955153f3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433337"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="544ea-102">ICLRStrongName::GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="544ea-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="544ea-103">產生之雜湊的 Unicode 字串所指定的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="544ea-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="544ea-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="544ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="544ea-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="544ea-106">[in]Unicode 雜湊的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="544ea-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="544ea-107">[in、 out]要產生雜湊時所使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="544ea-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="544ea-108">有效的演算法是由 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="544ea-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="544ea-109">如果`piHashAlg`設為 0，則使用 CALG_SHA 1 的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="544ea-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="544ea-110">[out]位元組陣列，包含所產生的雜湊。</span><span class="sxs-lookup"><span data-stu-id="544ea-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="544ea-111">[in]所指向之緩衝區的大小上限`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="544ea-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="544ea-112">[out]大小，以位元組為單位的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="544ea-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="544ea-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="544ea-113">Return Value</span></span>  
 <span data-ttu-id="544ea-114">`S_OK` 如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="544ea-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="544ea-115">備註</span><span class="sxs-lookup"><span data-stu-id="544ea-115">Remarks</span></span>  
 <span data-ttu-id="544ea-116">這個方法相當於[iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)方法，不同之處在於的檔案名稱的規格是 Unicode，而非 ANSI。</span><span class="sxs-lookup"><span data-stu-id="544ea-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="544ea-117">需求</span><span class="sxs-lookup"><span data-stu-id="544ea-117">Requirements</span></span>  
 <span data-ttu-id="544ea-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="544ea-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="544ea-119">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="544ea-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="544ea-120">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="544ea-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="544ea-121">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="544ea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544ea-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="544ea-122">See Also</span></span>  
 [<span data-ttu-id="544ea-123">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="544ea-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="544ea-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="544ea-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
