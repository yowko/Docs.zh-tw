---
title: IMetaDataEmit::DefineField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8ba8a762c56a666c67b25b9ce0420099fce419a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223520"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="293f2-102">IMetaDataEmit::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="293f2-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="293f2-103">建立欄位的定義，具有指定之中繼資料簽章，並取得該欄位定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="293f2-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="293f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="293f2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="293f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="293f2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="293f2-106">[in]`mdTypeDef`封入類別或介面的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="293f2-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="293f2-107">[in]以 Unicode 欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="293f2-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="293f2-108">[in]欄位的欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="293f2-108">[in] The field attributes.</span></span> <span data-ttu-id="293f2-109">這是位元遮罩`CorFieldAttr`值。</span><span class="sxs-lookup"><span data-stu-id="293f2-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="293f2-110">[in]為 BLOB 欄位簽章。</span><span class="sxs-lookup"><span data-stu-id="293f2-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="293f2-111">[in]中的位元組計數`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="293f2-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="293f2-112">[in]`ELEMENT_TYPE_` *\** 常數的值。</span><span class="sxs-lookup"><span data-stu-id="293f2-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="293f2-113">這是`CorElementType`值。</span><span class="sxs-lookup"><span data-stu-id="293f2-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="293f2-114">如果未定義欄位的常數值，使用`ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="293f2-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="293f2-115">[in]欄位的常值。</span><span class="sxs-lookup"><span data-stu-id="293f2-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="293f2-116">[in](Unicode) 字元的大小`pValue`。</span><span class="sxs-lookup"><span data-stu-id="293f2-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="293f2-117">[out]`mdFieldDef`指派權杖。</span><span class="sxs-lookup"><span data-stu-id="293f2-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="293f2-118">需求</span><span class="sxs-lookup"><span data-stu-id="293f2-118">Requirements</span></span>  
 <span data-ttu-id="293f2-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="293f2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="293f2-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="293f2-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="293f2-121">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="293f2-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="293f2-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="293f2-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="293f2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="293f2-123">See also</span></span>

- [<span data-ttu-id="293f2-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="293f2-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="293f2-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="293f2-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
