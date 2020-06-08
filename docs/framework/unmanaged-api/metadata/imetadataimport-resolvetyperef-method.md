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
ms.openlocfilehash: f55af87e21b48430807166cb03e1d41271e830a1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503428"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="5a8aa-102">IMetaDataImport::ResolveTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="5a8aa-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="5a8aa-103">解析 <xref:System.Type> 指定的 TypeRef 標記所表示的參考。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a8aa-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a8aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a8aa-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="5a8aa-106">在要傳回之參考型別資訊的 TypeRef 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="5a8aa-107">在要在中傳回之介面的 IID `ppIScope` 。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="5a8aa-108">一般來說，這會是 IID_IMetaDataImport。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="5a8aa-109">脫銷定義參考型別之模組範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5a8aa-110">脫銷表示參考型別之 TypeDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a8aa-111">備註</span><span class="sxs-lookup"><span data-stu-id="5a8aa-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5a8aa-112">如果載入多個應用程式域，請勿使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="5a8aa-113">方法不會遵守應用程式域界限。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="5a8aa-114">如果載入元件的多個版本，而且它們包含具有相同命名空間的相同類型，則方法會傳回所找到之第一個類型的模組範圍。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="5a8aa-115">`ResolveTypeRef`方法會搜尋其他模組中的型別定義。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="5a8aa-116">如果找到類型定義，則會傳回 `ResolveTypeRef` 該模組範圍的介面，以及該類型的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="5a8aa-117">如果要解析的類型參考具有 AssemblyRef 的解析範圍，此 `ResolveTypeRef` 方法只會搜尋已經使用[IMetaDataDispenser：： OpenScope](imetadatadispenser-openscope-method.md)方法或[IMetaDataDispenser：： OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md)方法的呼叫開啟的中繼資料範圍中的相符項。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="5a8aa-118">這是因為 `ResolveTypeRef` 無法只從磁片或全域組件快取中儲存元件的 AssemblyRef 範圍判斷。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a8aa-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="5a8aa-119">Requirements</span></span>  
 <span data-ttu-id="5a8aa-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8aa-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a8aa-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5a8aa-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a8aa-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5a8aa-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a8aa-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a8aa-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8aa-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a8aa-124">See also</span></span>

- [<span data-ttu-id="5a8aa-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5a8aa-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5a8aa-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5a8aa-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
