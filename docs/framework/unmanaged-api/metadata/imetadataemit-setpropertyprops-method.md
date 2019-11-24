---
title: IMetaDataEmit::SetPropertyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: 0fdec87324d6efa0f911e37573093c19b93c0349
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440544"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="ee73b-102">IMetaDataEmit::SetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="ee73b-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="ee73b-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="ee73b-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee73b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee73b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee73b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee73b-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="ee73b-106">[in] The token for the property to be changed</span><span class="sxs-lookup"><span data-stu-id="ee73b-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="ee73b-107">[in] Property flags.</span><span class="sxs-lookup"><span data-stu-id="ee73b-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="ee73b-108">[in] The type of the property's default value.</span><span class="sxs-lookup"><span data-stu-id="ee73b-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ee73b-109">[in] The default value for the property.</span><span class="sxs-lookup"><span data-stu-id="ee73b-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ee73b-110">[in] The count of (Unicode) characters in `pValue`.</span><span class="sxs-lookup"><span data-stu-id="ee73b-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="ee73b-111">[in] The method that sets the property value.</span><span class="sxs-lookup"><span data-stu-id="ee73b-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="ee73b-112">[in] The method that gets the property value.</span><span class="sxs-lookup"><span data-stu-id="ee73b-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="ee73b-113">[in] An array of other methods associated with the property.</span><span class="sxs-lookup"><span data-stu-id="ee73b-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="ee73b-114">Terminate this array with an `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="ee73b-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee73b-115">需求</span><span class="sxs-lookup"><span data-stu-id="ee73b-115">Requirements</span></span>  
 <span data-ttu-id="ee73b-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee73b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee73b-117">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee73b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee73b-118">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee73b-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee73b-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee73b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee73b-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee73b-120">See also</span></span>

- [<span data-ttu-id="ee73b-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ee73b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ee73b-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ee73b-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
