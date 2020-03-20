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
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177256"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="3cc15-102">IMetaDataImport::FindMethod 方法</span><span class="sxs-lookup"><span data-stu-id="3cc15-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="3cc15-103">獲取指向方法的指標，該方法由指定內容<xref:System.Type>封閉，並且具有指定的名稱和中繼資料簽名。</span><span class="sxs-lookup"><span data-stu-id="3cc15-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc15-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cc15-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc15-105">參數</span><span class="sxs-lookup"><span data-stu-id="3cc15-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3cc15-106">[在]包含`mdTypeDef`要搜索的成員的類型（類或介面）的權杖。</span><span class="sxs-lookup"><span data-stu-id="3cc15-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="3cc15-107">如果此值為`mdTokenNil`，則對全域函數執行查找。</span><span class="sxs-lookup"><span data-stu-id="3cc15-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="3cc15-108">[在]要搜索的方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cc15-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3cc15-109">[在]指向方法的二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="3cc15-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3cc15-110">[在]的大小（以位元組為單位）。 `pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="3cc15-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="3cc15-111">[出]指向匹配的 MethodDef 權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="3cc15-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cc15-112">備註</span><span class="sxs-lookup"><span data-stu-id="3cc15-112">Remarks</span></span>  
 <span data-ttu-id="3cc15-113">使用其封閉類或介面 （））`td``szName`和可選方式指定方法的簽名 （）。`pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="3cc15-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="3cc15-114">類或介面中可能有多個同名方法。</span><span class="sxs-lookup"><span data-stu-id="3cc15-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="3cc15-115">在這種情況下，傳遞方法的簽名以查找唯一匹配項。</span><span class="sxs-lookup"><span data-stu-id="3cc15-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="3cc15-116">傳遞給的簽名`FindMethod`必須在當前作用域中生成，因為簽名綁定到特定作用域。</span><span class="sxs-lookup"><span data-stu-id="3cc15-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="3cc15-117">簽名可以嵌入標識封閉類或數值型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="3cc15-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="3cc15-118">權杖是本地 TypeDef 表中的索引。</span><span class="sxs-lookup"><span data-stu-id="3cc15-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="3cc15-119">不能在當前作用域的上下文之外生成運行時簽名，並且使用該簽名作為輸入 到`FindMethod`的輸入。</span><span class="sxs-lookup"><span data-stu-id="3cc15-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="3cc15-120">`FindMethod`僅查找直接在類或介面中定義的方法;它找不到繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="3cc15-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc15-121">需求</span><span class="sxs-lookup"><span data-stu-id="3cc15-121">Requirements</span></span>  
 <span data-ttu-id="3cc15-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc15-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc15-123">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="3cc15-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cc15-124">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3cc15-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3cc15-125">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc15-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc15-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cc15-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="3cc15-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3cc15-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3cc15-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3cc15-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
