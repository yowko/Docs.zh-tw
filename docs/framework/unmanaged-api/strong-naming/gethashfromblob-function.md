---
title: "GetHashFromBlob 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromBlob
helpviewer_keywords: GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4564ea36ed8dd4c5de0d1633ba791b47bc2a01b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="44ae5-102">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="44ae5-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="44ae5-103">取得該組件的雜湊指定的記憶體位址，使用指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="44ae5-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="44ae5-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="44ae5-104">This function has been deprecated.</span></span> <span data-ttu-id="44ae5-105">使用[ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="44ae5-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44ae5-106">語法</span><span class="sxs-lookup"><span data-stu-id="44ae5-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44ae5-107">參數</span><span class="sxs-lookup"><span data-stu-id="44ae5-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="44ae5-108">[in]要雜湊的記憶體區塊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="44ae5-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="44ae5-109">[in]記憶體區塊的長度，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="44ae5-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="44ae5-110">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="44ae5-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="44ae5-111">使用預設演算法為零。</span><span class="sxs-lookup"><span data-stu-id="44ae5-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="44ae5-112">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="44ae5-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="44ae5-113">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="44ae5-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="44ae5-114">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="44ae5-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44ae5-115">需求</span><span class="sxs-lookup"><span data-stu-id="44ae5-115">Requirements</span></span>  
 <span data-ttu-id="44ae5-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44ae5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44ae5-117">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="44ae5-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="44ae5-118">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="44ae5-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44ae5-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44ae5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ae5-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="44ae5-120">See Also</span></span>  
 [<span data-ttu-id="44ae5-121">GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="44ae5-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="44ae5-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="44ae5-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
