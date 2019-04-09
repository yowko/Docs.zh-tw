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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8d871f2ecbd96d5bda781b2ae11b94efd409442
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128397"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="728b3-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="728b3-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="728b3-103">列舉代表指定類型成員的 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="728b3-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="728b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="728b3-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="728b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="728b3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="728b3-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="728b3-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="728b3-107">[in]代表其成員的列舉的類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="728b3-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="728b3-108">[out]陣列，用來保存 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="728b3-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="728b3-109">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="728b3-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="728b3-110">[out]MemberDef 語彙基元中傳回的實際數目`rMembers`。</span><span class="sxs-lookup"><span data-stu-id="728b3-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="728b3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="728b3-111">Return Value</span></span>  
  
|<span data-ttu-id="728b3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="728b3-112">HRESULT</span></span>|<span data-ttu-id="728b3-113">描述</span><span class="sxs-lookup"><span data-stu-id="728b3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` <span data-ttu-id="728b3-114">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="728b3-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="728b3-115">沒有列舉 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="728b3-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="728b3-116">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="728b3-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="728b3-117">備註</span><span class="sxs-lookup"><span data-stu-id="728b3-117">Remarks</span></span>  
 <span data-ttu-id="728b3-118">列舉集合之成員的類別，當`EnumMembers`只傳回成員 (欄位和方法，但**不**屬性或事件) 直接在類別上定義。</span><span class="sxs-lookup"><span data-stu-id="728b3-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="728b3-119">它不會傳回此類別繼承，任何成員即使類別會提供實作這些繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="728b3-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="728b3-120">若要列舉繼承的成員，呼叫者必須明確地逐步繼承鏈結。</span><span class="sxs-lookup"><span data-stu-id="728b3-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="728b3-121">請注意，規則的繼承鏈結可能會不同的語言或編譯器發出的原始中繼資料而定。</span><span class="sxs-lookup"><span data-stu-id="728b3-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="728b3-122">屬性和事件不會列舉`EnumMembers`。</span><span class="sxs-lookup"><span data-stu-id="728b3-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="728b3-123">若要列舉的請使用[EnumProperties](imetadataimport-enumproperties-method.md)或是[EnumEvents](imetadataimport-enumevents-method.md)。</span><span class="sxs-lookup"><span data-stu-id="728b3-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="728b3-124">需求</span><span class="sxs-lookup"><span data-stu-id="728b3-124">Requirements</span></span>  
 <span data-ttu-id="728b3-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="728b3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="728b3-126">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="728b3-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="728b3-127">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="728b3-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="728b3-128">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="728b3-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="728b3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="728b3-129">See also</span></span>

- [<span data-ttu-id="728b3-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="728b3-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="728b3-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="728b3-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
