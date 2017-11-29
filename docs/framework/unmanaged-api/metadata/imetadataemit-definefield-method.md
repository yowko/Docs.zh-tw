---
title: "IMetaDataEmit::DefineField 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2a544d7e676b71fb00b8fd7a3d871867f7f55626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="58bbe-102">IMetaDataEmit::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="58bbe-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="58bbe-103">建立欄位的定義，與指定的中繼資料簽章，並取得該欄位定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="58bbe-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58bbe-104">語法</span><span class="sxs-lookup"><span data-stu-id="58bbe-104">Syntax</span></span>  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58bbe-105">參數</span><span class="sxs-lookup"><span data-stu-id="58bbe-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="58bbe-106">[in]`mdTypeDef`權杖封入類別或介面。</span><span class="sxs-lookup"><span data-stu-id="58bbe-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="58bbe-107">[in]以 Unicode 欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="58bbe-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="58bbe-108">[in]欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="58bbe-108">[in] The field attributes.</span></span> <span data-ttu-id="58bbe-109">這是位元遮罩`CorFieldAttr`值。</span><span class="sxs-lookup"><span data-stu-id="58bbe-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="58bbe-110">[in]欄位簽章為 BLOB。</span><span class="sxs-lookup"><span data-stu-id="58bbe-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="58bbe-111">[in]中的位元組計數`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="58bbe-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="58bbe-112">[in]`ELEMENT_TYPE_`  *\** 常數的值。</span><span class="sxs-lookup"><span data-stu-id="58bbe-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="58bbe-113">這是`CorElementType`值。</span><span class="sxs-lookup"><span data-stu-id="58bbe-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="58bbe-114">如果未定義欄位的常數值，使用`ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="58bbe-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="58bbe-115">[in]欄位的常值。</span><span class="sxs-lookup"><span data-stu-id="58bbe-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="58bbe-116">[in]以 (Unicode) 字元為單位的大小`pValue`。</span><span class="sxs-lookup"><span data-stu-id="58bbe-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="58bbe-117">[out]`mdFieldDef`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="58bbe-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58bbe-118">需求</span><span class="sxs-lookup"><span data-stu-id="58bbe-118">Requirements</span></span>  
 <span data-ttu-id="58bbe-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58bbe-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58bbe-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58bbe-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58bbe-121">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="58bbe-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58bbe-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58bbe-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bbe-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58bbe-123">See Also</span></span>  
 [<span data-ttu-id="58bbe-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="58bbe-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="58bbe-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="58bbe-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
