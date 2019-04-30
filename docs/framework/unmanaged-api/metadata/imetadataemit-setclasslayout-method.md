---
title: IMetaDataEmit::SetClassLayout 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bf9de3eb274bf536b2794ba2ed14e7e9b553cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050047"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="3d8fc-102">IMetaDataEmit::SetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="3d8fc-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="3d8fc-103">完成欄位已由先前呼叫所定義之類別的配置[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d8fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d8fc-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d8fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="3d8fc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3d8fc-106">[in]`mdTypeDef`語彙基元，指定要配置的類別。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="3d8fc-107">[in]封裝大小：1、 2、 4、 8 或 16 個位元組。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="3d8fc-108">封裝大小是相鄰的欄位之間的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="3d8fc-109">[in]陣列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構，其中每一個指定類別的欄位和欄位之間的時差，該類別內。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="3d8fc-110">終止陣列`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="3d8fc-111">[in]大小，以位元組為單位的類別。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d8fc-112">備註</span><span class="sxs-lookup"><span data-stu-id="3d8fc-112">Remarks</span></span>  
 <span data-ttu-id="3d8fc-113">一開始已定義類別，藉由呼叫[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法，並指定其中一個欄位的類別的三個配置： 自動、 循序或明確。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="3d8fc-114">一般來說，您會使用自動版面配置，並讓執行階段選擇最佳的方式來配置的欄位。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="3d8fc-115">不過，您可以根據程式碼會使用未受管理的排列方式配置的欄位。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="3d8fc-116">在此情況下，選擇 循序或明確的配置和呼叫`SetClassLayout`完成欄位的配置：</span><span class="sxs-lookup"><span data-stu-id="3d8fc-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="3d8fc-117">循序配置：指定封裝大小。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="3d8fc-118">欄位會根據其自然的大小或封裝大小，任何會導致較小的欄位位移對齊。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="3d8fc-119">設定`rFieldOffsets`和`ulClassSize`為零。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="3d8fc-120">明確的配置：指定每個欄位的位移，或指定類別和封裝大小。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d8fc-121">需求</span><span class="sxs-lookup"><span data-stu-id="3d8fc-121">Requirements</span></span>  
 <span data-ttu-id="3d8fc-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d8fc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d8fc-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3d8fc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d8fc-124">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3d8fc-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d8fc-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d8fc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d8fc-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d8fc-126">See also</span></span>

- [<span data-ttu-id="3d8fc-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3d8fc-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3d8fc-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3d8fc-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
