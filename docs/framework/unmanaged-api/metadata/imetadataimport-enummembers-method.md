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
ms.openlocfilehash: 88b8f874400d68110fa5e8fb66ca910b8e7231e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645960"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="0ef85-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="0ef85-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="0ef85-103">列舉代表指定類型成員的 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0ef85-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ef85-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ef85-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ef85-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ef85-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0ef85-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="0ef85-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="0ef85-107">[in]代表其成員的列舉的類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0ef85-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="0ef85-108">[out]陣列，用來保存 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0ef85-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0ef85-109">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="0ef85-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0ef85-110">[out]MemberDef 語彙基元中傳回的實際數目`rMembers`。</span><span class="sxs-lookup"><span data-stu-id="0ef85-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ef85-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="0ef85-111">Return Value</span></span>  
  
|<span data-ttu-id="0ef85-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ef85-112">HRESULT</span></span>|<span data-ttu-id="0ef85-113">描述</span><span class="sxs-lookup"><span data-stu-id="0ef85-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0ef85-114">`EnumMembers` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0ef85-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0ef85-115">沒有列舉 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0ef85-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="0ef85-116">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="0ef85-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ef85-117">備註</span><span class="sxs-lookup"><span data-stu-id="0ef85-117">Remarks</span></span>  
 <span data-ttu-id="0ef85-118">列舉集合之成員的類別，當`EnumMembers`傳回直接在類別上定義的成員。</span><span class="sxs-lookup"><span data-stu-id="0ef85-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="0ef85-119">它不會傳回此類別繼承，任何成員即使類別會提供實作這些繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="0ef85-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="0ef85-120">若要列舉繼承的成員，呼叫者必須明確地逐步繼承鏈結。</span><span class="sxs-lookup"><span data-stu-id="0ef85-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="0ef85-121">請注意，規則的繼承鏈結可能會不同的語言或編譯器發出的原始中繼資料而定。</span><span class="sxs-lookup"><span data-stu-id="0ef85-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ef85-122">需求</span><span class="sxs-lookup"><span data-stu-id="0ef85-122">Requirements</span></span>  
 <span data-ttu-id="0ef85-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef85-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ef85-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ef85-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ef85-125">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0ef85-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ef85-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ef85-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef85-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ef85-127">See also</span></span>
- [<span data-ttu-id="0ef85-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="0ef85-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0ef85-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="0ef85-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
