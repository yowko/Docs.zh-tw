---
title: IMetaDataImport::FindMember 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177274"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="ded28-102">IMetaDataImport::FindMember 方法</span><span class="sxs-lookup"><span data-stu-id="ded28-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="ded28-103">獲取指向成員Def權杖的指標，用於指定<xref:System.Type>內容所包含且具有指定名稱和中繼資料簽名的欄位或方法。</span><span class="sxs-lookup"><span data-stu-id="ded28-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded28-104">語法</span><span class="sxs-lookup"><span data-stu-id="ded28-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ded28-105">參數</span><span class="sxs-lookup"><span data-stu-id="ded28-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ded28-106">[在]包含要搜索的成員的類或介面的 TypeDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="ded28-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="ded28-107">如果此值為`mdTokenNil`，則查找將執行全域變數或全域函數。</span><span class="sxs-lookup"><span data-stu-id="ded28-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="ded28-108">[在]要搜索的成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="ded28-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ded28-109">[在]指向成員的二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="ded28-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ded28-110">[在]的大小（以位元組為單位）。 `pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="ded28-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="ded28-111">[出]指向匹配的會員Def權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="ded28-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ded28-112">備註</span><span class="sxs-lookup"><span data-stu-id="ded28-112">Remarks</span></span>  
 <span data-ttu-id="ded28-113">您可以使用其封閉類或介面 （））`td``szName`指定成員，並選擇其簽名 （）。`pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="ded28-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="ded28-114">類或介面中可能有多個具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="ded28-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="ded28-115">在這種情況下，傳遞成員的簽名以查找唯一匹配項。</span><span class="sxs-lookup"><span data-stu-id="ded28-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="ded28-116">傳遞給的簽名`FindMember`必須在當前作用域中生成，因為簽名綁定到特定作用域。</span><span class="sxs-lookup"><span data-stu-id="ded28-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="ded28-117">簽名可以嵌入標識封閉類或數值型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="ded28-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="ded28-118">權杖是本地 TypeDef 表中的索引。</span><span class="sxs-lookup"><span data-stu-id="ded28-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="ded28-119">不能在當前作用域的上下文之外生成運行時簽名，並且使用該簽名作為輸入 到`FindMember`的輸入。</span><span class="sxs-lookup"><span data-stu-id="ded28-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="ded28-120">`FindMember`僅查找直接在類或介面中定義的成員;它找不到繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="ded28-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ded28-121">`FindMember`是説明方法。</span><span class="sxs-lookup"><span data-stu-id="ded28-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="ded28-122">它調用[IMetaData 導入：：查找方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md);如果該呼叫找不到匹配項，`FindMember`則調用[IMetaDataImport：：FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ded28-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded28-123">需求</span><span class="sxs-lookup"><span data-stu-id="ded28-123">Requirements</span></span>  
 <span data-ttu-id="ded28-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ded28-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded28-125">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="ded28-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ded28-126">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ded28-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ded28-127">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ded28-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded28-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ded28-128">See also</span></span>

- [<span data-ttu-id="ded28-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ded28-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ded28-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ded28-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
