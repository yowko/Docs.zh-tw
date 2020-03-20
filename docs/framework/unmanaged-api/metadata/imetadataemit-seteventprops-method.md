---
title: IMetaDataEmit::SetEventProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177533"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="1b974-102">IMetaDataEmit::SetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="1b974-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="1b974-103">設置或更新由之前調用[IMetaDataEmit：:DefineEvent）](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)定義的事件的指定功能。</span><span class="sxs-lookup"><span data-stu-id="1b974-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b974-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b974-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b974-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b974-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="1b974-106">[在]事件權杖。</span><span class="sxs-lookup"><span data-stu-id="1b974-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="1b974-107">[在]事件標誌。</span><span class="sxs-lookup"><span data-stu-id="1b974-107">[in] Event flags.</span></span> <span data-ttu-id="1b974-108">這是值的`CorEventAttr`位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="1b974-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="1b974-109">[在]事件類的權杖。</span><span class="sxs-lookup"><span data-stu-id="1b974-109">[in] The token for the event class.</span></span> <span data-ttu-id="1b974-110">這是 或`mdTypeDef``mdTypeRef`標記。</span><span class="sxs-lookup"><span data-stu-id="1b974-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="1b974-111">[在]用於訂閱事件或 null 的方法。</span><span class="sxs-lookup"><span data-stu-id="1b974-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="1b974-112">[在]用於取消訂閱事件或 null 的方法。</span><span class="sxs-lookup"><span data-stu-id="1b974-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="1b974-113">[在]用於（由派生類）引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="1b974-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="1b974-114">[在]與事件關聯的其他方法的權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="1b974-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="1b974-115">陣列的最後一個元素必須是`mdMethodDefNil`。</span><span class="sxs-lookup"><span data-stu-id="1b974-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b974-116">需求</span><span class="sxs-lookup"><span data-stu-id="1b974-116">Requirements</span></span>  
 <span data-ttu-id="1b974-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b974-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b974-118">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="1b974-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b974-119">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1b974-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b974-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b974-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b974-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b974-121">See also</span></span>

- [<span data-ttu-id="1b974-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1b974-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1b974-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1b974-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
