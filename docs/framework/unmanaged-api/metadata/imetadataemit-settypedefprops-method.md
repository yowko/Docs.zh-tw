---
title: "IMetaDataEmit::SetTypeDefProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50f92d0ff307621695887ee7a0af2d4d19985f51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="6c87b-102">IMetaDataEmit::SetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="6c87b-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="6c87b-103">設定由先前呼叫所定義之類型的功能[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6c87b-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c87b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c87b-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c87b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c87b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6c87b-106">[in]`mdTypeDef`語彙基元取自原始呼叫[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6c87b-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="6c87b-107">[in]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="6c87b-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="6c87b-108">這是位元遮罩`CorTypeAttr`值。</span><span class="sxs-lookup"><span data-stu-id="6c87b-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="6c87b-109">[in]`mdToken`基底類別。</span><span class="sxs-lookup"><span data-stu-id="6c87b-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="6c87b-110">取自先前呼叫[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)，或`null`。</span><span class="sxs-lookup"><span data-stu-id="6c87b-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="6c87b-111">[in]這個類型所實作之介面的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="6c87b-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="6c87b-112">這些`mdTypeRef`使用取得語彙基元[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6c87b-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="6c87b-113">陣列的最後一個項目，則必須是`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="6c87b-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c87b-114">需求</span><span class="sxs-lookup"><span data-stu-id="6c87b-114">Requirements</span></span>  
 <span data-ttu-id="6c87b-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c87b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c87b-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6c87b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c87b-117">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6c87b-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c87b-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c87b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c87b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c87b-119">See Also</span></span>  
 [<span data-ttu-id="6c87b-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6c87b-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6c87b-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6c87b-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
