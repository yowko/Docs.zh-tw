---
title: IMetaDataImport::EnumFields 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 313dbd11f1d033f0e15de651b9c130cc98c217e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049930"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="4f146-102">IMetaDataImport::EnumFields 方法</span><span class="sxs-lookup"><span data-stu-id="4f146-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="4f146-103">列舉指定 TypeDef 語彙基元所參考類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4f146-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f146-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f146-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f146-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f146-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4f146-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="4f146-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="4f146-107">[in]其欄位是列舉類別的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4f146-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="4f146-108">[out]FieldDef 語彙基元清單。</span><span class="sxs-lookup"><span data-stu-id="4f146-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4f146-109">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="4f146-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4f146-110">[out]中傳回的 fielddef 語彙基元的實際數目`rFields`。</span><span class="sxs-lookup"><span data-stu-id="4f146-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f146-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4f146-111">Return Value</span></span>  
  
|<span data-ttu-id="4f146-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f146-112">HRESULT</span></span>|<span data-ttu-id="4f146-113">描述</span><span class="sxs-lookup"><span data-stu-id="4f146-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4f146-114">`EnumFields` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4f146-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4f146-115">沒有列舉欄位。</span><span class="sxs-lookup"><span data-stu-id="4f146-115">There are no fields to enumerate.</span></span> <span data-ttu-id="4f146-116">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="4f146-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f146-117">需求</span><span class="sxs-lookup"><span data-stu-id="4f146-117">Requirements</span></span>  
 <span data-ttu-id="4f146-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f146-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f146-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4f146-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f146-120">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4f146-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f146-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f146-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f146-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f146-122">See also</span></span>

- [<span data-ttu-id="4f146-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4f146-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4f146-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4f146-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
