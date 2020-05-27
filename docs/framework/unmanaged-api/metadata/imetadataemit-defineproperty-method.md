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
ms.openlocfilehash: 479cb25ad8e1c263d3539a4203ac5bea781eb931
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009370"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="8ee9e-102">IMetaDataEmit::DefineProperty 方法</span><span class="sxs-lookup"><span data-stu-id="8ee9e-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="8ee9e-103">使用指定的和方法存取子，為指定的類型建立屬性定義 `get` `set` ，並取得該屬性定義的 token。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ee9e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8ee9e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ee9e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8ee9e-106">在要在其上定義屬性之類別或介面的 token。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="8ee9e-107">在屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="8ee9e-108">在屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="8ee9e-109">在屬性簽章。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="8ee9e-110">在中的位元組計數 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="8ee9e-111">在屬性的預設值類型。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8ee9e-112">在屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="8ee9e-113">在中的（Unicode）字元計數 `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="8ee9e-114">在設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="8ee9e-115">在取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="8ee9e-116">在與屬性相關聯之其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="8ee9e-117">使用終止陣列 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="8ee9e-118">脫銷`mdProperty`指派的 token。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee9e-119">需求</span><span class="sxs-lookup"><span data-stu-id="8ee9e-119">Requirements</span></span>  
 <span data-ttu-id="8ee9e-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ee9e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee9e-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8ee9e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ee9e-122">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="8ee9e-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ee9e-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee9e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee9e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ee9e-124">See also</span></span>

- [<span data-ttu-id="8ee9e-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8ee9e-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8ee9e-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="8ee9e-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
