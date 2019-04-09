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
ms.openlocfilehash: abfa8a3f58d3e9f7c80762c1faf2bc51514d71b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113811"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="9ae02-102">IMetaDataEmit::SetEventProps 方法</span><span class="sxs-lookup"><span data-stu-id="9ae02-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="9ae02-103">設定或更新指定的功能的先前呼叫所定義的事件[imetadataemit:: Defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae02-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ae02-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ae02-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9ae02-105">參數</span><span class="sxs-lookup"><span data-stu-id="9ae02-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="9ae02-106">[in]事件語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9ae02-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="9ae02-107">[in]事件的旗標。</span><span class="sxs-lookup"><span data-stu-id="9ae02-107">[in] Event flags.</span></span> <span data-ttu-id="9ae02-108">這是位元遮罩`CorEventAttr`值。</span><span class="sxs-lookup"><span data-stu-id="9ae02-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="9ae02-109">[in]事件類別之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9ae02-109">[in] The token for the event class.</span></span> <span data-ttu-id="9ae02-110">這是`mdTypeDef`或`mdTypeRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9ae02-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="9ae02-111">[in]若要訂閱事件或 null 所用的方法。</span><span class="sxs-lookup"><span data-stu-id="9ae02-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="9ae02-112">[in]用來取消訂閱事件，則為 null 的方法。</span><span class="sxs-lookup"><span data-stu-id="9ae02-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="9ae02-113">[in]（藉由衍生類別） 用來引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="9ae02-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="9ae02-114">[in]如需其他方法與事件相關聯的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="9ae02-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="9ae02-115">陣列的最後一個項目必須是`mdMethodDefNil`。</span><span class="sxs-lookup"><span data-stu-id="9ae02-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ae02-116">需求</span><span class="sxs-lookup"><span data-stu-id="9ae02-116">Requirements</span></span>  
 <span data-ttu-id="9ae02-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae02-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ae02-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9ae02-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ae02-119">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9ae02-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9ae02-120">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9ae02-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ae02-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae02-121">See also</span></span>

- [<span data-ttu-id="9ae02-122">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9ae02-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9ae02-123">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9ae02-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
