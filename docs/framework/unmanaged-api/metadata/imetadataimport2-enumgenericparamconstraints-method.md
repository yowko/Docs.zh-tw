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
ms.openlocfilehash: d1683965193801dbdee038ab06366178891fd978
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426719"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="1ab64-102">IMetaDataImport2::EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="1ab64-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="1ab64-103">取得與指定標記所代表的泛型參數相關聯之泛型參數條件約束陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1ab64-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ab64-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ab64-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ab64-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ab64-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1ab64-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="1ab64-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="1ab64-107">在  Token，代表要列舉其條件約束的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="1ab64-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="1ab64-108">脫銷要列舉的泛型參數條件約束陣列。</span><span class="sxs-lookup"><span data-stu-id="1ab64-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1ab64-109">在  要在 `rGenericParamConstraints`中放置的最大權杖數目。</span><span class="sxs-lookup"><span data-stu-id="1ab64-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="1ab64-110">脫銷放在 `rGenericParamConstraints`中之標記數目的指標。</span><span class="sxs-lookup"><span data-stu-id="1ab64-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ab64-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ab64-111">Return Value</span></span>  
  
|<span data-ttu-id="1ab64-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ab64-112">HRESULT</span></span>|<span data-ttu-id="1ab64-113">描述</span><span class="sxs-lookup"><span data-stu-id="1ab64-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1ab64-114">已成功傳回 `EnumGenericParameterConstraints`。</span><span class="sxs-lookup"><span data-stu-id="1ab64-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1ab64-115">`phEnum` 沒有成員元素。</span><span class="sxs-lookup"><span data-stu-id="1ab64-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="1ab64-116">在此情況下，`pcGenericParameterConstraints` 會設定為0（零）。</span><span class="sxs-lookup"><span data-stu-id="1ab64-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ab64-117">需求</span><span class="sxs-lookup"><span data-stu-id="1ab64-117">Requirements</span></span>  
 <span data-ttu-id="1ab64-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab64-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ab64-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1ab64-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ab64-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1ab64-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ab64-121">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ab64-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab64-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ab64-122">See also</span></span>

- [<span data-ttu-id="1ab64-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="1ab64-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="1ab64-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="1ab64-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
