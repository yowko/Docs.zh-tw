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
ms.openlocfilehash: b83c868f1a804d4e6f32adffc190ae086aa5e0a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719329"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="441ea-102">IMetaDataEmit::DefineTypeRefByName 方法</span><span class="sxs-lookup"><span data-stu-id="441ea-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>

<span data-ttu-id="441ea-103">取得指定範圍內所定義之類型的元資料標記，該類型在目前的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="441ea-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="441ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="441ea-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="441ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="441ea-105">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="441ea-106">在指定解析範圍的標記。</span><span class="sxs-lookup"><span data-stu-id="441ea-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="441ea-107">下列權杖類型有效：</span><span class="sxs-lookup"><span data-stu-id="441ea-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="441ea-108">`mdModuleRef`如果類型定義在定義呼叫端的相同元件中，則為。</span><span class="sxs-lookup"><span data-stu-id="441ea-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="441ea-109">`mdAssemblyRef`如果類型是在定義了呼叫端的元件以外的元件中定義的，則為。</span><span class="sxs-lookup"><span data-stu-id="441ea-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="441ea-110">`mdTypeRef`，如果類型為巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="441ea-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="441ea-111">`mdModule`如果類型是在定義呼叫端的相同模組中定義。</span><span class="sxs-lookup"><span data-stu-id="441ea-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="441ea-112">如果類型是全域定義，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="441ea-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="441ea-113">在Unicode 中目標型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="441ea-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="441ea-114">擴展指派給類型的 `mdTypeRef` 標記指標。</span><span class="sxs-lookup"><span data-stu-id="441ea-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="441ea-115">需求</span><span class="sxs-lookup"><span data-stu-id="441ea-115">Requirements</span></span>  

 <span data-ttu-id="441ea-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="441ea-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="441ea-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="441ea-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="441ea-118">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="441ea-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="441ea-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="441ea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441ea-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="441ea-120">See also</span></span>

- [<span data-ttu-id="441ea-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="441ea-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="441ea-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="441ea-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
