---
title: "IMetaDataImport::EnumFieldsWithName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumFieldsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77b5ba7e191d9aa0f1587e4ac1ec25e655c27b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="e8960-102">IMetaDataImport::EnumFieldsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="e8960-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="e8960-103">列舉具有指定名稱之指定類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e8960-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8960-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8960-104">Syntax</span></span>  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8960-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8960-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e8960-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="e8960-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="e8960-107">[in]要列舉其欄位的類型語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e8960-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="e8960-108">[in]列舉的範圍限制的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="e8960-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="e8960-109">[out]用來儲存 fielddef 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="e8960-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e8960-110">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="e8960-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e8960-111">[out]Fielddef 語彙基元中傳回的實際數目`rFields`。</span><span class="sxs-lookup"><span data-stu-id="e8960-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8960-112">備註</span><span class="sxs-lookup"><span data-stu-id="e8960-112">Remarks</span></span>  
 <span data-ttu-id="e8960-113">不同於[imetadataimport:: Enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)，`EnumFieldsWithName`會捨棄所有不具有指定的名稱的欄位語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e8960-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8960-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="e8960-114">Return Value</span></span>  
  
|<span data-ttu-id="e8960-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8960-115">HRESULT</span></span>|<span data-ttu-id="e8960-116">描述</span><span class="sxs-lookup"><span data-stu-id="e8960-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e8960-117">`EnumFieldsWithName`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e8960-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e8960-118">沒有要列舉的欄位。</span><span class="sxs-lookup"><span data-stu-id="e8960-118">There are no fields to enumerate.</span></span> <span data-ttu-id="e8960-119">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="e8960-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8960-120">需求</span><span class="sxs-lookup"><span data-stu-id="e8960-120">Requirements</span></span>  
 <span data-ttu-id="e8960-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8960-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8960-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e8960-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8960-123">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e8960-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8960-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8960-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8960-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8960-125">See Also</span></span>  
 [<span data-ttu-id="e8960-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e8960-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e8960-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e8960-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
