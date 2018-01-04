---
title: "IMetaDataImport::EnumMembersWithName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembersWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b0cef8fca7be315185ab521464b251f2a94f3b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="27946-102">IMetaDataImport::EnumMembersWithName 方法</span><span class="sxs-lookup"><span data-stu-id="27946-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="27946-103">列舉 MemberDef 語彙基元，其代表具有指定名稱之指定類型成員。</span><span class="sxs-lookup"><span data-stu-id="27946-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27946-104">語法</span><span class="sxs-lookup"><span data-stu-id="27946-104">Syntax</span></span>  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27946-105">參數</span><span class="sxs-lookup"><span data-stu-id="27946-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="27946-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="27946-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="27946-107">[in]代表具有列舉的成員類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="27946-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="27946-108">[in]列舉值的範圍限制成員名稱。</span><span class="sxs-lookup"><span data-stu-id="27946-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="27946-109">[out]陣列，用來儲存 memberdef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="27946-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="27946-110">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="27946-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="27946-111">[out]Memberdef 語彙基元中傳回的實際數目`rMembers`。</span><span class="sxs-lookup"><span data-stu-id="27946-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27946-112">備註</span><span class="sxs-lookup"><span data-stu-id="27946-112">Remarks</span></span>  
 <span data-ttu-id="27946-113">這個方法會列舉欄位和方法，但沒有屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="27946-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="27946-114">不同於[imetadataimport:: Enummembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)，`EnumMembersWithName`捨棄不具有指定的名稱的所有欄位和成員 token。</span><span class="sxs-lookup"><span data-stu-id="27946-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27946-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="27946-115">Return Value</span></span>  
  
|<span data-ttu-id="27946-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27946-116">HRESULT</span></span>|<span data-ttu-id="27946-117">描述</span><span class="sxs-lookup"><span data-stu-id="27946-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="27946-118">`EnumTypeDefs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="27946-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="27946-119">沒有列舉 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="27946-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="27946-120">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="27946-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27946-121">需求</span><span class="sxs-lookup"><span data-stu-id="27946-121">Requirements</span></span>  
 <span data-ttu-id="27946-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27946-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27946-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27946-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27946-124">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="27946-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27946-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27946-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27946-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="27946-126">See Also</span></span>  
 [<span data-ttu-id="27946-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="27946-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="27946-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="27946-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
