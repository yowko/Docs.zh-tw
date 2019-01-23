---
title: IMetaDataImport::FindField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b07d75b6a8839f9a223ef2c0be52830e107e4088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527597"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="da1da-102">IMetaDataImport::FindField 方法</span><span class="sxs-lookup"><span data-stu-id="da1da-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="da1da-103">取得指標 FieldDef 語彙基元的欄位，以指定<xref:System.Type>且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="da1da-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da1da-104">語法</span><span class="sxs-lookup"><span data-stu-id="da1da-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da1da-105">參數</span><span class="sxs-lookup"><span data-stu-id="da1da-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="da1da-106">[in]類別或介面，包含要搜尋的欄位之 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="da1da-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="da1da-107">如果此值為`mdTokenNil`，會在完成查詢的全域變數。</span><span class="sxs-lookup"><span data-stu-id="da1da-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="da1da-108">[in]要搜尋的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="da1da-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="da1da-109">[in]二進位中繼資料簽章欄位的指標。</span><span class="sxs-lookup"><span data-stu-id="da1da-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="da1da-110">[in]以位元組為單位的大小`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="da1da-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="da1da-111">[out]比對的 FieldDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="da1da-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da1da-112">備註</span><span class="sxs-lookup"><span data-stu-id="da1da-112">Remarks</span></span>  
 <span data-ttu-id="da1da-113">指定使用其封入類別或介面的欄位 (`td`)，其名稱 (`szName`)，和 （選擇性） 其簽章 (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="da1da-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="da1da-114">簽章傳遞至`FindField`必須已產生在目前的範圍內，因為簽章會繫結至特定的範圍。</span><span class="sxs-lookup"><span data-stu-id="da1da-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="da1da-115">簽章可以內嵌識別封入類別或實值類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="da1da-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="da1da-116">（語彙基元，為區域 TypeDef 資訊表內的索引）。</span><span class="sxs-lookup"><span data-stu-id="da1da-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="da1da-117">您無法建置目前範圍的內容以外的執行階段簽章，並使用該簽章，做為輸入`FindField`。</span><span class="sxs-lookup"><span data-stu-id="da1da-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="da1da-118">`FindField` 尋找直接在類別或介面中所定義的欄位找不到繼承的欄位。</span><span class="sxs-lookup"><span data-stu-id="da1da-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da1da-119">需求</span><span class="sxs-lookup"><span data-stu-id="da1da-119">Requirements</span></span>  
 <span data-ttu-id="da1da-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da1da-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da1da-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="da1da-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da1da-122">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="da1da-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da1da-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da1da-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1da-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da1da-124">See also</span></span>
- [<span data-ttu-id="da1da-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="da1da-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="da1da-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="da1da-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
