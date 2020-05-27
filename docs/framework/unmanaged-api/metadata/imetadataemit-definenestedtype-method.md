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
ms.openlocfilehash: 2b24c2ca6907dfdb63ad934ec30557c246db174c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004350"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="c74d6-102">IMetaDataEmit::DefineNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="c74d6-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="c74d6-103">建立類型定義的中繼資料簽章、傳回 `mdTypeDef` 該類型的 token，並指定定義的類型是參數所參考之類型的成員 `tdEncloser` 。</span><span class="sxs-lookup"><span data-stu-id="c74d6-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c74d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c74d6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c74d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="c74d6-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="c74d6-106">在Unicode 中的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="c74d6-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="c74d6-107">[in] `TypeDef`特性.</span><span class="sxs-lookup"><span data-stu-id="c74d6-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="c74d6-108">這是值的位元遮罩 `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="c74d6-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="c74d6-109">在基類的 token。</span><span class="sxs-lookup"><span data-stu-id="c74d6-109">[in] The token of the base class.</span></span> <span data-ttu-id="c74d6-110">這可能是 `mdTypeDef` 或 `mdTypeRef` 權杖。</span><span class="sxs-lookup"><span data-stu-id="c74d6-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="c74d6-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="c74d6-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="c74d6-112">在權杖的陣列，指定此類別或介面所執行的介面。</span><span class="sxs-lookup"><span data-stu-id="c74d6-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="c74d6-113">在封入類型的 token。</span><span class="sxs-lookup"><span data-stu-id="c74d6-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="c74d6-114">陣列的最後一個元素必須是 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="c74d6-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="c74d6-115">脫銷`mdTypeDef`指派的 token。</span><span class="sxs-lookup"><span data-stu-id="c74d6-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c74d6-116">需求</span><span class="sxs-lookup"><span data-stu-id="c74d6-116">Requirements</span></span>  
 <span data-ttu-id="c74d6-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c74d6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c74d6-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c74d6-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c74d6-119">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c74d6-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c74d6-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c74d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74d6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c74d6-121">See also</span></span>

- [<span data-ttu-id="c74d6-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c74d6-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c74d6-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c74d6-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
