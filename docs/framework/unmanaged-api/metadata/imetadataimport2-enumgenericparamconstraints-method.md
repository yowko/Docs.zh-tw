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
ms.openlocfilehash: 27c3ec349cf6c83f6783e252e6c5af5e99fa4b37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702832"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="f4437-102">IMetaDataImport2::EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="f4437-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>

<span data-ttu-id="f4437-103">取得泛型參數條件約束陣列的列舉值，這些條件約束與指定標記所表示的泛型參數相關聯。</span><span class="sxs-lookup"><span data-stu-id="f4437-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4437-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4437-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4437-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4437-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="f4437-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="f4437-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f4437-107">在  Token，代表要列舉其條件約束的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="f4437-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="f4437-108">擴展要列舉之泛型參數條件約束的陣列。</span><span class="sxs-lookup"><span data-stu-id="f4437-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f4437-109">在  要求的最大權杖數目 `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="f4437-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="f4437-110">擴展放入的標記數目指標 `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="f4437-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4437-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4437-111">Return Value</span></span>  
  
|<span data-ttu-id="f4437-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4437-112">HRESULT</span></span>|<span data-ttu-id="f4437-113">描述</span><span class="sxs-lookup"><span data-stu-id="f4437-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f4437-114">`EnumGenericParameterConstraints` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="f4437-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f4437-115">`phEnum` 沒有成員元素。</span><span class="sxs-lookup"><span data-stu-id="f4437-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="f4437-116">在此情況下， `pcGenericParameterConstraints` 會設定為 0 (零) 。</span><span class="sxs-lookup"><span data-stu-id="f4437-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4437-117">需求</span><span class="sxs-lookup"><span data-stu-id="f4437-117">Requirements</span></span>  

 <span data-ttu-id="f4437-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4437-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4437-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f4437-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4437-120">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f4437-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4437-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4437-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4437-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4437-122">See also</span></span>

- [<span data-ttu-id="f4437-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f4437-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="f4437-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f4437-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
