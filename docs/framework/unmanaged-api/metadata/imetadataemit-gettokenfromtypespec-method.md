---
title: "IMetaDataEmit::GetTokenFromTypeSpec 方法"
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
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6acb9d340aa1dc8df5d0b9dc3b0c0dd9c159257e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="e274e-102">IMetaDataEmit::GetTokenFromTypeSpec 方法</span><span class="sxs-lookup"><span data-stu-id="e274e-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="e274e-103">取得具有指定的中繼資料簽章的類型中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e274e-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e274e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e274e-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e274e-105">參數</span><span class="sxs-lookup"><span data-stu-id="e274e-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="e274e-106">[in]正在定義的簽章。</span><span class="sxs-lookup"><span data-stu-id="e274e-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="e274e-107">[in]中的位元組計數`pvSig`。</span><span class="sxs-lookup"><span data-stu-id="e274e-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="e274e-108">[out]`mdTypeSpec`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e274e-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e274e-109">需求</span><span class="sxs-lookup"><span data-stu-id="e274e-109">Requirements</span></span>  
 <span data-ttu-id="e274e-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e274e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e274e-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e274e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e274e-112">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e274e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e274e-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e274e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e274e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e274e-114">See Also</span></span>  
 [<span data-ttu-id="e274e-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="e274e-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e274e-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="e274e-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
