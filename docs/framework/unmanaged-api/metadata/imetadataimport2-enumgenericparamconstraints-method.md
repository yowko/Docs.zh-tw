---
title: IMetaDataImport2::EnumGenericParamConstraints 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7a51d1ddf7a5a65ce8713161c53c1c54a5d8861
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617690"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="f7144-102">IMetaDataImport2::EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="f7144-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="f7144-103">取得與指定的語彙基元所代表的泛型參數相關聯的泛型參數條件約束的陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f7144-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7144-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7144-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7144-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7144-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f7144-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="f7144-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f7144-107">[in]  代表泛型參數的條件約束是要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="f7144-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="f7144-108">[out]若要列舉的泛型參數條件約束的陣列。</span><span class="sxs-lookup"><span data-stu-id="f7144-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f7144-109">[in]  將放在權杖的要求的數目上限`rGenericParamConstraints`。</span><span class="sxs-lookup"><span data-stu-id="f7144-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="f7144-110">[out]權杖數目的指標放在`rGenericParamConstraints`。</span><span class="sxs-lookup"><span data-stu-id="f7144-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7144-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7144-111">Return Value</span></span>  
  
|<span data-ttu-id="f7144-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7144-112">HRESULT</span></span>|<span data-ttu-id="f7144-113">描述</span><span class="sxs-lookup"><span data-stu-id="f7144-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f7144-114">`EnumGenericParameterConstraints` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f7144-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f7144-115">`phEnum` 有沒有成員項目。</span><span class="sxs-lookup"><span data-stu-id="f7144-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="f7144-116">在此情況下，`pcGenericParameterConstraints`設為 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="f7144-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7144-117">需求</span><span class="sxs-lookup"><span data-stu-id="f7144-117">Requirements</span></span>  
 <span data-ttu-id="f7144-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7144-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7144-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7144-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7144-120">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f7144-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7144-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7144-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7144-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7144-122">See also</span></span>
- [<span data-ttu-id="f7144-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f7144-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="f7144-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f7144-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
