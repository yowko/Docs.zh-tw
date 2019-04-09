---
title: ICLRStrongName::GetHashFromAssemblyFileW 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 578dd7941ad7a2cf1d39a3aeed7fa823eb7efa79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162159"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="14e9d-102">ICLRStrongName::GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="14e9d-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="14e9d-103">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="14e9d-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="14e9d-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14e9d-105">參數</span><span class="sxs-lookup"><span data-stu-id="14e9d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="14e9d-106">[in]要雜湊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="14e9d-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="14e9d-107">這個參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="14e9d-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="14e9d-108">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="14e9d-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="14e9d-109">使用預設雜湊演算法的零。</span><span class="sxs-lookup"><span data-stu-id="14e9d-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="14e9d-110">[out]傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="14e9d-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="14e9d-111">[in]要求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="14e9d-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="14e9d-112">[out]傳回大小，以位元組為單位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="14e9d-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14e9d-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="14e9d-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="14e9d-114">如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="14e9d-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14e9d-115">需求</span><span class="sxs-lookup"><span data-stu-id="14e9d-115">Requirements</span></span>  
 <span data-ttu-id="14e9d-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14e9d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e9d-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="14e9d-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="14e9d-118">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="14e9d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="14e9d-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="14e9d-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="14e9d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14e9d-120">See also</span></span>

- [<span data-ttu-id="14e9d-121">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="14e9d-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="14e9d-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="14e9d-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
