---
title: "IMetaDataEmit::DefineTypeDef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeDef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8fed37605252139428aa40bb3785c242d95cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="72d28-102">IMetaDataEmit::DefineTypeDef 方法</span><span class="sxs-lookup"><span data-stu-id="72d28-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="72d28-103">建立型別定義為 common language runtime 類型，並取得該型別定義的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="72d28-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72d28-104">語法</span><span class="sxs-lookup"><span data-stu-id="72d28-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72d28-105">參數</span><span class="sxs-lookup"><span data-stu-id="72d28-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="72d28-106">[in]以 Unicode 的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="72d28-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="72d28-107">[in]`TypeDef`屬性。</span><span class="sxs-lookup"><span data-stu-id="72d28-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="72d28-108">這是位元遮罩`CoreTypeAttr`值。</span><span class="sxs-lookup"><span data-stu-id="72d28-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="72d28-109">[in]基底類別的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="72d28-109">[in] The token of the base class.</span></span> <span data-ttu-id="72d28-110">它必須是`mdTypeDef`或`mdTypeRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="72d28-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="72d28-111">[in]指定此類別或介面實作的介面的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="72d28-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="72d28-112">[out]`mdTypeDef`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="72d28-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72d28-113">備註</span><span class="sxs-lookup"><span data-stu-id="72d28-113">Remarks</span></span>  
 <span data-ttu-id="72d28-114">中的旗標`dwTypeDefFlags`指定正在建立的類型是否為一般類型系統參考類型 （類別或介面） 或一般類型系統實值類型。</span><span class="sxs-lookup"><span data-stu-id="72d28-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="72d28-115">根據提供的參數，這個方法，副作用，也可能會建立`mdInterfaceImpl`記錄每個介面繼承，或由此類型實作。</span><span class="sxs-lookup"><span data-stu-id="72d28-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="72d28-116">不過，這個方法不會傳回任何一項都`mdInterfaceImpl`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="72d28-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="72d28-117">如果用戶端想要稍後加入或修改`mdInterfaceImpl`語彙基元，必須使用`IMetaDataImport`介面加以列舉。</span><span class="sxs-lookup"><span data-stu-id="72d28-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="72d28-118">如果您想要使用的 COM 語意`[default]`介面，您應該提供的預設介面中的第一個項目作為`rtkImplements`; 在類別上設定的自訂屬性會指示此類別具有預設介面 (一律會假設為第一次`mdInterfaceImpl`類別宣告的權杖)。</span><span class="sxs-lookup"><span data-stu-id="72d28-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="72d28-119">每個項目`rtkImplements`陣列保留`mdTypeDef`或`mdTypeRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="72d28-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="72d28-120">陣列中的最後一個項目必須是`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="72d28-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72d28-121">需求</span><span class="sxs-lookup"><span data-stu-id="72d28-121">Requirements</span></span>  
 <span data-ttu-id="72d28-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72d28-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72d28-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72d28-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72d28-124">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="72d28-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72d28-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72d28-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d28-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="72d28-126">See Also</span></span>  
 [<span data-ttu-id="72d28-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="72d28-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="72d28-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="72d28-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
