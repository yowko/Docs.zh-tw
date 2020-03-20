---
title: IMetaDataEmit::SetTypeDefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177468"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="5dbf8-102">IMetaDataEmit::SetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="5dbf8-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="5dbf8-103">設置以前調用[IMetaDataEmit：:DefineTypeDef）](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)定義的類型的功能。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dbf8-104">語法</span><span class="sxs-lookup"><span data-stu-id="5dbf8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dbf8-105">參數</span><span class="sxs-lookup"><span data-stu-id="5dbf8-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5dbf8-106">[在]從`mdTypeDef`原始調用[IMetaDataEmit 獲得權杖：:DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="5dbf8-107">[在]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="5dbf8-108">這是值的`CorTypeAttr`位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="5dbf8-109">[在]基`mdToken`類的 。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="5dbf8-110">從之前對[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)的調用中獲取：:Define`null`導入類型，或 。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="5dbf8-111">[在]此類型實現的介面的權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="5dbf8-112">這些`mdTypeRef`權杖是使用[IMetaDataEmit：:Define 導入類型](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)獲得的。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="5dbf8-113">陣列的最後一個元素必須是`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dbf8-114">需求</span><span class="sxs-lookup"><span data-stu-id="5dbf8-114">Requirements</span></span>  
 <span data-ttu-id="5dbf8-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbf8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dbf8-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="5dbf8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5dbf8-117">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5dbf8-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5dbf8-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dbf8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dbf8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dbf8-119">See also</span></span>

- [<span data-ttu-id="5dbf8-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5dbf8-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5dbf8-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="5dbf8-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
