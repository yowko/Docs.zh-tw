---
title: IMetaDataEmit::DefineField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432554"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="33da9-102">IMetaDataEmit::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="33da9-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="33da9-103">使用指定的中繼資料簽章建立欄位的定義，並取得該欄位定義的 token。</span><span class="sxs-lookup"><span data-stu-id="33da9-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33da9-104">語法</span><span class="sxs-lookup"><span data-stu-id="33da9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33da9-105">參數</span><span class="sxs-lookup"><span data-stu-id="33da9-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="33da9-106">在封入類別或介面的 `mdTypeDef` token。</span><span class="sxs-lookup"><span data-stu-id="33da9-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="33da9-107">在Unicode 中的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="33da9-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="33da9-108">在欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="33da9-108">[in] The field attributes.</span></span> <span data-ttu-id="33da9-109">這是 `CorFieldAttr` 值的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="33da9-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="33da9-110">在做為 BLOB 的欄位簽章。</span><span class="sxs-lookup"><span data-stu-id="33da9-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="33da9-111">在`pvSigBlob`中的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="33da9-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="33da9-112">在常數值的 `ELEMENT_TYPE_` *\** 。</span><span class="sxs-lookup"><span data-stu-id="33da9-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="33da9-113">這是 `CorElementType` 值。</span><span class="sxs-lookup"><span data-stu-id="33da9-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="33da9-114">如果未定義欄位的常數值，請使用 `ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="33da9-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="33da9-115">在欄位的常數值。</span><span class="sxs-lookup"><span data-stu-id="33da9-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="33da9-116">在`pValue`的（Unicode）字元大小。</span><span class="sxs-lookup"><span data-stu-id="33da9-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="33da9-117">脫銷指派的 `mdFieldDef` token。</span><span class="sxs-lookup"><span data-stu-id="33da9-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33da9-118">需求</span><span class="sxs-lookup"><span data-stu-id="33da9-118">Requirements</span></span>  
 <span data-ttu-id="33da9-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33da9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33da9-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="33da9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33da9-121">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="33da9-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33da9-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33da9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33da9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33da9-123">See also</span></span>

- [<span data-ttu-id="33da9-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="33da9-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="33da9-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="33da9-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
