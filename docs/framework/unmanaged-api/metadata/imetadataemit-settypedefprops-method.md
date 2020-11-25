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
ms.openlocfilehash: 2f572f66f16ff701350fde3b05be822b9e8c78b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706823"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="cce5b-102">IMetaDataEmit::SetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="cce5b-102">IMetaDataEmit::SetTypeDefProps Method</span></span>

<span data-ttu-id="cce5b-103">設定由先前呼叫 IMetaDataEmit 所定義之類型的功能 [：:D efinetypedef](imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="cce5b-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="cce5b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cce5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="cce5b-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="cce5b-106">在 `mdTypeDef` 從原始呼叫 [IMetaDataEmit：:D efinetypedef](imetadataemit-definetypedef-method.md)取得的權杖。</span><span class="sxs-lookup"><span data-stu-id="cce5b-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="cce5b-107">[in] `TypeDef` 屬性。</span><span class="sxs-lookup"><span data-stu-id="cce5b-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="cce5b-108">這是值的位元遮罩 `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="cce5b-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="cce5b-109">在 `mdToken` 基底類別的。</span><span class="sxs-lookup"><span data-stu-id="cce5b-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="cce5b-110">從先前對 IMetaDataEmit 的呼叫取得 [：:D efineimporttype](imetadataemit-defineimporttype-method.md)或 `null` 。</span><span class="sxs-lookup"><span data-stu-id="cce5b-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="cce5b-111">在這個型別所實行介面的標記陣列。</span><span class="sxs-lookup"><span data-stu-id="cce5b-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="cce5b-112">這些 `mdTypeRef` 權杖是使用 [IMetaDataEmit：:D efineimporttype](imetadataemit-defineimporttype-method.md)取得的。</span><span class="sxs-lookup"><span data-stu-id="cce5b-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="cce5b-113">陣列的最後一個元素必須是 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="cce5b-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce5b-114">需求</span><span class="sxs-lookup"><span data-stu-id="cce5b-114">Requirements</span></span>  

 <span data-ttu-id="cce5b-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cce5b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cce5b-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="cce5b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cce5b-117">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="cce5b-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cce5b-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cce5b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce5b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cce5b-119">See also</span></span>

- [<span data-ttu-id="cce5b-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="cce5b-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="cce5b-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="cce5b-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
