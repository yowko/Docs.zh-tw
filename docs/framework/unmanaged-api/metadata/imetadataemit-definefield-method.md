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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177707"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="023a0-102">IMetaDataEmit::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="023a0-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="023a0-103">為具有指定中繼資料簽名的欄位創建定義，並獲取該欄位定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="023a0-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="023a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="023a0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="023a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="023a0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="023a0-106">[在]封閉`mdTypeDef`類或介面的權杖。</span><span class="sxs-lookup"><span data-stu-id="023a0-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="023a0-107">[在]Unicode 中的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="023a0-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="023a0-108">[在]欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="023a0-108">[in] The field attributes.</span></span> <span data-ttu-id="023a0-109">這是值的`CorFieldAttr`位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="023a0-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="023a0-110">[在]欄位簽名作為 BLOB。</span><span class="sxs-lookup"><span data-stu-id="023a0-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="023a0-111">[在]中的`pvSigBlob`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="023a0-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="023a0-112">[在]常`ELEMENT_TYPE_`*\** 量值的 。</span><span class="sxs-lookup"><span data-stu-id="023a0-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="023a0-113">這是一個`CorElementType`值。</span><span class="sxs-lookup"><span data-stu-id="023a0-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="023a0-114">如果未為欄位定義常量值，請使用`ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="023a0-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="023a0-115">[在]欄位的常量值。</span><span class="sxs-lookup"><span data-stu-id="023a0-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="023a0-116">[在]的大小（Unicode）字元。 `pValue`</span><span class="sxs-lookup"><span data-stu-id="023a0-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="023a0-117">[出]分配的`mdFieldDef`權杖。</span><span class="sxs-lookup"><span data-stu-id="023a0-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="023a0-118">需求</span><span class="sxs-lookup"><span data-stu-id="023a0-118">Requirements</span></span>  
 <span data-ttu-id="023a0-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="023a0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="023a0-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="023a0-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="023a0-121">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="023a0-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="023a0-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="023a0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023a0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="023a0-123">See also</span></span>

- [<span data-ttu-id="023a0-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="023a0-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="023a0-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="023a0-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
