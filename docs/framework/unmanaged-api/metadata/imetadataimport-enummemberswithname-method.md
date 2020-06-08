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
ms.openlocfilehash: ea451bdd645d2d4dea4c5dd00408e0bc51804803
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492066"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="79eac-102">IMetaDataImport::EnumMembersWithName 方法</span><span class="sxs-lookup"><span data-stu-id="79eac-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="79eac-103">列舉 MemberDef 語彙基元，其代表具有指定名稱之指定類型成員。</span><span class="sxs-lookup"><span data-stu-id="79eac-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79eac-104">語法</span><span class="sxs-lookup"><span data-stu-id="79eac-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="79eac-105">參數</span><span class="sxs-lookup"><span data-stu-id="79eac-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="79eac-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="79eac-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="79eac-107">在TypeDef token，代表具有要列舉之成員的類型。</span><span class="sxs-lookup"><span data-stu-id="79eac-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="79eac-108">在限制列舉值範圍的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="79eac-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="79eac-109">脫銷用來儲存 MemberDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="79eac-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="79eac-110">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="79eac-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="79eac-111">脫銷在中傳回的 MemberDef token 實際數目 `rMembers` 。</span><span class="sxs-lookup"><span data-stu-id="79eac-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79eac-112">備註</span><span class="sxs-lookup"><span data-stu-id="79eac-112">Remarks</span></span>  
 <span data-ttu-id="79eac-113">這個方法會列舉欄位和方法，而不是屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="79eac-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="79eac-114">不同于[IMetaDataImport：： EnumMembers](imetadataimport-enummembers-method.md)，會 `EnumMembersWithName` 捨棄所有沒有指定名稱的欄位和成員 token。</span><span class="sxs-lookup"><span data-stu-id="79eac-114">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79eac-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="79eac-115">Return Value</span></span>  
  
|<span data-ttu-id="79eac-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79eac-116">HRESULT</span></span>|<span data-ttu-id="79eac-117">說明</span><span class="sxs-lookup"><span data-stu-id="79eac-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="79eac-118">`EnumTypeDefs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="79eac-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="79eac-119">沒有要列舉的 MemberDef token。</span><span class="sxs-lookup"><span data-stu-id="79eac-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="79eac-120">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="79eac-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79eac-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="79eac-121">Requirements</span></span>  
 <span data-ttu-id="79eac-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79eac-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79eac-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="79eac-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79eac-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="79eac-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79eac-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79eac-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79eac-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79eac-126">See also</span></span>

- [<span data-ttu-id="79eac-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="79eac-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="79eac-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="79eac-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
