---
title: IMetaDataEmit::DefineTypeRefByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4fd6102b65137a06009428c1245b80c0d44924a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445487"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="08de7-102">IMetaDataEmit::DefineTypeRefByName 方法</span><span class="sxs-lookup"><span data-stu-id="08de7-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="08de7-103">取得定義在指定範圍內，是在目前範圍之外的類型中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="08de7-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08de7-104">語法</span><span class="sxs-lookup"><span data-stu-id="08de7-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08de7-105">參數</span><span class="sxs-lookup"><span data-stu-id="08de7-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="08de7-106">[in]指定的解析範圍語彙基元。</span><span class="sxs-lookup"><span data-stu-id="08de7-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="08de7-107">下列語彙基元的型別是有效的：</span><span class="sxs-lookup"><span data-stu-id="08de7-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="08de7-108">`mdModuleRef`如果呼叫端定義所在的相同組件中定義的類型。</span><span class="sxs-lookup"><span data-stu-id="08de7-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="08de7-109">`mdAssemblyRef`如果呼叫端定義的非組件中定義類型。</span><span class="sxs-lookup"><span data-stu-id="08de7-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="08de7-110">`mdTypeRef`如果類型是巢狀的類型。</span><span class="sxs-lookup"><span data-stu-id="08de7-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="08de7-111">`mdModule`如果在呼叫端定義所在的相同模組中定義類型。</span><span class="sxs-lookup"><span data-stu-id="08de7-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="08de7-112">如果為 null，全域定義類型。</span><span class="sxs-lookup"><span data-stu-id="08de7-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="08de7-113">[in]以 Unicode 的目標類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="08de7-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="08de7-114">[out]指標`mdTypeRef`指派給類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="08de7-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08de7-115">需求</span><span class="sxs-lookup"><span data-stu-id="08de7-115">Requirements</span></span>  
 <span data-ttu-id="08de7-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08de7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08de7-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08de7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08de7-118">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="08de7-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08de7-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08de7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08de7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08de7-120">See Also</span></span>  
 [<span data-ttu-id="08de7-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="08de7-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="08de7-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="08de7-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
