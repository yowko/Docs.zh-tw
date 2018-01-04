---
title: "IMetaDataEmit::SetClassLayout 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0c02e615bf77a2cc9136b50efd7395585959141
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="2d1e7-102">IMetaDataEmit::SetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="2d1e7-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="2d1e7-103">完成欄位已由先前呼叫所定義之類別的配置[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d1e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d1e7-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d1e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d1e7-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="2d1e7-106">[in]`mdTypeDef`語彙基元，指定要配置的類別。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="2d1e7-107">[in]封裝大小： 1、 2、 4、 8 或 16 個位元組。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="2d1e7-108">封裝大小是相鄰的欄位之間的位元組數。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="2d1e7-109">[in]陣列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構，每個皆指定類別的欄位和欄位的位移在類別中。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="2d1e7-110">終止與陣列`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="2d1e7-111">[in]以位元組為單位，類別的大小。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d1e7-112">備註</span><span class="sxs-lookup"><span data-stu-id="2d1e7-112">Remarks</span></span>  
 <span data-ttu-id="2d1e7-113">藉由呼叫一開始定義類別[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法，並指定其中三個類別的欄位配置： 自動、 循序或明確。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="2d1e7-114">一般來說，您會使用自動配置，讓執行階段選擇欄位配置的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="2d1e7-115">不過，您可以根據 unmanaged 程式碼使用的排列方式配置的欄位。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="2d1e7-116">在此情況下，選擇 循序或明確的配置和呼叫`SetClassLayout`完成欄位的配置：</span><span class="sxs-lookup"><span data-stu-id="2d1e7-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="2d1e7-117">循序配置： 指定的封裝大小。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="2d1e7-118">欄位會根據其自然的大小或封裝大小，較小的欄位位移中的任何結果對齊。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="2d1e7-119">設定`rFieldOffsets`和`ulClassSize`為零。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="2d1e7-120">明確的配置： 指定每個欄位的位移，或指定類別和封裝大小。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d1e7-121">需求</span><span class="sxs-lookup"><span data-stu-id="2d1e7-121">Requirements</span></span>  
 <span data-ttu-id="2d1e7-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d1e7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d1e7-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d1e7-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d1e7-124">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2d1e7-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d1e7-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d1e7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1e7-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d1e7-126">See Also</span></span>  
 [<span data-ttu-id="2d1e7-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2d1e7-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2d1e7-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="2d1e7-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
