---
title: GetHashFromAssemblyFile 函式
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56a509d08b19cf449177984e7b59481eb7b09a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092158"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="e4602-102">GetHashFromAssemblyFile 函式</span><span class="sxs-lookup"><span data-stu-id="e4602-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="e4602-103">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="e4602-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="e4602-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="e4602-104">This function has been deprecated.</span></span> <span data-ttu-id="e4602-105">使用[iclrstrongname:: Gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="e4602-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4602-106">語法</span><span class="sxs-lookup"><span data-stu-id="e4602-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4602-107">參數</span><span class="sxs-lookup"><span data-stu-id="e4602-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="e4602-108">[in]要雜湊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e4602-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e4602-109">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="e4602-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e4602-110">使用預設雜湊演算法的零。</span><span class="sxs-lookup"><span data-stu-id="e4602-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e4602-111">[out]傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e4602-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e4602-112">[in]要求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="e4602-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e4602-113">[out]傳回大小，以位元組為單位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="e4602-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4602-114">需求</span><span class="sxs-lookup"><span data-stu-id="e4602-114">Requirements</span></span>  
 <span data-ttu-id="e4602-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4602-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4602-116">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e4602-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e4602-117">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e4602-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e4602-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e4602-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e4602-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4602-119">See also</span></span>

- [<span data-ttu-id="e4602-120">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="e4602-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="e4602-121">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="e4602-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="e4602-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="e4602-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
