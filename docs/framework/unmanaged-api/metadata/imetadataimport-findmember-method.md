---
title: IMetaDataImport::FindMember 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 267a36fbbdf48472bc35581ce98af5cd7a9cef9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550366"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="8ea88-102">IMetaDataImport::FindMember 方法</span><span class="sxs-lookup"><span data-stu-id="8ea88-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="8ea88-103">取得的 memberdef 語彙基元指標的欄位或方法是由指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="8ea88-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ea88-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ea88-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ea88-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ea88-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8ea88-106">[in]類別或介面，包含要搜尋的成員 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8ea88-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="8ea88-107">如果此值為`mdTokenNil`，全域變數或全域函式完成的查詢。</span><span class="sxs-lookup"><span data-stu-id="8ea88-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="8ea88-108">[in]要搜尋的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="8ea88-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8ea88-109">[in]二進位中繼資料簽章的成員指標。</span><span class="sxs-lookup"><span data-stu-id="8ea88-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8ea88-110">[in]以位元組為單位的大小`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="8ea88-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="8ea88-111">[out]比對的 MemberDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="8ea88-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ea88-112">備註</span><span class="sxs-lookup"><span data-stu-id="8ea88-112">Remarks</span></span>  
 <span data-ttu-id="8ea88-113">指定使用其封入類別或介面的成員 (`td`)，其名稱 (`szName`)，和 （選擇性） 其簽章 (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="8ea88-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="8ea88-114">可能有多個具有相同名稱的類別或介面中的成員。</span><span class="sxs-lookup"><span data-stu-id="8ea88-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="8ea88-115">在此情況下，傳遞該成員的簽章，以尋找唯一相符項目。</span><span class="sxs-lookup"><span data-stu-id="8ea88-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="8ea88-116">簽章傳遞至`FindMember`必須已產生在目前的範圍內，因為簽章會繫結至特定的範圍。</span><span class="sxs-lookup"><span data-stu-id="8ea88-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="8ea88-117">簽章可以內嵌識別封入類別或實值類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8ea88-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="8ea88-118">語彙基元是本機 TypeDef 資訊表內的索引。</span><span class="sxs-lookup"><span data-stu-id="8ea88-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="8ea88-119">您無法建置目前範圍的內容以外的執行階段簽章，並使用該簽章為輸入至輸入`FindMember`。</span><span class="sxs-lookup"><span data-stu-id="8ea88-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="8ea88-120">`FindMember` 尋找直接在類別或介面中所定義的成員找不到繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="8ea88-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ea88-121">`FindMember` 是 helper 方法。</span><span class="sxs-lookup"><span data-stu-id="8ea88-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="8ea88-122">它會呼叫[imetadataimport:: Findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); 如果該呼叫找不到相符項目，`FindMember`然後呼叫[imetadataimport:: Findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)。</span><span class="sxs-lookup"><span data-stu-id="8ea88-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ea88-123">需求</span><span class="sxs-lookup"><span data-stu-id="8ea88-123">Requirements</span></span>  
 <span data-ttu-id="8ea88-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ea88-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ea88-125">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ea88-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ea88-126">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8ea88-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ea88-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ea88-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea88-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ea88-128">See also</span></span>
- [<span data-ttu-id="8ea88-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8ea88-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8ea88-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8ea88-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
