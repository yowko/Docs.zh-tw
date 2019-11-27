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
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="0469e-102">IMetaDataEmit::SetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="0469e-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="0469e-103">針對先前呼叫[DefineProperty 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)所定義的屬性，設定儲存在中繼資料中的功能。</span><span class="sxs-lookup"><span data-stu-id="0469e-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0469e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0469e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0469e-105">參數</span><span class="sxs-lookup"><span data-stu-id="0469e-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="0469e-106">在要變更之屬性的標記</span><span class="sxs-lookup"><span data-stu-id="0469e-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="0469e-107">在屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="0469e-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="0469e-108">在屬性的預設值類型。</span><span class="sxs-lookup"><span data-stu-id="0469e-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0469e-109">在屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="0469e-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="0469e-110">在`pValue`中的（Unicode）字元計數。</span><span class="sxs-lookup"><span data-stu-id="0469e-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="0469e-111">在設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="0469e-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="0469e-112">在取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="0469e-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="0469e-113">在與屬性相關聯之其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="0469e-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="0469e-114">使用 `mdTokenNil` token 終止此陣列。</span><span class="sxs-lookup"><span data-stu-id="0469e-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0469e-115">需求</span><span class="sxs-lookup"><span data-stu-id="0469e-115">Requirements</span></span>  
 <span data-ttu-id="0469e-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0469e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0469e-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="0469e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0469e-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="0469e-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0469e-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0469e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0469e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0469e-120">See also</span></span>

- [<span data-ttu-id="0469e-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0469e-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0469e-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0469e-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
