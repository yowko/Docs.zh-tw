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
ms.openlocfilehash: f11b374ed0ecbfc137c43fb641ae691237604691
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431529"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="d4b69-102">IMetaDataEmit::DefineProperty 方法</span><span class="sxs-lookup"><span data-stu-id="d4b69-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="d4b69-103">使用指定的 `get` 和 `set` 方法存取子，為指定的類型建立屬性定義，並取得該屬性定義的 token。</span><span class="sxs-lookup"><span data-stu-id="d4b69-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b69-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4b69-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d4b69-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4b69-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d4b69-106">在要在其上定義屬性之類別或介面的 token。</span><span class="sxs-lookup"><span data-stu-id="d4b69-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="d4b69-107">在屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4b69-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="d4b69-108">在屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="d4b69-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="d4b69-109">在屬性簽章。</span><span class="sxs-lookup"><span data-stu-id="d4b69-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d4b69-110">在`pvSig`中的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="d4b69-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d4b69-111">在屬性的預設值類型。</span><span class="sxs-lookup"><span data-stu-id="d4b69-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d4b69-112">在屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="d4b69-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d4b69-113">在`pValue`中的（Unicode）字元計數。</span><span class="sxs-lookup"><span data-stu-id="d4b69-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="d4b69-114">在設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="d4b69-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="d4b69-115">在取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="d4b69-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d4b69-116">在與屬性相關聯之其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="d4b69-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="d4b69-117">使用 `mdTokenNil`終止陣列。</span><span class="sxs-lookup"><span data-stu-id="d4b69-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="d4b69-118">脫銷指派的 `mdProperty` token。</span><span class="sxs-lookup"><span data-stu-id="d4b69-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b69-119">需求</span><span class="sxs-lookup"><span data-stu-id="d4b69-119">Requirements</span></span>  
 <span data-ttu-id="d4b69-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b69-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4b69-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d4b69-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4b69-122">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d4b69-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4b69-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4b69-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b69-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4b69-124">See also</span></span>

- [<span data-ttu-id="d4b69-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d4b69-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d4b69-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d4b69-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
