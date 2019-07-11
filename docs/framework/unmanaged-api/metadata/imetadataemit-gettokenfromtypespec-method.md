---
title: IMetaDataEmit::GetTokenFromTypeSpec 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85b0edc81a9a861a3eed6a7bc3ffc1ed1db37403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770742"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="f4428-102">IMetaDataEmit::GetTokenFromTypeSpec 方法</span><span class="sxs-lookup"><span data-stu-id="f4428-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="f4428-103">取得具有指定之中繼資料簽章的類型中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f4428-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4428-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4428-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4428-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4428-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="f4428-106">[in]正在定義的簽章。</span><span class="sxs-lookup"><span data-stu-id="f4428-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="f4428-107">[in]中的位元組計數`pvSig`。</span><span class="sxs-lookup"><span data-stu-id="f4428-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="f4428-108">[out]`mdTypeSpec`指派權杖。</span><span class="sxs-lookup"><span data-stu-id="f4428-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4428-109">需求</span><span class="sxs-lookup"><span data-stu-id="f4428-109">Requirements</span></span>  
 <span data-ttu-id="f4428-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4428-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4428-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f4428-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4428-112">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f4428-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4428-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4428-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4428-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4428-114">See also</span></span>

- [<span data-ttu-id="f4428-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f4428-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f4428-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f4428-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
