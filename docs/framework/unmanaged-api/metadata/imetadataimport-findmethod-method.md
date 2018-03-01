---
title: "IMetaDataImport::FindMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e59cc440ba004545c31d6b25d36cca4fdfb58899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="670c3-102">IMetaDataImport::FindMethod 方法</span><span class="sxs-lookup"><span data-stu-id="670c3-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="670c3-103">取得指標 methoddef 語彙基元的方法，以指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="670c3-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="670c3-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="670c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="670c3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="670c3-106">[in]`mdTypeDef`內含要搜尋之成員的類型 （類別或介面） 的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="670c3-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="670c3-107">如果此值為`mdTokenNil`，則查閱是為全域函式。</span><span class="sxs-lookup"><span data-stu-id="670c3-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="670c3-108">[in]若要搜尋方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="670c3-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="670c3-109">[in]方法的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="670c3-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="670c3-110">[in]以位元組為單位的大小`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="670c3-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="670c3-111">[out]比對的 MethodDef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="670c3-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="670c3-112">備註</span><span class="sxs-lookup"><span data-stu-id="670c3-112">Remarks</span></span>  
 <span data-ttu-id="670c3-113">指定封入的類別或介面的方法 (`td`)，其名稱 (`szName`)，以及 （選擇性） 其簽章 (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="670c3-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="670c3-114">可能會有多個具有相同名稱的類別或介面中的方法。</span><span class="sxs-lookup"><span data-stu-id="670c3-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="670c3-115">在此情況下，傳遞方法的簽章，以尋找唯一的符合項目。</span><span class="sxs-lookup"><span data-stu-id="670c3-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="670c3-116">簽章傳遞至`FindMethod`必須已產生中目前的範圍，因為簽章會繫結至特定範圍內。</span><span class="sxs-lookup"><span data-stu-id="670c3-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="670c3-117">簽章可以內嵌識別封入類別或實值類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="670c3-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="670c3-118">語彙基元為區域 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="670c3-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="670c3-119">您無法建立在目前範圍的內容以外的執行階段簽章，並使用該簽章為輸入到輸入`FindMethod`。</span><span class="sxs-lookup"><span data-stu-id="670c3-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="670c3-120">`FindMethod`尋找定義類別或介面; 中的直接的方法找不到繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="670c3-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="670c3-121">需求</span><span class="sxs-lookup"><span data-stu-id="670c3-121">Requirements</span></span>  
 <span data-ttu-id="670c3-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="670c3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="670c3-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="670c3-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="670c3-124">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="670c3-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="670c3-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="670c3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="670c3-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="670c3-126">See Also</span></span>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="670c3-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="670c3-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="670c3-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="670c3-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
