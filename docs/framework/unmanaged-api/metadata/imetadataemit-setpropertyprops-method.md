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
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007776"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="6bee5-102">IMetaDataEmit::SetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="6bee5-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="6bee5-103">針對先前呼叫[DefineProperty 方法](imetadataemit-defineproperty-method.md)所定義的屬性，設定儲存在中繼資料中的功能。</span><span class="sxs-lookup"><span data-stu-id="6bee5-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bee5-104">語法</span><span class="sxs-lookup"><span data-stu-id="6bee5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6bee5-105">參數</span><span class="sxs-lookup"><span data-stu-id="6bee5-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="6bee5-106">在要變更之屬性的標記</span><span class="sxs-lookup"><span data-stu-id="6bee5-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="6bee5-107">在屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="6bee5-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="6bee5-108">在屬性的預設值類型。</span><span class="sxs-lookup"><span data-stu-id="6bee5-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="6bee5-109">在屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="6bee5-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="6bee5-110">在中的（Unicode）字元計數 `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="6bee5-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="6bee5-111">在設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="6bee5-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="6bee5-112">在取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="6bee5-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="6bee5-113">在與屬性相關聯之其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="6bee5-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="6bee5-114">使用權杖終止此陣列 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="6bee5-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bee5-115">需求</span><span class="sxs-lookup"><span data-stu-id="6bee5-115">Requirements</span></span>  
 <span data-ttu-id="6bee5-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bee5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bee5-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6bee5-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6bee5-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6bee5-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bee5-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bee5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bee5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bee5-120">See also</span></span>

- [<span data-ttu-id="6bee5-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6bee5-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6bee5-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6bee5-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
