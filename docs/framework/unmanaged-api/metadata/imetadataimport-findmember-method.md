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
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503675"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="67eb3-102">IMetaDataImport::FindMember 方法</span><span class="sxs-lookup"><span data-stu-id="67eb3-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="67eb3-103">取得欄位或方法的 MemberDef token 指標，此標記是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="67eb3-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67eb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="67eb3-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67eb3-105">參數</span><span class="sxs-lookup"><span data-stu-id="67eb3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="67eb3-106">在用來括住要搜尋之成員的類別或介面的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="67eb3-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="67eb3-107">如果這個值為 `mdTokenNil` ，則會針對全域變數或全域函式進行查閱。</span><span class="sxs-lookup"><span data-stu-id="67eb3-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="67eb3-108">在要搜尋之成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="67eb3-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="67eb3-109">在成員的二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="67eb3-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="67eb3-110">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="67eb3-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="67eb3-111">脫銷對應之 MemberDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="67eb3-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67eb3-112">備註</span><span class="sxs-lookup"><span data-stu-id="67eb3-112">Remarks</span></span>  
 <span data-ttu-id="67eb3-113">您可以使用其封入類別或介面（ `td` ）、其名稱（） `szName` ，以及選擇性的簽章（）來指定成員 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="67eb3-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="67eb3-114">類別或介面中可能有多個具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="67eb3-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="67eb3-115">在此情況下，請傳遞成員的簽章來尋找唯一的相符項。</span><span class="sxs-lookup"><span data-stu-id="67eb3-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="67eb3-116">傳遞至的簽章 `FindMember` 必須已在目前的範圍中產生，因為簽章已系結至特定範圍。</span><span class="sxs-lookup"><span data-stu-id="67eb3-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="67eb3-117">簽章可以內嵌可識別封閉類別或實數值型別的 token。</span><span class="sxs-lookup"><span data-stu-id="67eb3-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="67eb3-118">Token 是本機 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="67eb3-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="67eb3-119">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入來輸入至 `FindMember` 。</span><span class="sxs-lookup"><span data-stu-id="67eb3-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="67eb3-120">`FindMember`只尋找直接定義于類別或介面中的成員;它找不到繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="67eb3-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67eb3-121">`FindMember`是 helper 方法。</span><span class="sxs-lookup"><span data-stu-id="67eb3-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="67eb3-122">它會呼叫[IMetaDataImport：： FindMethod](imetadataimport-findmethod-method.md);如果該呼叫找不到相符的， `FindMember` 則會呼叫[IMetaDataImport：： FindField](imetadataimport-findfield-method.md)。</span><span class="sxs-lookup"><span data-stu-id="67eb3-122">It calls [IMetaDataImport::FindMethod](imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67eb3-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="67eb3-123">Requirements</span></span>  
 <span data-ttu-id="67eb3-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67eb3-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67eb3-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="67eb3-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67eb3-126">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="67eb3-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67eb3-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67eb3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67eb3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67eb3-128">See also</span></span>

- [<span data-ttu-id="67eb3-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="67eb3-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="67eb3-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="67eb3-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
