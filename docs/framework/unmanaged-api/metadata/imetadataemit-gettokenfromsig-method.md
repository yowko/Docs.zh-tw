---
title: "IMetaDataEmit::GetTokenFromSig 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromSig
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df454b8dd95839f4cabe3c725e206f3683437ec4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="0e86d-102">IMetaDataEmit::GetTokenFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="0e86d-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="0e86d-103">取得指定的中繼資料簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0e86d-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e86d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e86d-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e86d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e86d-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="0e86d-106">[in]要保存和儲存簽章。</span><span class="sxs-lookup"><span data-stu-id="0e86d-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="0e86d-107">[in]中的位元組計數`pvSig`。</span><span class="sxs-lookup"><span data-stu-id="0e86d-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="0e86d-108">[out]`mdSignature`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0e86d-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e86d-109">需求</span><span class="sxs-lookup"><span data-stu-id="0e86d-109">Requirements</span></span>  
 <span data-ttu-id="0e86d-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e86d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e86d-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e86d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e86d-112">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0e86d-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e86d-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e86d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e86d-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e86d-114">See Also</span></span>  
 [<span data-ttu-id="0e86d-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0e86d-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="0e86d-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0e86d-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
