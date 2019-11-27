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
ms.openlocfilehash: 59512cc1c1b280d7fe6deb2f9d721ad53547e356
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437964"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="3bc81-102">IMetaDataImport::FindMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="3bc81-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="3bc81-103">取得成員參考之 MemberRef token 的指標，此標記是由指定的 <xref:System.Type> 所括住，而且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="3bc81-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc81-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bc81-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bc81-105">參數</span><span class="sxs-lookup"><span data-stu-id="3bc81-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3bc81-106">在類別或介面的 TypeRef token，用於括住要搜尋的成員參考。</span><span class="sxs-lookup"><span data-stu-id="3bc81-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="3bc81-107">如果這個值是 `mdTokenNil`，就會針對全域變數或全域函式參考來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="3bc81-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="3bc81-108">在要搜尋之成員參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bc81-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3bc81-109">在成員參考之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="3bc81-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3bc81-110">在`pvSigBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3bc81-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="3bc81-111">脫銷符合的 MemberRef 標記的指標。</span><span class="sxs-lookup"><span data-stu-id="3bc81-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bc81-112">備註</span><span class="sxs-lookup"><span data-stu-id="3bc81-112">Remarks</span></span>  
 <span data-ttu-id="3bc81-113">您可以使用其封入類別或介面（`td`）、其名稱（`szName`），以及選擇性的簽章（`pvSigBlob`）來指定成員。</span><span class="sxs-lookup"><span data-stu-id="3bc81-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="3bc81-114">傳遞給 `FindMemberRef` 的簽章必須已在目前的範圍中產生，因為簽章已系結至特定範圍。</span><span class="sxs-lookup"><span data-stu-id="3bc81-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="3bc81-115">簽章可以內嵌可識別封閉類別或實數值型別的 token。</span><span class="sxs-lookup"><span data-stu-id="3bc81-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="3bc81-116">Token 是本機 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="3bc81-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="3bc81-117">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為 `FindMemberRef`的輸入。</span><span class="sxs-lookup"><span data-stu-id="3bc81-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="3bc81-118">`FindMemberRef` 只會尋找直接定義于類別或介面中的成員參考;但找不到繼承的成員參考。</span><span class="sxs-lookup"><span data-stu-id="3bc81-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bc81-119">需求</span><span class="sxs-lookup"><span data-stu-id="3bc81-119">Requirements</span></span>  
 <span data-ttu-id="3bc81-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bc81-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bc81-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3bc81-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3bc81-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3bc81-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3bc81-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bc81-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bc81-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="3bc81-124">See also</span></span>

- [<span data-ttu-id="3bc81-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3bc81-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3bc81-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3bc81-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
