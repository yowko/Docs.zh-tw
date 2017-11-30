---
title: "GetHashFromFileW 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFileW
helpviewer_keywords: GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c19047f03279b1284ea8b5b8f99785cfaff5146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="86cfe-102">GetHashFromFileW 函式</span><span class="sxs-lookup"><span data-stu-id="86cfe-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="86cfe-103">產生之雜湊的 Unicode 字串所指定的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="86cfe-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="86cfe-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="86cfe-104">This function has been deprecated.</span></span> <span data-ttu-id="86cfe-105">使用[iclrstrongname:: Gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="86cfe-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cfe-106">語法</span><span class="sxs-lookup"><span data-stu-id="86cfe-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="86cfe-107">參數</span><span class="sxs-lookup"><span data-stu-id="86cfe-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="86cfe-108">[in]Unicode 雜湊的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="86cfe-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="86cfe-109">[in、 out]要產生雜湊時所使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="86cfe-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="86cfe-110">有效的演算法是由 Win32 CryptoAPI 所定義。</span><span class="sxs-lookup"><span data-stu-id="86cfe-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="86cfe-111">如果`piHashAlg`設為 0，則使用 CALG_SHA 1 的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="86cfe-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="86cfe-112">[out]位元組陣列，包含所產生的雜湊。</span><span class="sxs-lookup"><span data-stu-id="86cfe-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="86cfe-113">[in]所指向之緩衝區的大小上限`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="86cfe-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="86cfe-114">[out]大小，以位元組為單位的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="86cfe-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86cfe-115">備註</span><span class="sxs-lookup"><span data-stu-id="86cfe-115">Remarks</span></span>  
 <span data-ttu-id="86cfe-116">此函式是相同[GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)，唯一的檔案名稱規格是 Unicode，而非 ANSI。</span><span class="sxs-lookup"><span data-stu-id="86cfe-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86cfe-117">需求</span><span class="sxs-lookup"><span data-stu-id="86cfe-117">Requirements</span></span>  
 <span data-ttu-id="86cfe-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86cfe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86cfe-119">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="86cfe-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="86cfe-120">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="86cfe-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86cfe-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86cfe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86cfe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86cfe-122">See Also</span></span>  
 [<span data-ttu-id="86cfe-123">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="86cfe-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="86cfe-124">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="86cfe-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="86cfe-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="86cfe-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
