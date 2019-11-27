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
ms.openlocfilehash: 3ab29fc8c983b354ad5088d26c547868940ec70a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447724"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="5d482-102">IMetaDataEmit::SetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="5d482-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="5d482-103">設定先前呼叫 IMetaDataEmit 所定義之類型的功能[：:D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5d482-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d482-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d482-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d482-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d482-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5d482-106">在從原始呼叫 IMetaDataEmit 取得的 `mdTypeDef` token [：:D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5d482-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="5d482-107">[in] `TypeDef` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5d482-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="5d482-108">這是 `CorTypeAttr` 值的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="5d482-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="5d482-109">在基類的 `mdToken`。</span><span class="sxs-lookup"><span data-stu-id="5d482-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="5d482-110">從先前的 IMetaDataEmit 呼叫取得[：:D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)，或 `null`。</span><span class="sxs-lookup"><span data-stu-id="5d482-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="5d482-111">在這個類型所執行介面的權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="5d482-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="5d482-112">這些 `mdTypeRef` 權杖是使用[IMetaDataEmit：:D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)取得。</span><span class="sxs-lookup"><span data-stu-id="5d482-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="5d482-113">陣列的最後一個元素必須 `mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="5d482-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d482-114">需求</span><span class="sxs-lookup"><span data-stu-id="5d482-114">Requirements</span></span>  
 <span data-ttu-id="5d482-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d482-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d482-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5d482-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d482-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5d482-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d482-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d482-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d482-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d482-119">See also</span></span>

- [<span data-ttu-id="5d482-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5d482-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5d482-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="5d482-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
