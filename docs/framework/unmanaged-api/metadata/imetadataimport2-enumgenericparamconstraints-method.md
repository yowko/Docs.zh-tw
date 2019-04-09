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
ms.openlocfilehash: f66b0145dbaece7292d2ccad169a97fbb10b6d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186676"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="058fe-102">IMetaDataImport2::EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="058fe-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="058fe-103">取得與指定的語彙基元所代表的泛型參數相關聯的泛型參數條件約束的陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="058fe-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="058fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="058fe-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="058fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="058fe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="058fe-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="058fe-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="058fe-107">[in]  代表泛型參數的條件約束是要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="058fe-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="058fe-108">[out]若要列舉的泛型參數條件約束的陣列。</span><span class="sxs-lookup"><span data-stu-id="058fe-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="058fe-109">[in]  將放在權杖的要求的數目上限`rGenericParamConstraints`。</span><span class="sxs-lookup"><span data-stu-id="058fe-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="058fe-110">[out]權杖數目的指標放在`rGenericParamConstraints`。</span><span class="sxs-lookup"><span data-stu-id="058fe-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="058fe-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="058fe-111">Return Value</span></span>  
  
|<span data-ttu-id="058fe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="058fe-112">HRESULT</span></span>|<span data-ttu-id="058fe-113">描述</span><span class="sxs-lookup"><span data-stu-id="058fe-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` <span data-ttu-id="058fe-114">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="058fe-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="058fe-115">有沒有成員項目。</span><span class="sxs-lookup"><span data-stu-id="058fe-115">has no member elements.</span></span> <span data-ttu-id="058fe-116">在此情況下，`pcGenericParameterConstraints`設為 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="058fe-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="058fe-117">需求</span><span class="sxs-lookup"><span data-stu-id="058fe-117">Requirements</span></span>  
 <span data-ttu-id="058fe-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="058fe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="058fe-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="058fe-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="058fe-120">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="058fe-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="058fe-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="058fe-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="058fe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="058fe-122">See also</span></span>

- [<span data-ttu-id="058fe-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="058fe-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="058fe-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="058fe-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
