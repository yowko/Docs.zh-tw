---
title: IMetaDataImport2::EnumGenericParams 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175300"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="3f009-102">IMetaDataImport2::EnumGenericParams 方法</span><span class="sxs-lookup"><span data-stu-id="3f009-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="3f009-103">獲取與指定 TypeDef 或 MethodDef 權杖關聯的泛型參數權杖陣列的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="3f009-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f009-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f009-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f009-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f009-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3f009-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="3f009-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="3f009-107">[在]要枚舉泛型參數的 TypeDef 或 MethodDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="3f009-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="3f009-108">[出]要枚舉的泛型參數陣列。</span><span class="sxs-lookup"><span data-stu-id="3f009-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3f009-109">[在]要放置在 中`rGenericParams`的最大權杖數。</span><span class="sxs-lookup"><span data-stu-id="3f009-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="3f009-110">[出]放置在 的`rGenericParams`返回的權杖數。</span><span class="sxs-lookup"><span data-stu-id="3f009-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f009-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="3f009-111">Return Value</span></span>  
  
|<span data-ttu-id="3f009-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f009-112">HRESULT</span></span>|<span data-ttu-id="3f009-113">描述</span><span class="sxs-lookup"><span data-stu-id="3f009-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3f009-114">`EnumGenericParams`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="3f009-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3f009-115">`phEnum`沒有成員元素。</span><span class="sxs-lookup"><span data-stu-id="3f009-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="3f009-116">在這種情況下，`pcGenericParams`設置為 0（零）。</span><span class="sxs-lookup"><span data-stu-id="3f009-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f009-117">需求</span><span class="sxs-lookup"><span data-stu-id="3f009-117">Requirements</span></span>  
 <span data-ttu-id="3f009-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f009-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f009-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="3f009-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f009-120">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3f009-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f009-121">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f009-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f009-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f009-122">See also</span></span>

- [<span data-ttu-id="3f009-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3f009-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="3f009-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3f009-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
