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
ms.openlocfilehash: 35b82c33e54619eb9bebd5e5749ae202e905357a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720983"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="8c02f-102">IMetaDataImport::EnumMembersWithName 方法</span><span class="sxs-lookup"><span data-stu-id="8c02f-102">IMetaDataImport::EnumMembersWithName Method</span></span>

<span data-ttu-id="8c02f-103">列舉 MemberDef 語彙基元，其代表具有指定名稱之指定類型成員。</span><span class="sxs-lookup"><span data-stu-id="8c02f-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c02f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c02f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8c02f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c02f-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="8c02f-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="8c02f-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="8c02f-107">在表示具有要列舉之成員類型的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="8c02f-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c02f-108">在限制列舉值範圍的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="8c02f-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="8c02f-109">擴展用來儲存 MemberDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="8c02f-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8c02f-110">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8c02f-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8c02f-111">擴展在中傳回的 MemberDef token 的實際數目 `rMembers` 。</span><span class="sxs-lookup"><span data-stu-id="8c02f-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c02f-112">備註</span><span class="sxs-lookup"><span data-stu-id="8c02f-112">Remarks</span></span>  

 <span data-ttu-id="8c02f-113">這個方法會列舉欄位和方法，但不會列舉屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="8c02f-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="8c02f-114">不同于 [IMetaDataImport：： EnumMembers](imetadataimport-enummembers-method.md)，會 `EnumMembersWithName` 捨棄沒有指定名稱的所有欄位和成員標記。</span><span class="sxs-lookup"><span data-stu-id="8c02f-114">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c02f-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="8c02f-115">Return Value</span></span>  
  
|<span data-ttu-id="8c02f-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c02f-116">HRESULT</span></span>|<span data-ttu-id="8c02f-117">描述</span><span class="sxs-lookup"><span data-stu-id="8c02f-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8c02f-118">`EnumTypeDefs` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="8c02f-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8c02f-119">沒有要列舉的 MemberDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="8c02f-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="8c02f-120">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="8c02f-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c02f-121">需求</span><span class="sxs-lookup"><span data-stu-id="8c02f-121">Requirements</span></span>  

 <span data-ttu-id="8c02f-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c02f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c02f-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8c02f-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c02f-124">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8c02f-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c02f-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c02f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c02f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c02f-126">See also</span></span>

- [<span data-ttu-id="8c02f-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8c02f-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8c02f-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8c02f-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
