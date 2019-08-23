---
title: IMetaDataImport::ResolveTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f323e91e60c9735a51e955eaab6673ca167f294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951871"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="33667-102">IMetaDataImport::ResolveTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="33667-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="33667-103">解析指定的 TypeRef 標記所表示的參考。<xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="33667-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33667-104">語法</span><span class="sxs-lookup"><span data-stu-id="33667-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33667-105">參數</span><span class="sxs-lookup"><span data-stu-id="33667-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="33667-106">在要傳回之參考型別資訊的 TypeRef 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="33667-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="33667-107">在要在中`ppIScope`傳回之介面的 IID。</span><span class="sxs-lookup"><span data-stu-id="33667-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="33667-108">一般來說, 這會是 IID_IMetaDataImport。</span><span class="sxs-lookup"><span data-stu-id="33667-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="33667-109">脫銷定義參考型別之模組範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="33667-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="33667-110">脫銷表示參考型別之 TypeDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="33667-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33667-111">備註</span><span class="sxs-lookup"><span data-stu-id="33667-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="33667-112">如果載入多個應用程式域, 請勿使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="33667-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="33667-113">方法不會遵守應用程式域界限。</span><span class="sxs-lookup"><span data-stu-id="33667-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="33667-114">如果載入元件的多個版本, 而且它們包含具有相同命名空間的相同類型, 則方法會傳回所找到之第一個類型的模組範圍。</span><span class="sxs-lookup"><span data-stu-id="33667-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="33667-115">`ResolveTypeRef`方法會搜尋其他模組中的型別定義。</span><span class="sxs-lookup"><span data-stu-id="33667-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="33667-116">如果找到類型定義, `ResolveTypeRef`則會傳回該模組範圍的介面, 以及該類型的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="33667-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="33667-117">如果要解析的類型參考具有 AssemblyRef 的解析範圍, 此`ResolveTypeRef`方法只會搜尋已經使用[IMetaDataDispenser:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法或[的呼叫來開啟的中繼資料範圍中的相符項IMetaDataDispenser:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="33667-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="33667-118">這是因為`ResolveTypeRef`無法只從磁片或全域組件快取中儲存元件的 AssemblyRef 範圍判斷。</span><span class="sxs-lookup"><span data-stu-id="33667-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33667-119">需求</span><span class="sxs-lookup"><span data-stu-id="33667-119">Requirements</span></span>  
 <span data-ttu-id="33667-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33667-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33667-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="33667-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33667-122">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="33667-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33667-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33667-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33667-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33667-124">See also</span></span>

- [<span data-ttu-id="33667-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="33667-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="33667-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="33667-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
