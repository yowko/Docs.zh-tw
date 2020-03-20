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
ms.openlocfilehash: be2845d1d660d86447cfbb6f2845a8e68b727e66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175508"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="1dd92-102">IMetaDataImport::EnumFields 方法</span><span class="sxs-lookup"><span data-stu-id="1dd92-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="1dd92-103">列舉指定 TypeDef 語彙基元所參考類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1dd92-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd92-104">語法</span><span class="sxs-lookup"><span data-stu-id="1dd92-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd92-105">參數</span><span class="sxs-lookup"><span data-stu-id="1dd92-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1dd92-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="1dd92-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="1dd92-107">[在]要枚舉其欄位的類的 TypeDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="1dd92-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="1dd92-108">[出]FieldDef 權杖的清單。</span><span class="sxs-lookup"><span data-stu-id="1dd92-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1dd92-109">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="1dd92-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1dd92-110">[出]在 中`rFields`返回的實際欄位Def 權杖數。</span><span class="sxs-lookup"><span data-stu-id="1dd92-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dd92-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="1dd92-111">Return Value</span></span>  
  
|<span data-ttu-id="1dd92-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dd92-112">HRESULT</span></span>|<span data-ttu-id="1dd92-113">描述</span><span class="sxs-lookup"><span data-stu-id="1dd92-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1dd92-114">`EnumFields`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="1dd92-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1dd92-115">沒有要枚舉的欄位。</span><span class="sxs-lookup"><span data-stu-id="1dd92-115">There are no fields to enumerate.</span></span> <span data-ttu-id="1dd92-116">在這種情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="1dd92-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dd92-117">需求</span><span class="sxs-lookup"><span data-stu-id="1dd92-117">Requirements</span></span>  
 <span data-ttu-id="1dd92-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd92-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd92-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="1dd92-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dd92-120">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1dd92-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd92-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd92-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd92-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd92-122">See also</span></span>

- [<span data-ttu-id="1dd92-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="1dd92-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1dd92-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="1dd92-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
