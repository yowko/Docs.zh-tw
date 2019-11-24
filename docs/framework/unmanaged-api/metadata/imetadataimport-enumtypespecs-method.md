---
title: IMetaDataImport::EnumTypeSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 42b8360ac6a7bb62f29046475d6cc98124619770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449964"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="facb2-102">IMetaDataImport::EnumTypeSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="facb2-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="facb2-103">列舉在目前中繼資料範圍中定義的 TypeSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="facb2-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="facb2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="facb2-105">參數</span><span class="sxs-lookup"><span data-stu-id="facb2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="facb2-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="facb2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="facb2-107">This value must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="facb2-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="facb2-108">[out] The array used to store the TypeSpec tokens.</span><span class="sxs-lookup"><span data-stu-id="facb2-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="facb2-109">[in] `rTypeSpecs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="facb2-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="facb2-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="facb2-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="facb2-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="facb2-111">Return Value</span></span>  
  
|<span data-ttu-id="facb2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="facb2-112">HRESULT</span></span>|<span data-ttu-id="facb2-113">描述</span><span class="sxs-lookup"><span data-stu-id="facb2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="facb2-114">`EnumTypeSpecs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="facb2-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="facb2-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="facb2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="facb2-116">In that case, `pcTypeSpecs` is zero.</span><span class="sxs-lookup"><span data-stu-id="facb2-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="facb2-117">備註</span><span class="sxs-lookup"><span data-stu-id="facb2-117">Remarks</span></span>  
 <span data-ttu-id="facb2-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="facb2-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facb2-119">需求</span><span class="sxs-lookup"><span data-stu-id="facb2-119">Requirements</span></span>  
 <span data-ttu-id="facb2-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="facb2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facb2-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="facb2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="facb2-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="facb2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="facb2-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facb2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facb2-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="facb2-124">See also</span></span>

- [<span data-ttu-id="facb2-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="facb2-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="facb2-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="facb2-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
