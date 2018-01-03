---
title: "ICLRStrongName::GetHashFromBlob 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1947441e395ddb9d9d0fd9c4b02e7e991b1c84a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="b9b6a-102">ICLRStrongName::GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="b9b6a-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="b9b6a-103">取得該組件的雜湊指定的記憶體位址，使用指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9b6a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b9b6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9b6a-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="b9b6a-106">[in]要雜湊的記憶體區塊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="b9b6a-107">[in]記憶體區塊的長度，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b9b6a-108">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b9b6a-109">使用預設演算法為零。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b9b6a-110">[out]傳回雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b9b6a-111">[in]要求的大小上限的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b9b6a-112">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9b6a-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9b6a-113">Return Value</span></span>  
 <span data-ttu-id="b9b6a-114">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b6a-115">需求</span><span class="sxs-lookup"><span data-stu-id="b9b6a-115">Requirements</span></span>  
 <span data-ttu-id="b9b6a-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9b6a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b6a-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b9b6a-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b9b6a-118">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b9b6a-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9b6a-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b6a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b6a-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b6a-120">See Also</span></span>  
 [<span data-ttu-id="b9b6a-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="b9b6a-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
