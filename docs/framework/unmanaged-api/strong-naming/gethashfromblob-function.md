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
ms.openlocfilehash: 360036cd1578c2845f09f92c09d79e44618abe75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="f8778-102">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="f8778-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="f8778-103">取得該組件的雜湊指定的記憶體位址，使用指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="f8778-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="f8778-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="f8778-104">This function has been deprecated.</span></span> <span data-ttu-id="f8778-105">使用[ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="f8778-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8778-106">語法</span><span class="sxs-lookup"><span data-stu-id="f8778-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f8778-107">參數</span><span class="sxs-lookup"><span data-stu-id="f8778-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="f8778-108">[in]要雜湊的記憶體區塊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="f8778-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="f8778-109">[in]記憶體區塊的長度，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="f8778-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f8778-110">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="f8778-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f8778-111">使用預設演算法為零。</span><span class="sxs-lookup"><span data-stu-id="f8778-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f8778-112">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f8778-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f8778-113">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="f8778-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f8778-114">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="f8778-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8778-115">需求</span><span class="sxs-lookup"><span data-stu-id="f8778-115">Requirements</span></span>  
 <span data-ttu-id="f8778-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8778-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8778-117">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f8778-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f8778-118">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f8778-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8778-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8778-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8778-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8778-120">See Also</span></span>  
 [<span data-ttu-id="f8778-121">GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="f8778-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="f8778-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="f8778-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
