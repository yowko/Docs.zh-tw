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
ms.openlocfilehash: bcd9499d0aef34fb34065ed58c0f0d69cc4ecedc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711438"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="e0970-102">IMetaDataImport::FindMember 方法</span><span class="sxs-lookup"><span data-stu-id="e0970-102">IMetaDataImport::FindMember Method</span></span>

<span data-ttu-id="e0970-103">取得欄位或方法的 MemberDef token 指標，這個欄位或方法是由指定的 <xref:System.Type> ，且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="e0970-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0970-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0970-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0970-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0970-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="e0970-106">在包含要搜尋之成員之類別或介面的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="e0970-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="e0970-107">如果這個值為 `mdTokenNil` ，則會對全域變數或全域函式進行查閱。</span><span class="sxs-lookup"><span data-stu-id="e0970-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="e0970-108">在要搜尋之成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0970-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e0970-109">在成員的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="e0970-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e0970-110">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="e0970-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="e0970-111">擴展相符 MemberDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="e0970-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0970-112">備註</span><span class="sxs-lookup"><span data-stu-id="e0970-112">Remarks</span></span>  

 <span data-ttu-id="e0970-113">您可以使用其封入類別或介面 (`td`) 、其名稱 (`szName`) ，以及選擇性的簽章 () ，來指定成員 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="e0970-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="e0970-114">類別或介面中可能有多個相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="e0970-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="e0970-115">在此情況下，請傳遞成員的簽章，以找出唯一的相符項。</span><span class="sxs-lookup"><span data-stu-id="e0970-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="e0970-116">傳遞給的簽章 `FindMember` 必須在目前的範圍內產生，因為簽章會系結至特定的範圍。</span><span class="sxs-lookup"><span data-stu-id="e0970-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="e0970-117">簽章可以內嵌可識別封閉類別或實數值型別的標記。</span><span class="sxs-lookup"><span data-stu-id="e0970-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="e0970-118">Token 是本機 TypeDef 資料表中的索引。</span><span class="sxs-lookup"><span data-stu-id="e0970-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="e0970-119">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入的輸入 `FindMember` 。</span><span class="sxs-lookup"><span data-stu-id="e0970-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="e0970-120">`FindMember` 只尋找直接定義于類別或介面中的成員;找不到繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="e0970-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0970-121">`FindMember` 是 helper 方法。</span><span class="sxs-lookup"><span data-stu-id="e0970-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="e0970-122">它會呼叫 [IMetaDataImport：： FindMethod](imetadataimport-findmethod-method.md);如果該呼叫找不到相符的， `FindMember` 則會呼叫 [IMetaDataImport：： FindField](imetadataimport-findfield-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e0970-122">It calls [IMetaDataImport::FindMethod](imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0970-123">需求</span><span class="sxs-lookup"><span data-stu-id="e0970-123">Requirements</span></span>  

 <span data-ttu-id="e0970-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0970-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0970-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e0970-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0970-126">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e0970-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0970-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0970-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0970-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0970-128">See also</span></span>

- [<span data-ttu-id="e0970-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e0970-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e0970-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e0970-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
