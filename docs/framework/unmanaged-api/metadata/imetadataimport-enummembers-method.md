---
title: IMetaDataImport::EnumMembers 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175482"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="0ab85-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="0ab85-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="0ab85-103">列舉代表指定類型成員的 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0ab85-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab85-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ab85-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ab85-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ab85-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0ab85-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="0ab85-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="0ab85-107">[在]表示要枚舉其成員的類型的類型的類型的類型。</span><span class="sxs-lookup"><span data-stu-id="0ab85-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="0ab85-108">[出]用於保存成員Def權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="0ab85-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0ab85-109">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="0ab85-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0ab85-110">[出]在 中`rMembers`返回的會員Def權杖的實際數量。</span><span class="sxs-lookup"><span data-stu-id="0ab85-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ab85-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="0ab85-111">Return Value</span></span>  
  
|<span data-ttu-id="0ab85-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ab85-112">HRESULT</span></span>|<span data-ttu-id="0ab85-113">描述</span><span class="sxs-lookup"><span data-stu-id="0ab85-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0ab85-114">`EnumMembers`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="0ab85-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0ab85-115">沒有要枚舉的會員Def權杖。</span><span class="sxs-lookup"><span data-stu-id="0ab85-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="0ab85-116">在這種情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="0ab85-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ab85-117">備註</span><span class="sxs-lookup"><span data-stu-id="0ab85-117">Remarks</span></span>  
 <span data-ttu-id="0ab85-118">枚舉類成員的集合時，`EnumMembers`僅返回直接在類上定義的成員（欄位和方法，**但不包括**屬性或事件）。</span><span class="sxs-lookup"><span data-stu-id="0ab85-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="0ab85-119">它不返回類繼承的任何成員，即使類為這些繼承成員提供了實現也是如此。</span><span class="sxs-lookup"><span data-stu-id="0ab85-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="0ab85-120">要枚舉繼承的成員，調用方必須顯式遍歷繼承鏈。</span><span class="sxs-lookup"><span data-stu-id="0ab85-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="0ab85-121">請注意，繼承鏈的規則可能因發出原始中繼資料的語言或編譯器而異。</span><span class="sxs-lookup"><span data-stu-id="0ab85-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="0ab85-122">屬性和事件不由 枚舉`EnumMembers`枚舉。</span><span class="sxs-lookup"><span data-stu-id="0ab85-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="0ab85-123">要枚舉這些，請使用[枚舉屬性](imetadataimport-enumproperties-method.md)或[枚舉事件](imetadataimport-enumevents-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0ab85-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="0ab85-124">需求</span><span class="sxs-lookup"><span data-stu-id="0ab85-124">Requirements</span></span>  
 <span data-ttu-id="0ab85-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ab85-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ab85-126">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="0ab85-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ab85-127">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0ab85-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ab85-128">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ab85-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab85-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ab85-129">See also</span></span>

- [<span data-ttu-id="0ab85-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="0ab85-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0ab85-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="0ab85-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
