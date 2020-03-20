---
title: IMetaDataEmit::DefineNestedType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175807"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="3744d-102">IMetaDataEmit::DefineNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="3744d-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="3744d-103">創建類型定義的中繼資料簽名，返回該類型的`mdTypeDef`權杖，並指定定義的類型是`tdEncloser`參數引用的類型的成員。</span><span class="sxs-lookup"><span data-stu-id="3744d-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3744d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3744d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3744d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3744d-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="3744d-106">[在]Unicode 中類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="3744d-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="3744d-107">[在]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="3744d-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="3744d-108">這是值的`CorTypeAttr`位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="3744d-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="3744d-109">[在]基類的權杖。</span><span class="sxs-lookup"><span data-stu-id="3744d-109">[in] The token of the base class.</span></span> <span data-ttu-id="3744d-110">這是 或`mdTypeDef``mdTypeRef`標記。</span><span class="sxs-lookup"><span data-stu-id="3744d-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="3744d-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="3744d-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="3744d-112">[在]指定此類或介面實現的介面的權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="3744d-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="3744d-113">[在]封閉類型的標記。</span><span class="sxs-lookup"><span data-stu-id="3744d-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="3744d-114">陣列的最後一個元素必須是`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="3744d-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="3744d-115">[出]分配的`mdTypeDef`權杖。</span><span class="sxs-lookup"><span data-stu-id="3744d-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3744d-116">需求</span><span class="sxs-lookup"><span data-stu-id="3744d-116">Requirements</span></span>  
 <span data-ttu-id="3744d-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3744d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3744d-118">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="3744d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3744d-119">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3744d-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3744d-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3744d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3744d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3744d-121">See also</span></span>

- [<span data-ttu-id="3744d-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3744d-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3744d-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3744d-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
