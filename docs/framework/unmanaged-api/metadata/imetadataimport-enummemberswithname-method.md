---
title: IMetaDataImport::EnumMembersWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177324"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="98048-102">IMetaDataImport::EnumMembersWithName 方法</span><span class="sxs-lookup"><span data-stu-id="98048-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="98048-103">列舉 MemberDef 語彙基元，其代表具有指定名稱之指定類型成員。</span><span class="sxs-lookup"><span data-stu-id="98048-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98048-104">語法</span><span class="sxs-lookup"><span data-stu-id="98048-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98048-105">參數</span><span class="sxs-lookup"><span data-stu-id="98048-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="98048-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="98048-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="98048-107">[在]表示要枚舉的成員的類型的類型的類型的類型類型。</span><span class="sxs-lookup"><span data-stu-id="98048-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="98048-108">[在]限制枚舉器範圍的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="98048-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="98048-109">[出]用於存儲成員Def權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="98048-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="98048-110">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="98048-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="98048-111">[出]在 中`rMembers`返回的會員Def權杖的實際數量。</span><span class="sxs-lookup"><span data-stu-id="98048-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98048-112">備註</span><span class="sxs-lookup"><span data-stu-id="98048-112">Remarks</span></span>  
 <span data-ttu-id="98048-113">此方法枚舉欄位和方法，但不枚舉屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="98048-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="98048-114">與[IMetaDataImport：：enum成員](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)不同，`EnumMembersWithName`請丟棄沒有指定名稱的所有欄位和成員權杖。</span><span class="sxs-lookup"><span data-stu-id="98048-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98048-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="98048-115">Return Value</span></span>  
  
|<span data-ttu-id="98048-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98048-116">HRESULT</span></span>|<span data-ttu-id="98048-117">描述</span><span class="sxs-lookup"><span data-stu-id="98048-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="98048-118">`EnumTypeDefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="98048-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="98048-119">沒有要枚舉的會員Def權杖。</span><span class="sxs-lookup"><span data-stu-id="98048-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="98048-120">在這種情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="98048-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98048-121">需求</span><span class="sxs-lookup"><span data-stu-id="98048-121">Requirements</span></span>  
 <span data-ttu-id="98048-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98048-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98048-123">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="98048-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98048-124">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="98048-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98048-125">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98048-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98048-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98048-126">See also</span></span>

- [<span data-ttu-id="98048-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="98048-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="98048-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="98048-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
