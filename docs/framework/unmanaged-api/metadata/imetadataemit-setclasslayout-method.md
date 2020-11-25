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
ms.openlocfilehash: ee10907fb7f5d90db1bdce845272cd3de38e35a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718692"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="01e73-102">IMetaDataEmit::SetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="01e73-102">IMetaDataEmit::SetClassLayout Method</span></span>

<span data-ttu-id="01e73-103">完成先前呼叫 [DefineTypeDef 方法](imetadataemit-definetypedef-method.md)所定義之類別的欄位版面配置。</span><span class="sxs-lookup"><span data-stu-id="01e73-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e73-104">語法</span><span class="sxs-lookup"><span data-stu-id="01e73-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01e73-105">參數</span><span class="sxs-lookup"><span data-stu-id="01e73-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="01e73-106">在 `mdTypeDef` 指定要配置之類別的權杖。</span><span class="sxs-lookup"><span data-stu-id="01e73-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="01e73-107">在封裝大小：1、2、4、8或16位元組。</span><span class="sxs-lookup"><span data-stu-id="01e73-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="01e73-108">封裝大小是相鄰欄位之間的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="01e73-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="01e73-109">在 [COR_FIELD_OFFSET](cor-field-offset-structure.md) 結構的陣列，其中每個結構會指定類別的欄位，以及類別內欄位的位移。</span><span class="sxs-lookup"><span data-stu-id="01e73-109">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="01e73-110">使用結束陣列 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="01e73-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="01e73-111">在類別的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="01e73-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01e73-112">備註</span><span class="sxs-lookup"><span data-stu-id="01e73-112">Remarks</span></span>  

 <span data-ttu-id="01e73-113">此類別一開始是透過呼叫 [IMetaDataEmit：:D efinetypedef](imetadataemit-definetypedef-method.md) 方法來定義，並為類別的欄位指定三個配置的其中一個：自動、連續或明確。</span><span class="sxs-lookup"><span data-stu-id="01e73-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="01e73-114">一般來說，您會使用自動版面配置，並讓執行時間選擇配置欄位的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="01e73-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="01e73-115">不過，您可能會想要根據非受控碼所使用的相片順序來配置欄位。</span><span class="sxs-lookup"><span data-stu-id="01e73-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="01e73-116">在此情況下，請選擇連續或明確的版面配置，並呼叫 `SetClassLayout` 以完成欄位的版面配置：</span><span class="sxs-lookup"><span data-stu-id="01e73-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="01e73-117">順序配置：指定封裝大小。</span><span class="sxs-lookup"><span data-stu-id="01e73-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="01e73-118">欄位會根據其自然大小或封裝大小對齊，以較小的欄位位移為准。</span><span class="sxs-lookup"><span data-stu-id="01e73-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="01e73-119">將 `rFieldOffsets` 設定 `ulClassSize` 為零。</span><span class="sxs-lookup"><span data-stu-id="01e73-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="01e73-120">明確配置：請指定每個欄位的位移，或指定類別大小和封裝大小。</span><span class="sxs-lookup"><span data-stu-id="01e73-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e73-121">需求</span><span class="sxs-lookup"><span data-stu-id="01e73-121">Requirements</span></span>  

 <span data-ttu-id="01e73-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01e73-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e73-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="01e73-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01e73-124">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="01e73-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01e73-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e73-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e73-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01e73-126">See also</span></span>

- [<span data-ttu-id="01e73-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="01e73-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="01e73-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="01e73-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
