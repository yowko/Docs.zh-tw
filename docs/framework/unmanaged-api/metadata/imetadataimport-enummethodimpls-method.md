---
title: IMetaDataImport::EnumMethodImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aebfd41a232a3284f79e4229a8845bf5a34f9d1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574764"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="3b8ce-102">IMetaDataImport::EnumMethodImpls 方法</span><span class="sxs-lookup"><span data-stu-id="3b8ce-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="3b8ce-103">列舉代表指定類型方法的 MethodBody 和 MethodDeclaration 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b8ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b8ce-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b8ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b8ce-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3b8ce-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3b8ce-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="3b8ce-108">[in]TypeDef 的權杖類型來列舉其方法實作。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="3b8ce-109">[out]要儲存的 MethodBody 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="3b8ce-110">[out]要儲存 MethodDeclaration 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3b8ce-111">[in]大小上限`rMethodBody`和`rMethodDecl`陣列。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3b8ce-112">[in]方法中傳回的實際數目`rMethodBody`和`rMethodDecl`。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b8ce-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="3b8ce-113">Return Value</span></span>  
  
|<span data-ttu-id="3b8ce-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b8ce-114">HRESULT</span></span>|<span data-ttu-id="3b8ce-115">描述</span><span class="sxs-lookup"><span data-stu-id="3b8ce-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3b8ce-116">`EnumMethodImpls` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3b8ce-117">沒有方法語彙基元來列舉。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="3b8ce-118">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b8ce-119">需求</span><span class="sxs-lookup"><span data-stu-id="3b8ce-119">Requirements</span></span>  
 <span data-ttu-id="3b8ce-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b8ce-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b8ce-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3b8ce-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b8ce-122">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3b8ce-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b8ce-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b8ce-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b8ce-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b8ce-124">See also</span></span>
- [<span data-ttu-id="3b8ce-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3b8ce-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3b8ce-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3b8ce-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
