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
ms.openlocfilehash: ed193aab8beb0de1321aa1d52ec9f963b08b316c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441657"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="9d0c9-102">IMetaDataImport::EnumMembersWithName 方法</span><span class="sxs-lookup"><span data-stu-id="9d0c9-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="9d0c9-103">列舉 MemberDef 語彙基元，其代表具有指定名稱之指定類型成員。</span><span class="sxs-lookup"><span data-stu-id="9d0c9-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d0c9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9d0c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d0c9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9d0c9-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="9d0c9-107">[in] A TypeDef token representing the type with members to enumerate.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="9d0c9-108">[in] The member name that limits the scope of the enumerator.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="9d0c9-109">[out] The array used to store the MemberDef tokens.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9d0c9-110">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="9d0c9-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9d0c9-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d0c9-112">備註</span><span class="sxs-lookup"><span data-stu-id="9d0c9-112">Remarks</span></span>  
 <span data-ttu-id="9d0c9-113">This method enumerates fields and methods, but not properties or events.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="9d0c9-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d0c9-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="9d0c9-115">Return Value</span></span>  
  
|<span data-ttu-id="9d0c9-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d0c9-116">HRESULT</span></span>|<span data-ttu-id="9d0c9-117">描述</span><span class="sxs-lookup"><span data-stu-id="9d0c9-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9d0c9-118">`EnumTypeDefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9d0c9-119">There are no MemberDef tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="9d0c9-120">In that case, `pcTokens` is zero.</span><span class="sxs-lookup"><span data-stu-id="9d0c9-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d0c9-121">需求</span><span class="sxs-lookup"><span data-stu-id="9d0c9-121">Requirements</span></span>  
 <span data-ttu-id="9d0c9-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d0c9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d0c9-123">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d0c9-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d0c9-124">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d0c9-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d0c9-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d0c9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0c9-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="9d0c9-126">See also</span></span>

- [<span data-ttu-id="9d0c9-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9d0c9-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9d0c9-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="9d0c9-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
