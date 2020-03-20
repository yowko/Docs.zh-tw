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
ms.openlocfilehash: 23a6931b31ea2d7e4e8d1cb3dc8adf3a51216315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175742"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="f03b7-102">IMetaDataEmit::DefineTypeRefByName 方法</span><span class="sxs-lookup"><span data-stu-id="f03b7-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="f03b7-103">獲取在指定作用域中定義的類型的中繼資料權杖，該類型在當前作用域之外。</span><span class="sxs-lookup"><span data-stu-id="f03b7-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f03b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f03b7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f03b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="f03b7-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="f03b7-106">[在]指定解析作用域的權杖。</span><span class="sxs-lookup"><span data-stu-id="f03b7-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="f03b7-107">以下權杖類型有效：</span><span class="sxs-lookup"><span data-stu-id="f03b7-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="f03b7-108">`mdModuleRef`，如果類型是在定義調用方的同一程式集中定義的。</span><span class="sxs-lookup"><span data-stu-id="f03b7-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="f03b7-109">`mdAssemblyRef`，如果類型是在定義調用方的程式集以外的程式集中定義的。</span><span class="sxs-lookup"><span data-stu-id="f03b7-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="f03b7-110">`mdTypeRef`，如果類型是巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="f03b7-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="f03b7-111">`mdModule`，如果類型是在定義調用方的同一模組中定義的。</span><span class="sxs-lookup"><span data-stu-id="f03b7-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="f03b7-112">如果類型是全域定義的，則為 null。</span><span class="sxs-lookup"><span data-stu-id="f03b7-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="f03b7-113">[在]Unicode 中的目標型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="f03b7-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f03b7-114">[出]指向分配給類型的`mdTypeRef`權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="f03b7-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f03b7-115">需求</span><span class="sxs-lookup"><span data-stu-id="f03b7-115">Requirements</span></span>  
 <span data-ttu-id="f03b7-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f03b7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f03b7-117">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="f03b7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f03b7-118">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f03b7-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f03b7-119">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f03b7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03b7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f03b7-120">See also</span></span>

- [<span data-ttu-id="f03b7-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f03b7-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f03b7-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f03b7-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
