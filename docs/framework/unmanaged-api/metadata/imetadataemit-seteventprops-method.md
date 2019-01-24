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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab479aab56b429c104a44b1fae192bc7f20a389d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656917"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="9daf1-102">IMetaDataEmit::SetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="9daf1-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="9daf1-103">設定或更新指定的功能的先前呼叫所定義的事件[imetadataemit:: Defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9daf1-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9daf1-104">語法</span><span class="sxs-lookup"><span data-stu-id="9daf1-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="9daf1-105">參數</span><span class="sxs-lookup"><span data-stu-id="9daf1-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="9daf1-106">[in]事件語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9daf1-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="9daf1-107">[in]事件的旗標。</span><span class="sxs-lookup"><span data-stu-id="9daf1-107">[in] Event flags.</span></span> <span data-ttu-id="9daf1-108">這是位元遮罩`CorEventAttr`值。</span><span class="sxs-lookup"><span data-stu-id="9daf1-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="9daf1-109">[in]事件類別之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9daf1-109">[in] The token for the event class.</span></span> <span data-ttu-id="9daf1-110">這是`mdTypeDef`或`mdTypeRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9daf1-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="9daf1-111">[in]若要訂閱事件或 null 所用的方法。</span><span class="sxs-lookup"><span data-stu-id="9daf1-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="9daf1-112">[in]用來取消訂閱事件，則為 null 的方法。</span><span class="sxs-lookup"><span data-stu-id="9daf1-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="9daf1-113">[in]（藉由衍生類別） 用來引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="9daf1-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="9daf1-114">[in]如需其他方法與事件相關聯的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="9daf1-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="9daf1-115">陣列的最後一個項目必須是`mdMethodDefNil`。</span><span class="sxs-lookup"><span data-stu-id="9daf1-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9daf1-116">需求</span><span class="sxs-lookup"><span data-stu-id="9daf1-116">Requirements</span></span>  
 <span data-ttu-id="9daf1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9daf1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9daf1-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9daf1-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9daf1-119">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9daf1-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9daf1-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9daf1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9daf1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9daf1-121">See also</span></span>
- [<span data-ttu-id="9daf1-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9daf1-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9daf1-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9daf1-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
