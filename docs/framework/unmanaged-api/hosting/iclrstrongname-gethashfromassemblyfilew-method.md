---
title: "ICLRStrongName::GetHashFromAssemblyFileW 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromAssemblyFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 14b4e6dae97777873f458018acdaf0c3f5d4f070
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="ae40b-102">ICLRStrongName::GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="ae40b-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="ae40b-103">產生之雜湊的 Unicode 字串所指定的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="ae40b-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae40b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae40b-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae40b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae40b-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ae40b-106">[in]要雜湊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ae40b-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="ae40b-107">這個參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="ae40b-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ae40b-108">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="ae40b-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ae40b-109">使用預設雜湊演算法的零。</span><span class="sxs-lookup"><span data-stu-id="ae40b-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ae40b-110">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ae40b-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ae40b-111">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="ae40b-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ae40b-112">[out]傳回的大小，以位元組為單位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="ae40b-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae40b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae40b-113">Return Value</span></span>  
 <span data-ttu-id="ae40b-114">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="ae40b-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae40b-115">需求</span><span class="sxs-lookup"><span data-stu-id="ae40b-115">Requirements</span></span>  
 <span data-ttu-id="ae40b-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae40b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae40b-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ae40b-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ae40b-118">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ae40b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae40b-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae40b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae40b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae40b-120">See Also</span></span>  
 [<span data-ttu-id="ae40b-121">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="ae40b-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="ae40b-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ae40b-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
