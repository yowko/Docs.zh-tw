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
ms.openlocfilehash: b8be30e8c3b6bc7c03ede5f897f176e04153003b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781970"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="74528-102">IMetaDataImport::EnumMethodImpls 方法</span><span class="sxs-lookup"><span data-stu-id="74528-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="74528-103">列舉代表指定類型方法的 MethodBody 和 MethodDeclaration 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="74528-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74528-104">語法</span><span class="sxs-lookup"><span data-stu-id="74528-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74528-105">參數</span><span class="sxs-lookup"><span data-stu-id="74528-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="74528-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="74528-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="74528-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="74528-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="74528-108">[in]TypeDef 的權杖類型來列舉其方法實作。</span><span class="sxs-lookup"><span data-stu-id="74528-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="74528-109">[out]要儲存的 MethodBody 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="74528-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="74528-110">[out]要儲存 MethodDeclaration 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="74528-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="74528-111">[in]大小上限`rMethodBody`和`rMethodDecl`陣列。</span><span class="sxs-lookup"><span data-stu-id="74528-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="74528-112">[in]方法中傳回的實際數目`rMethodBody`和`rMethodDecl`。</span><span class="sxs-lookup"><span data-stu-id="74528-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74528-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="74528-113">Return Value</span></span>  
  
|<span data-ttu-id="74528-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74528-114">HRESULT</span></span>|<span data-ttu-id="74528-115">描述</span><span class="sxs-lookup"><span data-stu-id="74528-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="74528-116">`EnumMethodImpls` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="74528-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="74528-117">沒有方法語彙基元來列舉。</span><span class="sxs-lookup"><span data-stu-id="74528-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="74528-118">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="74528-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74528-119">需求</span><span class="sxs-lookup"><span data-stu-id="74528-119">Requirements</span></span>  
 <span data-ttu-id="74528-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74528-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74528-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74528-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74528-122">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="74528-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74528-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74528-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74528-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74528-124">See also</span></span>

- [<span data-ttu-id="74528-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="74528-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="74528-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="74528-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
