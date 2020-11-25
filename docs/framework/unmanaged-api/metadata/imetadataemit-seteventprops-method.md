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
ms.openlocfilehash: 5c2880ac07f0317bc36ff4bbde68cd3a25febf52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721981"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="c0bff-102">IMetaDataEmit::SetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="c0bff-102">IMetaDataEmit::SetEventProps Method</span></span>

<span data-ttu-id="c0bff-103">設定或更新由先前呼叫 [IMetaDataEmit：:D efineevent](imetadataemit-defineevent-method.md)所定義之事件的指定功能。</span><span class="sxs-lookup"><span data-stu-id="c0bff-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0bff-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0bff-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c0bff-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0bff-105">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="c0bff-106">在事件標記。</span><span class="sxs-lookup"><span data-stu-id="c0bff-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="c0bff-107">在事件旗標。</span><span class="sxs-lookup"><span data-stu-id="c0bff-107">[in] Event flags.</span></span> <span data-ttu-id="c0bff-108">這是值的位元遮罩 `CorEventAttr` 。</span><span class="sxs-lookup"><span data-stu-id="c0bff-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="c0bff-109">在事件類別的 token。</span><span class="sxs-lookup"><span data-stu-id="c0bff-109">[in] The token for the event class.</span></span> <span data-ttu-id="c0bff-110">這可能是 `mdTypeDef` 或 `mdTypeRef` 標記。</span><span class="sxs-lookup"><span data-stu-id="c0bff-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="c0bff-111">在用來訂閱事件的方法，或 null。</span><span class="sxs-lookup"><span data-stu-id="c0bff-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="c0bff-112">在用來取消訂閱事件的方法，或 null。</span><span class="sxs-lookup"><span data-stu-id="c0bff-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="c0bff-113">在衍生類別 (使用的方法) 來引發事件。</span><span class="sxs-lookup"><span data-stu-id="c0bff-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="c0bff-114">在與事件相關聯之其他方法的標記陣列。</span><span class="sxs-lookup"><span data-stu-id="c0bff-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="c0bff-115">陣列的最後一個元素必須是 `mdMethodDefNil` 。</span><span class="sxs-lookup"><span data-stu-id="c0bff-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0bff-116">需求</span><span class="sxs-lookup"><span data-stu-id="c0bff-116">Requirements</span></span>  

 <span data-ttu-id="c0bff-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0bff-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0bff-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c0bff-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0bff-119">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c0bff-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0bff-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0bff-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0bff-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0bff-121">See also</span></span>

- [<span data-ttu-id="c0bff-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c0bff-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c0bff-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c0bff-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
