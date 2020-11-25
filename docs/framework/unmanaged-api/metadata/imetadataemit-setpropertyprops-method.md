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
ms.openlocfilehash: 553a82475f241fac3a56c1fb009e3ed56b2c14f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704236"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="99fd0-102">IMetaDataEmit::SetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="99fd0-102">IMetaDataEmit::SetPropertyProps Method</span></span>

<span data-ttu-id="99fd0-103">針對之前呼叫 [DefineProperty 方法](imetadataemit-defineproperty-method.md)所定義的屬性，設定儲存在中繼資料中的功能。</span><span class="sxs-lookup"><span data-stu-id="99fd0-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="99fd0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="99fd0-105">參數</span><span class="sxs-lookup"><span data-stu-id="99fd0-105">Parameters</span></span>  

 `pr`  
 <span data-ttu-id="99fd0-106">在要變更之屬性的標記</span><span class="sxs-lookup"><span data-stu-id="99fd0-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="99fd0-107">在屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="99fd0-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="99fd0-108">在屬性預設值的型別。</span><span class="sxs-lookup"><span data-stu-id="99fd0-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="99fd0-109">在屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="99fd0-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="99fd0-110">在 (的 Unicode) 字元計數 `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="99fd0-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="99fd0-111">在設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="99fd0-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="99fd0-112">在取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="99fd0-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="99fd0-113">在與屬性相關聯之其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="99fd0-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="99fd0-114">使用標記結束此陣列 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="99fd0-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fd0-115">需求</span><span class="sxs-lookup"><span data-stu-id="99fd0-115">Requirements</span></span>  

 <span data-ttu-id="99fd0-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99fd0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fd0-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="99fd0-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99fd0-118">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="99fd0-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99fd0-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fd0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fd0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99fd0-120">See also</span></span>

- [<span data-ttu-id="99fd0-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="99fd0-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="99fd0-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="99fd0-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
