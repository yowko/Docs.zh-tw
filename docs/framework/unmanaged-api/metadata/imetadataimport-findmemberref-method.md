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
ms.openlocfilehash: 0ba25c981cc389baf06ecca0db543d48ac60317b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711399"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="0c85d-102">IMetaDataImport::FindMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="0c85d-102">IMetaDataImport::FindMemberRef Method</span></span>

<span data-ttu-id="0c85d-103">取得成員參考的 MemberRef 標記指標，該成員參考是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="0c85d-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c85d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c85d-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c85d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c85d-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="0c85d-106">在用來搜尋成員參考之類別或介面的 TypeRef 標記。</span><span class="sxs-lookup"><span data-stu-id="0c85d-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="0c85d-107">如果這個值為 `mdTokenNil` ，就會針對全域變數或全域函式參考來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="0c85d-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="0c85d-108">在要搜尋之成員參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c85d-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0c85d-109">在成員參考的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="0c85d-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0c85d-110">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="0c85d-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="0c85d-111">擴展相符的 MemberRef token 指標。</span><span class="sxs-lookup"><span data-stu-id="0c85d-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c85d-112">備註</span><span class="sxs-lookup"><span data-stu-id="0c85d-112">Remarks</span></span>  

 <span data-ttu-id="0c85d-113">您可以使用其封入類別或介面 (`td`) 、其名稱 (`szName`) ，以及選擇性的簽章 () ，來指定成員 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="0c85d-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="0c85d-114">傳遞給的簽章 `FindMemberRef` 必須在目前的範圍內產生，因為簽章會系結至特定的範圍。</span><span class="sxs-lookup"><span data-stu-id="0c85d-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="0c85d-115">簽章可以內嵌可識別封閉類別或實數值型別的標記。</span><span class="sxs-lookup"><span data-stu-id="0c85d-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="0c85d-116">Token 是本機 TypeDef 資料表中的索引。</span><span class="sxs-lookup"><span data-stu-id="0c85d-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="0c85d-117">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為的輸入 `FindMemberRef` 。</span><span class="sxs-lookup"><span data-stu-id="0c85d-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="0c85d-118">`FindMemberRef` 只尋找直接定義于類別或介面中的成員參考;找不到繼承的成員參考。</span><span class="sxs-lookup"><span data-stu-id="0c85d-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c85d-119">需求</span><span class="sxs-lookup"><span data-stu-id="0c85d-119">Requirements</span></span>  

 <span data-ttu-id="0c85d-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c85d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c85d-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="0c85d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c85d-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0c85d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c85d-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c85d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c85d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c85d-124">See also</span></span>

- [<span data-ttu-id="0c85d-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="0c85d-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0c85d-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="0c85d-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
