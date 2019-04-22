---
title: IMetaDataEmit::SetPropertyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdee8491b22675fb8dd8fa89e77ebf8541185173
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207887"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="0e623-102">IMetaDataEmit::SetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="0e623-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="0e623-103">設定儲存在先前呼叫所定義之屬性的中繼資料的功能[DefineProperty 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0e623-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e623-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e623-104">Syntax</span></span>  
  
```  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e623-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e623-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="0e623-106">[in]若要變更屬性的語彙基元</span><span class="sxs-lookup"><span data-stu-id="0e623-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="0e623-107">[in]屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="0e623-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="0e623-108">[in]屬性的預設值的型別。</span><span class="sxs-lookup"><span data-stu-id="0e623-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0e623-109">[in]屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="0e623-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="0e623-110">[in]中的字元 (Unicode) 的計數`pValue`。</span><span class="sxs-lookup"><span data-stu-id="0e623-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="0e623-111">[in]設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="0e623-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="0e623-112">[in]取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="0e623-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="0e623-113">[in]其他方法與屬性相關聯的陣列。</span><span class="sxs-lookup"><span data-stu-id="0e623-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="0e623-114">終止此陣列`mdTokenNil`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0e623-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e623-115">需求</span><span class="sxs-lookup"><span data-stu-id="0e623-115">Requirements</span></span>  
 <span data-ttu-id="0e623-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e623-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e623-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e623-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e623-118">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0e623-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e623-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e623-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e623-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e623-120">See also</span></span>

- [<span data-ttu-id="0e623-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0e623-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0e623-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0e623-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
