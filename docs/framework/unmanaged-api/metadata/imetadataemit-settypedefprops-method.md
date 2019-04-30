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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596888a8eb4a55c4cfe594b1911f17f6d32f56d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992429"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="c3e6e-102">IMetaDataEmit::SetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="c3e6e-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="c3e6e-103">設定功能的先前呼叫所定義的型別[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3e6e-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3e6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3e6e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c3e6e-106">[in]`mdTypeDef`取自原始呼叫的語彙基元[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="c3e6e-107">[in]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="c3e6e-108">這是位元遮罩`CorTypeAttr`值。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="c3e6e-109">[in]`mdToken`基底類別。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="c3e6e-110">從先前呼叫中取得[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)，或`null`。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="c3e6e-111">[in]這個類型所實作之介面的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="c3e6e-112">這些`mdTypeRef`使用取得語彙基元[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="c3e6e-113">陣列的最後一個項目必須是`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e6e-114">需求</span><span class="sxs-lookup"><span data-stu-id="c3e6e-114">Requirements</span></span>  
 <span data-ttu-id="c3e6e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3e6e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3e6e-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3e6e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3e6e-117">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c3e6e-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3e6e-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3e6e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e6e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3e6e-119">See also</span></span>

- [<span data-ttu-id="c3e6e-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c3e6e-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c3e6e-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c3e6e-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
