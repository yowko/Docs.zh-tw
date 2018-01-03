---
title: "ICLRStrongName::GetHashFromFile 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480113148e039ff1be3e438b4af2e24fdeacba14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="764f8-102">ICLRStrongName::GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="764f8-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="764f8-103">透過指定檔案的內容中產生之雜湊。</span><span class="sxs-lookup"><span data-stu-id="764f8-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="764f8-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="764f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="764f8-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="764f8-106">[in]要雜湊的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="764f8-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="764f8-107">[in、 out]要產生雜湊時所使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="764f8-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="764f8-108">有效的演算法是由 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="764f8-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="764f8-109">如果`piHashAlg`設為 0，則使用 CALG_SHA 1 的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="764f8-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="764f8-110">[out]位元組陣列，包含所產生的雜湊。</span><span class="sxs-lookup"><span data-stu-id="764f8-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="764f8-111">[in]緩衝區的大小上限，`pbHash`指向。</span><span class="sxs-lookup"><span data-stu-id="764f8-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="764f8-112">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="764f8-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="764f8-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="764f8-113">Return Value</span></span>  
 <span data-ttu-id="764f8-114">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="764f8-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="764f8-115">備註</span><span class="sxs-lookup"><span data-stu-id="764f8-115">Remarks</span></span>  
 <span data-ttu-id="764f8-116">這個方法相當於[iclrstrongname:: Gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)方法，不同之處在於的檔案名稱的規格為 ANSI，而非 Unicode。</span><span class="sxs-lookup"><span data-stu-id="764f8-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764f8-117">需求</span><span class="sxs-lookup"><span data-stu-id="764f8-117">Requirements</span></span>  
 <span data-ttu-id="764f8-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="764f8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="764f8-119">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="764f8-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="764f8-120">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="764f8-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="764f8-121">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="764f8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764f8-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="764f8-122">See Also</span></span>  
 [<span data-ttu-id="764f8-123">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="764f8-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="764f8-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="764f8-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
