---
title: GetHashFromBlob 函式
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 427d93a9aff527d36720c4199782fa104a66f8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455029"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="2dd7e-102">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="2dd7e-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="2dd7e-103">取得該組件的雜湊指定的記憶體位址，使用指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="2dd7e-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-104">This function has been deprecated.</span></span> <span data-ttu-id="2dd7e-105">使用[ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dd7e-106">語法</span><span class="sxs-lookup"><span data-stu-id="2dd7e-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2dd7e-107">參數</span><span class="sxs-lookup"><span data-stu-id="2dd7e-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="2dd7e-108">[in]要雜湊的記憶體區塊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="2dd7e-109">[in]記憶體區塊的長度，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2dd7e-110">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2dd7e-111">使用預設演算法為零。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2dd7e-112">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2dd7e-113">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2dd7e-114">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dd7e-115">需求</span><span class="sxs-lookup"><span data-stu-id="2dd7e-115">Requirements</span></span>  
 <span data-ttu-id="2dd7e-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd7e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dd7e-117">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2dd7e-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2dd7e-118">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2dd7e-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2dd7e-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dd7e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd7e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dd7e-120">See Also</span></span>  
 [<span data-ttu-id="2dd7e-121">GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="2dd7e-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="2dd7e-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="2dd7e-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
