---
title: "GetHashFromAssemblyFileW 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 938d7b5633a73aafb81b16fd2fa207160cac4e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="3b12d-102">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="3b12d-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="3b12d-103">取得指定的組件檔案，使用指定的雜湊演算法的雜湊。</span><span class="sxs-lookup"><span data-stu-id="3b12d-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="3b12d-104">組件檔案的路徑必須指定為 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="3b12d-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="3b12d-105">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="3b12d-105">This function has been deprecated.</span></span> <span data-ttu-id="3b12d-106">使用[iclrstrongname:: Gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="3b12d-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b12d-107">語法</span><span class="sxs-lookup"><span data-stu-id="3b12d-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b12d-108">參數</span><span class="sxs-lookup"><span data-stu-id="3b12d-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3b12d-109">[in]要雜湊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="3b12d-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="3b12d-110">這個參數必須是 Unicode 字串。</span><span class="sxs-lookup"><span data-stu-id="3b12d-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="3b12d-111">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="3b12d-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="3b12d-112">使用預設雜湊演算法的零。</span><span class="sxs-lookup"><span data-stu-id="3b12d-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="3b12d-113">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3b12d-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="3b12d-114">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="3b12d-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="3b12d-115">[out]傳回的大小，以位元組為單位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="3b12d-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b12d-116">需求</span><span class="sxs-lookup"><span data-stu-id="3b12d-116">Requirements</span></span>  
 <span data-ttu-id="3b12d-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b12d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b12d-118">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3b12d-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3b12d-119">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3b12d-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b12d-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b12d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b12d-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b12d-121">See Also</span></span>  
 [<span data-ttu-id="3b12d-122">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="3b12d-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="3b12d-123">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="3b12d-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="3b12d-124">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="3b12d-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
