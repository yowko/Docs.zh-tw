---
title: IMetaDataEmit::DefineTypeDef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175755"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="5b8c2-102">IMetaDataEmit::DefineTypeDef 方法</span><span class="sxs-lookup"><span data-stu-id="5b8c2-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="5b8c2-103">為通用語言運行時類型創建類型定義，並獲取該類型定義的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b8c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b8c2-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b8c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b8c2-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="5b8c2-106">[在]Unicode 中類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="5b8c2-107">[在]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="5b8c2-108">這是值的`CoreTypeAttr`位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="5b8c2-109">[在]基類的權杖。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-109">[in] The token of the base class.</span></span> <span data-ttu-id="5b8c2-110">它必須是 或`mdTypeDef``mdTypeRef`標記。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="5b8c2-111">[在]指定此類或介面實現的介面的權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5b8c2-112">[出]分配的`mdTypeDef`權杖。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b8c2-113">備註</span><span class="sxs-lookup"><span data-stu-id="5b8c2-113">Remarks</span></span>  
 <span data-ttu-id="5b8c2-114">中`dwTypeDefFlags`的標誌指定正在創建的類型是公共類型系統參考型別（類或介面）還是公共類型系統數值型別。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="5b8c2-115">根據提供的參數，此方法作為副作用，還可以為此類型繼承或實現的每個介面創建`mdInterfaceImpl`記錄。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="5b8c2-116">但是，此方法不會返回任何這些`mdInterfaceImpl`權杖。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="5b8c2-117">如果用戶端希望以後添加或修改`mdInterfaceImpl`權杖，則必須使用介面`IMetaDataImport`枚舉它們。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="5b8c2-118">如果要使用介面的`[default]`COM 語義，則應將預設介面作為`rtkImplements`中的第一個元素提供 。類上的自訂屬性集將指示類具有預設介面（始終假定該介面是為類聲明的第一個`mdInterfaceImpl`權杖）。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="5b8c2-119">`rtkImplements`陣列的每個元素都包含 或`mdTypeDef``mdTypeRef`權杖。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="5b8c2-120">陣列中的最後一個元素必須為`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b8c2-121">需求</span><span class="sxs-lookup"><span data-stu-id="5b8c2-121">Requirements</span></span>  
 <span data-ttu-id="5b8c2-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b8c2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b8c2-123">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="5b8c2-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b8c2-124">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5b8c2-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b8c2-125">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b8c2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8c2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b8c2-126">See also</span></span>

- [<span data-ttu-id="5b8c2-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5b8c2-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5b8c2-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="5b8c2-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
