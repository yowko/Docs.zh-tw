---
title: "IMetaDataImport::FindField 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2178f8738ca510fb2163c1043dd94ebcb7043904
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="8d1a6-102">IMetaDataImport::FindField 方法</span><span class="sxs-lookup"><span data-stu-id="8d1a6-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="8d1a6-103">取得 FieldDef 語彙基元指標，會包含該欄位指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d1a6-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d1a6-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d1a6-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d1a6-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8d1a6-106">[in]類別或介面包含要搜尋的欄位之 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="8d1a6-107">如果此值為`mdTokenNil`，查閱是為全域變數。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="8d1a6-108">[in]要搜尋的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8d1a6-109">[in]欄位的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8d1a6-110">[in]以位元組為單位的大小`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="8d1a6-111">[out]比對的 FieldDef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d1a6-112">備註</span><span class="sxs-lookup"><span data-stu-id="8d1a6-112">Remarks</span></span>  
 <span data-ttu-id="8d1a6-113">您指定使用其封入類別或介面的欄位 (`td`)，其名稱 (`szName`)，以及 （選擇性） 其簽章 (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="8d1a6-114">簽章傳遞至`FindField`必須已產生中目前的範圍，因為簽章會繫結至特定範圍內。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="8d1a6-115">簽章可以內嵌識別封入類別或實值類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="8d1a6-116">（語彙基元是本機的 TypeDef 資料表的索引）。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="8d1a6-117">您無法建立在目前範圍的內容以外的執行階段簽章，並使用該簽章，做為輸入`FindField`。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="8d1a6-118">`FindField`尋找已直接在類別或介面中定義的欄位找不到繼承的欄位。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d1a6-119">需求</span><span class="sxs-lookup"><span data-stu-id="8d1a6-119">Requirements</span></span>  
 <span data-ttu-id="8d1a6-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d1a6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d1a6-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8d1a6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d1a6-122">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d1a6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d1a6-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d1a6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d1a6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d1a6-124">See Also</span></span>  
 [<span data-ttu-id="8d1a6-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8d1a6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8d1a6-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8d1a6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
