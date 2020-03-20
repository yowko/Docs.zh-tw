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
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175417"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="2da66-102">IMetaDataImport::FindMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="2da66-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="2da66-103">獲取指向成員參考的指向成員Ref 權杖的指標，該引用由指定內容<xref:System.Type>所封閉，並且具有指定的名稱和中繼資料簽名。</span><span class="sxs-lookup"><span data-stu-id="2da66-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2da66-104">語法</span><span class="sxs-lookup"><span data-stu-id="2da66-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2da66-105">參數</span><span class="sxs-lookup"><span data-stu-id="2da66-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="2da66-106">[在]包含要搜索的成員引用的類或介面的 TypeRef 權杖。</span><span class="sxs-lookup"><span data-stu-id="2da66-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="2da66-107">如果此值為`mdTokenNil`，則查找將執行全域變數或全域函數引用。</span><span class="sxs-lookup"><span data-stu-id="2da66-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="2da66-108">[在]要搜索的成員引用的名稱。</span><span class="sxs-lookup"><span data-stu-id="2da66-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="2da66-109">[在]指向成員引用的二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="2da66-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="2da66-110">[在]的大小（以位元組為單位）。 `pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="2da66-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="2da66-111">[出]指向匹配的會員Ref權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="2da66-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2da66-112">備註</span><span class="sxs-lookup"><span data-stu-id="2da66-112">Remarks</span></span>  
 <span data-ttu-id="2da66-113">您可以使用其封閉類或介面 （））`td``szName`指定成員，並選擇其簽名 （）。`pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="2da66-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="2da66-114">傳遞給的簽名`FindMemberRef`必須在當前作用域中生成，因為簽名綁定到特定作用域。</span><span class="sxs-lookup"><span data-stu-id="2da66-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="2da66-115">簽名可以嵌入標識封閉類或數值型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="2da66-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="2da66-116">權杖是本地 TypeDef 表中的索引。</span><span class="sxs-lookup"><span data-stu-id="2da66-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="2da66-117">不能在當前作用域的上下文之外生成運行時簽名，並且使用該簽名作為 輸入`FindMemberRef`。</span><span class="sxs-lookup"><span data-stu-id="2da66-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="2da66-118">`FindMemberRef`僅查找直接在類或介面中定義的成員引用;它找不到繼承的成員引用。</span><span class="sxs-lookup"><span data-stu-id="2da66-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2da66-119">需求</span><span class="sxs-lookup"><span data-stu-id="2da66-119">Requirements</span></span>  
 <span data-ttu-id="2da66-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2da66-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2da66-121">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="2da66-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2da66-122">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2da66-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2da66-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2da66-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da66-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2da66-124">See also</span></span>

- [<span data-ttu-id="2da66-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2da66-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2da66-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2da66-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
