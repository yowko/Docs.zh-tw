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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf624695136a9397937f05b28dec18493c8e12d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042701"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="f7384-102">IMetaDataImport::EnumFieldsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="f7384-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="f7384-103">列舉具有指定名稱之指定類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f7384-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7384-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7384-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f7384-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7384-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f7384-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="f7384-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="f7384-107">[in]其欄位是列舉型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="f7384-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="f7384-108">[in]列舉的範圍限制欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="f7384-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="f7384-109">[out]用來儲存 fielddef 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="f7384-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f7384-110">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="f7384-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f7384-111">[out]中傳回的 fielddef 語彙基元的實際數目`rFields`。</span><span class="sxs-lookup"><span data-stu-id="f7384-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7384-112">備註</span><span class="sxs-lookup"><span data-stu-id="f7384-112">Remarks</span></span>  
 <span data-ttu-id="f7384-113">不同於[imetadataimport:: Enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)，`EnumFieldsWithName`會捨棄所有不具有指定的名稱的欄位語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f7384-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7384-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7384-114">Return Value</span></span>  
  
|<span data-ttu-id="f7384-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7384-115">HRESULT</span></span>|<span data-ttu-id="f7384-116">描述</span><span class="sxs-lookup"><span data-stu-id="f7384-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f7384-117">`EnumFieldsWithName` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f7384-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f7384-118">沒有列舉欄位。</span><span class="sxs-lookup"><span data-stu-id="f7384-118">There are no fields to enumerate.</span></span> <span data-ttu-id="f7384-119">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="f7384-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7384-120">需求</span><span class="sxs-lookup"><span data-stu-id="f7384-120">Requirements</span></span>  
 <span data-ttu-id="f7384-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7384-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7384-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7384-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7384-123">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f7384-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7384-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7384-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7384-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7384-125">See also</span></span>

- [<span data-ttu-id="f7384-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f7384-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f7384-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f7384-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
