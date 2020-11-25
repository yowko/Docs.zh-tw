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
ms.openlocfilehash: 99dc141cca0f911c8dd65645f6c22d950cc678d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719537"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="6b34b-102">IMetaDataEmit::DefineNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="6b34b-102">IMetaDataEmit::DefineNestedType Method</span></span>

<span data-ttu-id="6b34b-103">建立類型定義的中繼資料簽章、傳回 `mdTypeDef` 該類型的標記，並指定定義的類型是參數所參考之類型的成員 `tdEncloser` 。</span><span class="sxs-lookup"><span data-stu-id="6b34b-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b34b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b34b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6b34b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b34b-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="6b34b-106">在Unicode 的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6b34b-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="6b34b-107">[in] `TypeDef` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b34b-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="6b34b-108">這是值的位元遮罩 `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="6b34b-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="6b34b-109">在基類的 token。</span><span class="sxs-lookup"><span data-stu-id="6b34b-109">[in] The token of the base class.</span></span> <span data-ttu-id="6b34b-110">這可能是 `mdTypeDef` 或 `mdTypeRef` 標記。</span><span class="sxs-lookup"><span data-stu-id="6b34b-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="6b34b-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="6b34b-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="6b34b-112">在Token 的陣列，這個陣列會指定這個類別或介面所執行的介面。</span><span class="sxs-lookup"><span data-stu-id="6b34b-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="6b34b-113">在封入類型的標記。</span><span class="sxs-lookup"><span data-stu-id="6b34b-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="6b34b-114">陣列的最後一個元素必須是 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="6b34b-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="6b34b-115">擴展 `mdTypeDef` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="6b34b-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b34b-116">需求</span><span class="sxs-lookup"><span data-stu-id="6b34b-116">Requirements</span></span>  

 <span data-ttu-id="6b34b-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b34b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b34b-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6b34b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b34b-119">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6b34b-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b34b-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b34b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b34b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b34b-121">See also</span></span>

- [<span data-ttu-id="6b34b-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6b34b-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6b34b-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6b34b-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
