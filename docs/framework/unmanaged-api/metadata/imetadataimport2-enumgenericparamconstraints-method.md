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
ms.openlocfilehash: af226f9317b67b23e03d06614ed5b9c956939c22
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503415"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="94a28-102">IMetaDataImport2::EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="94a28-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="94a28-103">取得與指定標記所代表的泛型參數相關聯之泛型參數條件約束陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="94a28-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a28-104">語法</span><span class="sxs-lookup"><span data-stu-id="94a28-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94a28-105">參數</span><span class="sxs-lookup"><span data-stu-id="94a28-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="94a28-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="94a28-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="94a28-107">在  Token，代表要列舉其條件約束的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="94a28-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="94a28-108">脫銷要列舉的泛型參數條件約束陣列。</span><span class="sxs-lookup"><span data-stu-id="94a28-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="94a28-109">在  要放置在中的要求最大權杖數目 `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="94a28-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="94a28-110">脫銷放入中的標記數目的指標 `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="94a28-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94a28-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="94a28-111">Return Value</span></span>  
  
|<span data-ttu-id="94a28-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94a28-112">HRESULT</span></span>|<span data-ttu-id="94a28-113">說明</span><span class="sxs-lookup"><span data-stu-id="94a28-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="94a28-114">`EnumGenericParameterConstraints`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="94a28-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="94a28-115">`phEnum`沒有成員元素。</span><span class="sxs-lookup"><span data-stu-id="94a28-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="94a28-116">在此情況下， `pcGenericParameterConstraints` 會設為0（零）。</span><span class="sxs-lookup"><span data-stu-id="94a28-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94a28-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="94a28-117">Requirements</span></span>  
 <span data-ttu-id="94a28-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94a28-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94a28-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="94a28-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94a28-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="94a28-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94a28-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94a28-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a28-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94a28-122">See also</span></span>

- [<span data-ttu-id="94a28-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="94a28-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="94a28-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="94a28-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
