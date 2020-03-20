---
title: IMetaDataImport::EnumFieldsWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177346"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="e7adf-102">IMetaDataImport::EnumFieldsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="e7adf-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="e7adf-103">列舉具有指定名稱之指定類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e7adf-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7adf-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7adf-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7adf-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7adf-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e7adf-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="e7adf-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="e7adf-107">[在]要枚舉其欄位的類型的權杖。</span><span class="sxs-lookup"><span data-stu-id="e7adf-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="e7adf-108">[在]限制枚舉範圍的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="e7adf-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="e7adf-109">[出]用於存儲 FieldDef 權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="e7adf-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e7adf-110">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="e7adf-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e7adf-111">[出]在 中`rFields`返回的實際欄位Def 權杖數。</span><span class="sxs-lookup"><span data-stu-id="e7adf-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7adf-112">備註</span><span class="sxs-lookup"><span data-stu-id="e7adf-112">Remarks</span></span>  
 <span data-ttu-id="e7adf-113">與[IMetaDataImport：：enumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)不同，`EnumFieldsWithName`則丟棄所有沒有指定名稱的欄位權杖。</span><span class="sxs-lookup"><span data-stu-id="e7adf-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7adf-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="e7adf-114">Return Value</span></span>  
  
|<span data-ttu-id="e7adf-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7adf-115">HRESULT</span></span>|<span data-ttu-id="e7adf-116">描述</span><span class="sxs-lookup"><span data-stu-id="e7adf-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e7adf-117">`EnumFieldsWithName`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="e7adf-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e7adf-118">沒有要枚舉的欄位。</span><span class="sxs-lookup"><span data-stu-id="e7adf-118">There are no fields to enumerate.</span></span> <span data-ttu-id="e7adf-119">在這種情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="e7adf-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7adf-120">需求</span><span class="sxs-lookup"><span data-stu-id="e7adf-120">Requirements</span></span>  
 <span data-ttu-id="e7adf-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7adf-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7adf-122">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="e7adf-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7adf-123">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e7adf-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7adf-124">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7adf-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7adf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7adf-125">See also</span></span>

- [<span data-ttu-id="e7adf-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e7adf-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e7adf-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e7adf-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
