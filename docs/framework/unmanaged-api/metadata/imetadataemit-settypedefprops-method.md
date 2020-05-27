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
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007763"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="d8b41-102">IMetaDataEmit::SetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="d8b41-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="d8b41-103">設定先前呼叫 IMetaDataEmit 所定義之類型的功能[：:D efinetypedef](imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b41-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b41-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8b41-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8b41-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8b41-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d8b41-106">在`mdTypeDef`從原始呼叫中取得的權杖[IMetaDataEmit：:D efinetypedef](imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b41-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="d8b41-107">[in] `TypeDef`特性.</span><span class="sxs-lookup"><span data-stu-id="d8b41-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="d8b41-108">這是值的位元遮罩 `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="d8b41-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="d8b41-109">在`mdToken`基類的。</span><span class="sxs-lookup"><span data-stu-id="d8b41-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="d8b41-110">從先前的 IMetaDataEmit 呼叫取得[：:D efineimporttype](imetadataemit-defineimporttype-method.md)，或 `null` 。</span><span class="sxs-lookup"><span data-stu-id="d8b41-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="d8b41-111">在這個類型所執行介面的權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="d8b41-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="d8b41-112">這些 `mdTypeRef` 權杖是使用[IMetaDataEmit：:D efineimporttype](imetadataemit-defineimporttype-method.md)取得。</span><span class="sxs-lookup"><span data-stu-id="d8b41-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="d8b41-113">陣列的最後一個元素必須是 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="d8b41-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8b41-114">需求</span><span class="sxs-lookup"><span data-stu-id="d8b41-114">Requirements</span></span>  
 <span data-ttu-id="d8b41-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b41-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b41-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d8b41-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8b41-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d8b41-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8b41-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8b41-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b41-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8b41-119">See also</span></span>

- [<span data-ttu-id="d8b41-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d8b41-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d8b41-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d8b41-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
