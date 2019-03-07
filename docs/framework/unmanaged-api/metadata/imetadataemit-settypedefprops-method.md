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
ms.openlocfilehash: ddb40c3265b3f42514d9dbd6f620a783089a4fad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481170"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="89942-102">IMetaDataEmit::SetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="89942-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="89942-103">設定功能的先前呼叫所定義的型別[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="89942-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89942-104">語法</span><span class="sxs-lookup"><span data-stu-id="89942-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89942-105">參數</span><span class="sxs-lookup"><span data-stu-id="89942-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="89942-106">[in]`mdTypeDef`取自原始呼叫的語彙基元[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="89942-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="89942-107">[in]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="89942-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="89942-108">這是位元遮罩`CorTypeAttr`值。</span><span class="sxs-lookup"><span data-stu-id="89942-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="89942-109">[in]`mdToken`基底類別。</span><span class="sxs-lookup"><span data-stu-id="89942-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="89942-110">從先前呼叫中取得[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)，或`null`。</span><span class="sxs-lookup"><span data-stu-id="89942-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="89942-111">[in]這個類型所實作之介面的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="89942-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="89942-112">這些`mdTypeRef`使用取得語彙基元[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="89942-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="89942-113">陣列的最後一個項目必須是`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="89942-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89942-114">需求</span><span class="sxs-lookup"><span data-stu-id="89942-114">Requirements</span></span>  
 <span data-ttu-id="89942-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89942-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89942-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="89942-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89942-117">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="89942-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89942-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89942-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89942-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89942-119">See also</span></span>
- [<span data-ttu-id="89942-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="89942-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="89942-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="89942-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
