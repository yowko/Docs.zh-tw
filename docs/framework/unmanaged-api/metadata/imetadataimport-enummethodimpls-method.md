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
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175469"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="bc431-102">IMetaDataImport::EnumMethodImpls 方法</span><span class="sxs-lookup"><span data-stu-id="bc431-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="bc431-103">列舉代表指定類型方法的 MethodBody 和 MethodDeclaration 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="bc431-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc431-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc431-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bc431-105">參數</span><span class="sxs-lookup"><span data-stu-id="bc431-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bc431-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="bc431-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bc431-107">對於此方法的第一次調用，這必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="bc431-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="bc431-108">[在]方法要枚舉的類型的類型的 TypeDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="bc431-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="bc431-109">[出]要存儲方法體權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="bc431-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="bc431-110">[出]要存儲方法聲明權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="bc431-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bc431-111">[在]`rMethodBody`和`rMethodDecl`陣列的最大大小。</span><span class="sxs-lookup"><span data-stu-id="bc431-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bc431-112">[在]在 和`rMethodBody``rMethodDecl`中返回的實際方法數。</span><span class="sxs-lookup"><span data-stu-id="bc431-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc431-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc431-113">Return Value</span></span>  
  
|<span data-ttu-id="bc431-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc431-114">HRESULT</span></span>|<span data-ttu-id="bc431-115">描述</span><span class="sxs-lookup"><span data-stu-id="bc431-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bc431-116">`EnumMethodImpls`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="bc431-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bc431-117">沒有要枚舉的方法權杖。</span><span class="sxs-lookup"><span data-stu-id="bc431-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="bc431-118">在這種情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="bc431-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc431-119">需求</span><span class="sxs-lookup"><span data-stu-id="bc431-119">Requirements</span></span>  
 <span data-ttu-id="bc431-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc431-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc431-121">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="bc431-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc431-122">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="bc431-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc431-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc431-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc431-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc431-124">See also</span></span>

- [<span data-ttu-id="bc431-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="bc431-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bc431-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="bc431-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
