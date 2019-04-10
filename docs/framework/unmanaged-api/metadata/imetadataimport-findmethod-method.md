---
title: IMetaDataImport::FindMethod 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28aa8313e7ba0c071187d0f1f6d78431b16fc005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164797"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="255fc-102">IMetaDataImport::FindMethod 方法</span><span class="sxs-lookup"><span data-stu-id="255fc-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="255fc-103">取得指標的 MethodDef 語彙基元的方法，以指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="255fc-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="255fc-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="255fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="255fc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="255fc-106">[in]`mdTypeDef`括住要搜尋之成員的類型 （類別或介面） 的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="255fc-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="255fc-107">如果此值為`mdTokenNil`，則會在完成查詢的全域函式。</span><span class="sxs-lookup"><span data-stu-id="255fc-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="255fc-108">[in]要搜尋的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="255fc-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="255fc-109">[in]二進位中繼資料簽章方法的指標。</span><span class="sxs-lookup"><span data-stu-id="255fc-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="255fc-110">[in]以位元組為單位的大小`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="255fc-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="255fc-111">[out]比對的 MethodDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="255fc-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="255fc-112">備註</span><span class="sxs-lookup"><span data-stu-id="255fc-112">Remarks</span></span>  
 <span data-ttu-id="255fc-113">指定使用其封入類別或介面的方法 (`td`)，其名稱 (`szName`)，和 （選擇性） 其簽章 (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="255fc-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="255fc-114">可能有多個具有相同名稱的類別或介面中的方法。</span><span class="sxs-lookup"><span data-stu-id="255fc-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="255fc-115">在此情況下，傳遞方法的簽章，以尋找唯一相符項目。</span><span class="sxs-lookup"><span data-stu-id="255fc-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="255fc-116">簽章傳遞至`FindMethod`必須已產生在目前的範圍內，因為簽章會繫結至特定的範圍。</span><span class="sxs-lookup"><span data-stu-id="255fc-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="255fc-117">簽章可以內嵌識別封入類別或實值類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="255fc-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="255fc-118">語彙基元是本機 TypeDef 資訊表內的索引。</span><span class="sxs-lookup"><span data-stu-id="255fc-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="255fc-119">您無法建置目前範圍的內容以外的執行階段簽章，並使用該簽章為輸入至輸入`FindMethod`。</span><span class="sxs-lookup"><span data-stu-id="255fc-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 `FindMethod` <span data-ttu-id="255fc-120">尋找直接在類別或介面中所定義的方法找不到繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="255fc-120">finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="255fc-121">需求</span><span class="sxs-lookup"><span data-stu-id="255fc-121">Requirements</span></span>  
 <span data-ttu-id="255fc-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="255fc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="255fc-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="255fc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="255fc-124">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="255fc-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="255fc-125">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="255fc-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="255fc-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="255fc-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="255fc-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="255fc-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="255fc-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="255fc-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
