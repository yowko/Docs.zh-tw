---
title: "IMetaDataImport::EnumMembers 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembers
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc17437c18dd7a2cdc2fdabdc714b12f8d91cc7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="096e1-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="096e1-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="096e1-103">列舉代表指定類型成員的 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="096e1-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="096e1-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="096e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="096e1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="096e1-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="096e1-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="096e1-107">[in]代表其成員的列舉的類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="096e1-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="096e1-108">[out]陣列，用來保存 memberdef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="096e1-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="096e1-109">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="096e1-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="096e1-110">[out]Memberdef 語彙基元中傳回的實際數目`rMembers`。</span><span class="sxs-lookup"><span data-stu-id="096e1-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="096e1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="096e1-111">Return Value</span></span>  
  
|<span data-ttu-id="096e1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="096e1-112">HRESULT</span></span>|<span data-ttu-id="096e1-113">說明</span><span class="sxs-lookup"><span data-stu-id="096e1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="096e1-114">`EnumMembers`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="096e1-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="096e1-115">沒有列舉 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="096e1-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="096e1-116">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="096e1-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="096e1-117">備註</span><span class="sxs-lookup"><span data-stu-id="096e1-117">Remarks</span></span>  
 <span data-ttu-id="096e1-118">列舉集合成員的類別，當`EnumMembers`傳回直接在類別上定義的成員。</span><span class="sxs-lookup"><span data-stu-id="096e1-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="096e1-119">即使類別會實作提供這些繼承的成員，它不會傳回此類別會繼承，任何成員。</span><span class="sxs-lookup"><span data-stu-id="096e1-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="096e1-120">若要列舉繼承的成員，呼叫端必須明確地逐步繼承鏈結。</span><span class="sxs-lookup"><span data-stu-id="096e1-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="096e1-121">請注意，規則的繼承鏈結會視語言或編譯器發出的原始中繼資料。</span><span class="sxs-lookup"><span data-stu-id="096e1-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096e1-122">需求</span><span class="sxs-lookup"><span data-stu-id="096e1-122">Requirements</span></span>  
 <span data-ttu-id="096e1-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="096e1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="096e1-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="096e1-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="096e1-125">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="096e1-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="096e1-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="096e1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="096e1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="096e1-127">See Also</span></span>  
 [<span data-ttu-id="096e1-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="096e1-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="096e1-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="096e1-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
