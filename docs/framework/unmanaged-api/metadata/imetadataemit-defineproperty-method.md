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
ms.openlocfilehash: d2a4a15126f34666a58021a59e9e193685b15a49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719485"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="2759d-102">IMetaDataEmit::DefineProperty 方法</span><span class="sxs-lookup"><span data-stu-id="2759d-102">IMetaDataEmit::DefineProperty Method</span></span>

<span data-ttu-id="2759d-103">使用指定的和方法存取子，針對指定的型別建立屬性定義， `get` `set` 並取得該屬性定義的標記。</span><span class="sxs-lookup"><span data-stu-id="2759d-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2759d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2759d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2759d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2759d-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="2759d-106">在要在其上定義屬性之類別或介面的標記。</span><span class="sxs-lookup"><span data-stu-id="2759d-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="2759d-107">在屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="2759d-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="2759d-108">在屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="2759d-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="2759d-109">在屬性簽章。</span><span class="sxs-lookup"><span data-stu-id="2759d-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="2759d-110">在中的位元組計數 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="2759d-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="2759d-111">在屬性預設值的型別。</span><span class="sxs-lookup"><span data-stu-id="2759d-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="2759d-112">在屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="2759d-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="2759d-113">在 (的 Unicode) 字元計數 `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="2759d-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="2759d-114">在設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="2759d-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="2759d-115">在取得屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="2759d-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="2759d-116">在與屬性相關聯之其他方法的陣列。</span><span class="sxs-lookup"><span data-stu-id="2759d-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="2759d-117">使用來終止陣列 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="2759d-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="2759d-118">擴展 `mdProperty` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="2759d-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2759d-119">需求</span><span class="sxs-lookup"><span data-stu-id="2759d-119">Requirements</span></span>  

 <span data-ttu-id="2759d-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2759d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2759d-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2759d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2759d-122">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="2759d-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2759d-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2759d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2759d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2759d-124">See also</span></span>

- [<span data-ttu-id="2759d-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2759d-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2759d-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="2759d-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
