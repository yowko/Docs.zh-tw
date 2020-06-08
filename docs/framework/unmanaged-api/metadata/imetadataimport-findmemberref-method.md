---
title: IMetaDataImport::FindMemberRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 068014732cee91147edaec29fa0f954a741d8b5c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491637"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="e0992-102">IMetaDataImport::FindMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="e0992-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="e0992-103">取得成員參考之 MemberRef token 的指標，此標記是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="e0992-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0992-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0992-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0992-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0992-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e0992-106">在類別或介面的 TypeRef token，用於括住要搜尋的成員參考。</span><span class="sxs-lookup"><span data-stu-id="e0992-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="e0992-107">如果這個值為 `mdTokenNil` ，則會針對全域變數或全域函式參考進行查閱。</span><span class="sxs-lookup"><span data-stu-id="e0992-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="e0992-108">在要搜尋之成員參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0992-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e0992-109">在成員參考之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="e0992-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e0992-110">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="e0992-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="e0992-111">脫銷符合的 MemberRef 標記的指標。</span><span class="sxs-lookup"><span data-stu-id="e0992-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0992-112">備註</span><span class="sxs-lookup"><span data-stu-id="e0992-112">Remarks</span></span>  
 <span data-ttu-id="e0992-113">您可以使用其封入類別或介面（ `td` ）、其名稱（） `szName` ，以及選擇性的簽章（）來指定成員 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="e0992-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="e0992-114">傳遞至的簽章 `FindMemberRef` 必須已在目前的範圍中產生，因為簽章已系結至特定範圍。</span><span class="sxs-lookup"><span data-stu-id="e0992-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="e0992-115">簽章可以內嵌可識別封閉類別或實數值型別的 token。</span><span class="sxs-lookup"><span data-stu-id="e0992-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="e0992-116">Token 是本機 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="e0992-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="e0992-117">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為的輸入 `FindMemberRef` 。</span><span class="sxs-lookup"><span data-stu-id="e0992-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="e0992-118">`FindMemberRef`只尋找直接定義于類別或介面中的成員參考;但找不到繼承的成員參考。</span><span class="sxs-lookup"><span data-stu-id="e0992-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0992-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="e0992-119">Requirements</span></span>  
 <span data-ttu-id="e0992-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0992-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0992-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e0992-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0992-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e0992-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0992-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0992-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0992-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0992-124">See also</span></span>

- [<span data-ttu-id="e0992-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e0992-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e0992-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e0992-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
