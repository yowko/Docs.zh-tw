---
title: "IMetaDataEmit::DefineNestedType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineNestedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99250d98f9ffd90857128aa5d8a675a997926bf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="a7ba2-102">IMetaDataEmit::DefineNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="a7ba2-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="a7ba2-103">建立類型定義的中繼資料簽章、 傳回`mdTypeDef`權杖該類型，然後將其指定定義的類型為所參考的類型成員`tdEncloser`參數。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ba2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7ba2-104">Syntax</span></span>  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7ba2-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7ba2-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="a7ba2-106">[in]以 Unicode 的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="a7ba2-107">[in]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="a7ba2-108">這是位元遮罩`CorTypeAttr`值。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="a7ba2-109">[in]基底類別的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-109">[in] The token of the base class.</span></span> <span data-ttu-id="a7ba2-110">這可能是`mdTypeDef`或`mdTypeRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="a7ba2-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="a7ba2-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="a7ba2-112">[in]指定此類別或介面實作的介面的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="a7ba2-113">[in]封入類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="a7ba2-114">陣列的最後一個元素必須是`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="a7ba2-115">[out]`mdTypeDef`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ba2-116">需求</span><span class="sxs-lookup"><span data-stu-id="a7ba2-116">Requirements</span></span>  
 <span data-ttu-id="a7ba2-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7ba2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ba2-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7ba2-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7ba2-119">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a7ba2-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7ba2-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ba2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ba2-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7ba2-121">See Also</span></span>  
 [<span data-ttu-id="a7ba2-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a7ba2-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a7ba2-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a7ba2-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
