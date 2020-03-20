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
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177470"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="d2909-102">IMetaDataEmit::SetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="d2909-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="d2909-103">設置存儲在中繼資料中的屬性的功能，該屬性由之前調用[DefineProperty 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)定義。</span><span class="sxs-lookup"><span data-stu-id="d2909-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2909-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2909-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d2909-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2909-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="d2909-106">[在]要更改的屬性的權杖</span><span class="sxs-lookup"><span data-stu-id="d2909-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="d2909-107">[在]屬性標誌。</span><span class="sxs-lookup"><span data-stu-id="d2909-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d2909-108">[在]屬性的預設值的類型。</span><span class="sxs-lookup"><span data-stu-id="d2909-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d2909-109">[在]屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="d2909-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d2909-110">[在]中的（Unicode） 字元的`pValue`計數。</span><span class="sxs-lookup"><span data-stu-id="d2909-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="d2909-111">[在]設置屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="d2909-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="d2909-112">[在]獲取屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="d2909-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d2909-113">[在]與 屬性關聯的其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="d2909-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="d2909-114">使用權杖終止`mdTokenNil`此陣列。</span><span class="sxs-lookup"><span data-stu-id="d2909-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2909-115">需求</span><span class="sxs-lookup"><span data-stu-id="d2909-115">Requirements</span></span>  
 <span data-ttu-id="d2909-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2909-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2909-117">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="d2909-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2909-118">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d2909-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2909-119">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2909-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2909-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2909-120">See also</span></span>

- [<span data-ttu-id="d2909-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d2909-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d2909-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d2909-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
