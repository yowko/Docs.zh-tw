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
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437892"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="d0a0c-102">IMetaDataImport::FindMethod 方法</span><span class="sxs-lookup"><span data-stu-id="d0a0c-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="d0a0c-103">取得方法的 MethodDef 標記指標，此方法是由指定的 <xref:System.Type> 所括住，而且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0a0c-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0a0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0a0c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d0a0c-106">在用來括住要搜尋之成員的類型（類別或介面）的 `mdTypeDef` token。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="d0a0c-107">如果 `mdTokenNil`這個值，則會針對全域函式進行查閱。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="d0a0c-108">在要搜尋之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d0a0c-109">在方法之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d0a0c-110">在`pvSigBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="d0a0c-111">脫銷相符的 MethodDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0a0c-112">備註</span><span class="sxs-lookup"><span data-stu-id="d0a0c-112">Remarks</span></span>  
 <span data-ttu-id="d0a0c-113">您可以使用它的封入類別或介面（`td`）、其名稱（`szName`），以及選擇性的簽章（`pvSigBlob`）來指定方法。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="d0a0c-114">在類別或介面中，可能會有多個方法具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="d0a0c-115">在此情況下，請傳遞方法的簽章，以尋找唯一的相符項。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="d0a0c-116">傳遞給 `FindMethod` 的簽章必須已在目前的範圍中產生，因為簽章已系結至特定範圍。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d0a0c-117">簽章可以內嵌可識別封閉類別或實數值型別的 token。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d0a0c-118">Token 是本機 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="d0a0c-119">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為輸入來 `FindMethod`。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="d0a0c-120">`FindMethod` 只會尋找直接定義于類別或介面中的方法;但找不到繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a0c-121">需求</span><span class="sxs-lookup"><span data-stu-id="d0a0c-121">Requirements</span></span>  
 <span data-ttu-id="d0a0c-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a0c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0a0c-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d0a0c-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0a0c-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d0a0c-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0a0c-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0a0c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a0c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0a0c-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="d0a0c-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d0a0c-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d0a0c-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d0a0c-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
