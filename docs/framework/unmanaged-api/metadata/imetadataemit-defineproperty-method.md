---
title: "IMetaDataEmit::DefineProperty 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineProperty
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc0403fd51f028510eb60d93ff96fc7d05606366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="69410-102">IMetaDataEmit::DefineProperty 方法</span><span class="sxs-lookup"><span data-stu-id="69410-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="69410-103">建立指定類型的屬性定義具有指定`get`和`set`方法存取子，並取得該屬性定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="69410-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69410-104">語法</span><span class="sxs-lookup"><span data-stu-id="69410-104">Syntax</span></span>  
  
```  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69410-105">參數</span><span class="sxs-lookup"><span data-stu-id="69410-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="69410-106">[in]類別或介面定義屬性之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="69410-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="69410-107">[in]屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="69410-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="69410-108">[in]屬性的旗標。</span><span class="sxs-lookup"><span data-stu-id="69410-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="69410-109">[in]屬性的簽章。</span><span class="sxs-lookup"><span data-stu-id="69410-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="69410-110">[in]中的位元組計數`pvSig`。</span><span class="sxs-lookup"><span data-stu-id="69410-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="69410-111">[in]屬性的預設值的類型。</span><span class="sxs-lookup"><span data-stu-id="69410-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="69410-112">[in]屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="69410-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="69410-113">[in]中的字元 (Unicode) 的計數`pValue`。</span><span class="sxs-lookup"><span data-stu-id="69410-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="69410-114">[in]所設定的屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="69410-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="69410-115">[in]取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="69410-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="69410-116">[in]其他方法與屬性相關聯的陣列。</span><span class="sxs-lookup"><span data-stu-id="69410-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="69410-117">終止與陣列`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="69410-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="69410-118">[out]`mdProperty`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="69410-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69410-119">需求</span><span class="sxs-lookup"><span data-stu-id="69410-119">Requirements</span></span>  
 <span data-ttu-id="69410-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69410-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69410-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="69410-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69410-122">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="69410-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69410-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69410-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69410-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69410-124">See Also</span></span>  
 [<span data-ttu-id="69410-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="69410-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="69410-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="69410-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
