---
title: "GetHashFromAssemblyFile 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFile
helpviewer_keywords: GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5de637f8b8d51e2619ba205d89c753b27722bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="d0e40-102">GetHashFromAssemblyFile 函式</span><span class="sxs-lookup"><span data-stu-id="d0e40-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="d0e40-103">取得指定的組件檔案，使用指定的雜湊演算法的雜湊。</span><span class="sxs-lookup"><span data-stu-id="d0e40-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="d0e40-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="d0e40-104">This function has been deprecated.</span></span> <span data-ttu-id="d0e40-105">使用[iclrstrongname:: Gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="d0e40-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e40-106">語法</span><span class="sxs-lookup"><span data-stu-id="d0e40-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0e40-107">參數</span><span class="sxs-lookup"><span data-stu-id="d0e40-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="d0e40-108">[in]要雜湊檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="d0e40-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d0e40-109">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="d0e40-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d0e40-110">使用預設雜湊演算法的零。</span><span class="sxs-lookup"><span data-stu-id="d0e40-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d0e40-111">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d0e40-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d0e40-112">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="d0e40-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d0e40-113">[out]傳回的大小，以位元組為單位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="d0e40-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e40-114">需求</span><span class="sxs-lookup"><span data-stu-id="d0e40-114">Requirements</span></span>  
 <span data-ttu-id="d0e40-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e40-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0e40-116">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d0e40-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d0e40-117">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d0e40-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0e40-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0e40-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e40-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e40-119">See Also</span></span>  
 [<span data-ttu-id="d0e40-120">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="d0e40-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="d0e40-121">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="d0e40-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="d0e40-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d0e40-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
