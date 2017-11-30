---
title: "IMetaDataImport::FindMemberRef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMemberRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: efb8a3a74997c6894eff6fafb87e933a6d2cf7bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="5982e-102">IMetaDataImport::FindMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="5982e-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="5982e-103">取得成員的 MemberRef 語彙基元的指標參考也就是加上指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="5982e-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5982e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5982e-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5982e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5982e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5982e-106">[in]類別或介面成員參考來搜尋圍住 TypeRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5982e-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="5982e-107">如果此值為`mdTokenNil`，查閱是為全域變數或全域函式的參考。</span><span class="sxs-lookup"><span data-stu-id="5982e-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="5982e-108">[in]若要搜尋的成員參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="5982e-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5982e-109">[in]成員參考的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="5982e-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5982e-110">[in]以位元組為單位的大小`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="5982e-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="5982e-111">[out]比對的 MemberRef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="5982e-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5982e-112">備註</span><span class="sxs-lookup"><span data-stu-id="5982e-112">Remarks</span></span>  
 <span data-ttu-id="5982e-113">指定使用其封入類別或介面的成員 (`td`)，其名稱 (`szName`)，以及 （選擇性） 其簽章 (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="5982e-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="5982e-114">簽章傳遞至`FindMemberRef`必須已產生中目前的範圍，因為簽章會繫結至特定範圍內。</span><span class="sxs-lookup"><span data-stu-id="5982e-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="5982e-115">簽章可以內嵌識別封入類別或實值類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5982e-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="5982e-116">語彙基元為區域 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="5982e-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="5982e-117">您無法建立在目前範圍的內容以外的執行階段簽章，並使用該簽章，做為輸入`FindMemberRef`。</span><span class="sxs-lookup"><span data-stu-id="5982e-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="5982e-118">`FindMemberRef`尋找定義類別或介面; 中的直接成員參考找不到繼承的成員的參考。</span><span class="sxs-lookup"><span data-stu-id="5982e-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5982e-119">需求</span><span class="sxs-lookup"><span data-stu-id="5982e-119">Requirements</span></span>  
 <span data-ttu-id="5982e-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5982e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5982e-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5982e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5982e-122">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5982e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5982e-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5982e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5982e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5982e-124">See Also</span></span>  
 [<span data-ttu-id="5982e-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5982e-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5982e-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5982e-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
