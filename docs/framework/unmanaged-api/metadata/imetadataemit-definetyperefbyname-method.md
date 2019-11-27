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
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434377"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="74e34-102">IMetaDataEmit::DefineTypeRefByName 方法</span><span class="sxs-lookup"><span data-stu-id="74e34-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="74e34-103">取得在指定的範圍中定義之類型的元資料標記，這不在目前的範圍內。</span><span class="sxs-lookup"><span data-stu-id="74e34-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e34-104">語法</span><span class="sxs-lookup"><span data-stu-id="74e34-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74e34-105">參數</span><span class="sxs-lookup"><span data-stu-id="74e34-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="74e34-106">在指定解析範圍的 token。</span><span class="sxs-lookup"><span data-stu-id="74e34-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="74e34-107">下列 token 類型有效：</span><span class="sxs-lookup"><span data-stu-id="74e34-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="74e34-108">`mdModuleRef`，如果類型定義于定義呼叫者的相同元件中。</span><span class="sxs-lookup"><span data-stu-id="74e34-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="74e34-109">`mdAssemblyRef`，如果類型是在定義呼叫者的元件中定義的，則為。</span><span class="sxs-lookup"><span data-stu-id="74e34-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="74e34-110">`mdTypeRef`，如果型別是嵌套型別，則為。</span><span class="sxs-lookup"><span data-stu-id="74e34-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="74e34-111">如果類型定義于定義呼叫者的相同模組中，`mdModule`。</span><span class="sxs-lookup"><span data-stu-id="74e34-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="74e34-112">如果是全域定義的類型，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="74e34-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="74e34-113">在Unicode 中目標型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="74e34-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="74e34-114">脫銷指派給類型之 `mdTypeRef` token 的指標。</span><span class="sxs-lookup"><span data-stu-id="74e34-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74e34-115">需求</span><span class="sxs-lookup"><span data-stu-id="74e34-115">Requirements</span></span>  
 <span data-ttu-id="74e34-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74e34-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e34-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="74e34-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74e34-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="74e34-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74e34-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e34-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e34-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="74e34-120">See also</span></span>

- [<span data-ttu-id="74e34-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="74e34-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="74e34-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="74e34-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
