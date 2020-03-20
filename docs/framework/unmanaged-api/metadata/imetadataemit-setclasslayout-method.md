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
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177565"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="c85c3-102">IMetaDataEmit::SetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="c85c3-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="c85c3-103">完成由之前調用[DefineTypeDef 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)定義的類的欄位佈局。</span><span class="sxs-lookup"><span data-stu-id="c85c3-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c85c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="c85c3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c85c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="c85c3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c85c3-106">[在]指定`mdTypeDef`要佈局的類的權杖。</span><span class="sxs-lookup"><span data-stu-id="c85c3-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="c85c3-107">[在]包裝尺寸：1、2、4、8 或 16 位元組。</span><span class="sxs-lookup"><span data-stu-id="c85c3-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="c85c3-108">包裝大小是相鄰欄位之間的位元組數。</span><span class="sxs-lookup"><span data-stu-id="c85c3-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="c85c3-109">[在][COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構陣列，每個結構指定類的欄位和類中的欄位偏移量。</span><span class="sxs-lookup"><span data-stu-id="c85c3-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="c85c3-110">使用 終止陣列`mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="c85c3-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="c85c3-111">[在]類的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c85c3-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c85c3-112">備註</span><span class="sxs-lookup"><span data-stu-id="c85c3-112">Remarks</span></span>  
 <span data-ttu-id="c85c3-113">類最初通過調用[IMetaDataEmit：:DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法來定義，並為類的欄位指定三個佈局之一：自動、順序或顯式。</span><span class="sxs-lookup"><span data-stu-id="c85c3-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="c85c3-114">通常，您將使用自動佈局，讓運行時選擇佈局欄位的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="c85c3-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="c85c3-115">但是，您可能希望根據非託管代碼使用的相片順序佈局欄位。</span><span class="sxs-lookup"><span data-stu-id="c85c3-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="c85c3-116">在這種情況下，選擇順序或顯式佈局並調用`SetClassLayout`以完成欄位的佈局：</span><span class="sxs-lookup"><span data-stu-id="c85c3-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="c85c3-117">順序佈局：指定包裝大小。</span><span class="sxs-lookup"><span data-stu-id="c85c3-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="c85c3-118">欄位根據其自然大小或包裝大小對齊，以導致欄位偏移較小的為准。</span><span class="sxs-lookup"><span data-stu-id="c85c3-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="c85c3-119">設置`rFieldOffsets`和`ulClassSize`零。</span><span class="sxs-lookup"><span data-stu-id="c85c3-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="c85c3-120">顯式佈局：指定每個欄位的偏移量或指定類大小和包裝大小。</span><span class="sxs-lookup"><span data-stu-id="c85c3-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c85c3-121">需求</span><span class="sxs-lookup"><span data-stu-id="c85c3-121">Requirements</span></span>  
 <span data-ttu-id="c85c3-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c85c3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c85c3-123">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="c85c3-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c85c3-124">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c85c3-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c85c3-125">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c85c3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c85c3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c85c3-126">See also</span></span>

- [<span data-ttu-id="c85c3-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c85c3-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c85c3-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c85c3-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
