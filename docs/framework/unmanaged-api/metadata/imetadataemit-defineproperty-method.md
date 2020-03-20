---
title: IMetaDataEmit::DefineProperty 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175781"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="d7be7-102">IMetaDataEmit::DefineProperty 方法</span><span class="sxs-lookup"><span data-stu-id="d7be7-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="d7be7-103">使用指定的`get`和方法`set`訪問器為指定類型創建屬性定義，並獲取該屬性定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="d7be7-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7be7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7be7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7be7-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7be7-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d7be7-106">[在]正在定義屬性的類或介面的權杖。</span><span class="sxs-lookup"><span data-stu-id="d7be7-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="d7be7-107">[在]屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7be7-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="d7be7-108">[在]屬性標誌。</span><span class="sxs-lookup"><span data-stu-id="d7be7-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="d7be7-109">[在]屬性簽名。</span><span class="sxs-lookup"><span data-stu-id="d7be7-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d7be7-110">[在]中的`pvSig`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="d7be7-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d7be7-111">[在]屬性的預設值的類型。</span><span class="sxs-lookup"><span data-stu-id="d7be7-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d7be7-112">[在]屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="d7be7-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d7be7-113">[在]中的（Unicode） 字元的`pValue`計數。</span><span class="sxs-lookup"><span data-stu-id="d7be7-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="d7be7-114">[在]設置屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="d7be7-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="d7be7-115">[在]獲取屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="d7be7-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d7be7-116">[在]與 屬性關聯的其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="d7be7-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="d7be7-117">使用 終止陣列`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="d7be7-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="d7be7-118">[出]分配的`mdProperty`權杖。</span><span class="sxs-lookup"><span data-stu-id="d7be7-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7be7-119">需求</span><span class="sxs-lookup"><span data-stu-id="d7be7-119">Requirements</span></span>  
 <span data-ttu-id="d7be7-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7be7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7be7-121">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="d7be7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7be7-122">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d7be7-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7be7-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7be7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7be7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7be7-124">See also</span></span>

- [<span data-ttu-id="d7be7-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d7be7-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d7be7-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d7be7-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
