---
title: "IMetaDataImport::ResolveTypeRef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 390387abef5c48b4842adcfbfca126bb8292cc28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="e6d6f-102">IMetaDataImport::ResolveTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="e6d6f-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="e6d6f-103">解析<xref:System.Type>指定 TypeRef 語彙基元所代表的參考。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6d6f-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6d6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6d6f-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="e6d6f-106">[in]要傳回的參考型別資訊的 TypeRef 中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="e6d6f-107">[in]傳回介面的 IID `ppIScope`。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="e6d6f-108">通常，這會是 IID_IMetaDataImport。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="e6d6f-109">[out]要在其中定義參考的型別在模組範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="e6d6f-110">[out]表示參考的型別 TypeDef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6d6f-111">備註</span><span class="sxs-lookup"><span data-stu-id="e6d6f-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6d6f-112">如果載入多個應用程式定義域，則不使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="e6d6f-113">此方法不會遵守應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="e6d6f-114">如果多個版本的組件會載入，而它們包含具有相同的命名空間之相同類型，則方法會傳回模組範圍的第一個找到的類型。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="e6d6f-115">`ResolveTypeRef`方法搜尋的類型定義中其他模組。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="e6d6f-116">如果找到的類型定義，`ResolveTypeRef`讓介面返回該模組範圍，以及類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="e6d6f-117">如果要解析的型別參考已解析範圍的 AssemblyRef，`ResolveTypeRef`方法會搜尋相符項目只能在已經開啟與呼叫的中繼資料範圍[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法或[imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="e6d6f-118">這是因為`ResolveTypeRef`無法判斷從範圍僅限於 AssemblyRef 磁碟上或在全域組件快取組件儲存。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d6f-119">需求</span><span class="sxs-lookup"><span data-stu-id="e6d6f-119">Requirements</span></span>  
 <span data-ttu-id="e6d6f-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6d6f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d6f-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6d6f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6d6f-122">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e6d6f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6d6f-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d6f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d6f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6d6f-124">See Also</span></span>  
 [<span data-ttu-id="e6d6f-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e6d6f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e6d6f-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e6d6f-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
