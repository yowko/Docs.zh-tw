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
ms.openlocfilehash: c2ec907759a25048444ebcc81bf5bb0fd23ced58
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503649"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="24fab-102">IMetaDataImport::FindMethod 方法</span><span class="sxs-lookup"><span data-stu-id="24fab-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="24fab-103">取得方法之 MethodDef token 的指標，這個標記是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="24fab-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24fab-104">語法</span><span class="sxs-lookup"><span data-stu-id="24fab-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24fab-105">參數</span><span class="sxs-lookup"><span data-stu-id="24fab-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="24fab-106">在用 `mdTypeDef` 來括住要搜尋之成員的類型（類別或介面）的 token。</span><span class="sxs-lookup"><span data-stu-id="24fab-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="24fab-107">如果這個值為 `mdTokenNil` ，則會針對全域函式進行查閱。</span><span class="sxs-lookup"><span data-stu-id="24fab-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="24fab-108">在要搜尋之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="24fab-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="24fab-109">在方法之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="24fab-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="24fab-110">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="24fab-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="24fab-111">脫銷相符的 MethodDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="24fab-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24fab-112">備註</span><span class="sxs-lookup"><span data-stu-id="24fab-112">Remarks</span></span>  
 <span data-ttu-id="24fab-113">您可以使用它的封入類別或介面（ `td` ）、它的名稱（） `szName` ，以及選擇性的簽章（）來指定方法 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="24fab-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="24fab-114">在類別或介面中，可能會有多個方法具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="24fab-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="24fab-115">在此情況下，請傳遞方法的簽章，以尋找唯一的相符項。</span><span class="sxs-lookup"><span data-stu-id="24fab-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="24fab-116">傳遞至的簽章 `FindMethod` 必須已在目前的範圍中產生，因為簽章已系結至特定範圍。</span><span class="sxs-lookup"><span data-stu-id="24fab-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="24fab-117">簽章可以內嵌可識別封閉類別或實數值型別的 token。</span><span class="sxs-lookup"><span data-stu-id="24fab-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="24fab-118">Token 是本機 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="24fab-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="24fab-119">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入來輸入至 `FindMethod` 。</span><span class="sxs-lookup"><span data-stu-id="24fab-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="24fab-120">`FindMethod`只尋找直接定義于類別或介面中的方法;但找不到繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="24fab-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24fab-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="24fab-121">Requirements</span></span>  
 <span data-ttu-id="24fab-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24fab-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24fab-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="24fab-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24fab-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="24fab-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24fab-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24fab-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24fab-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24fab-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="24fab-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="24fab-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="24fab-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="24fab-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
