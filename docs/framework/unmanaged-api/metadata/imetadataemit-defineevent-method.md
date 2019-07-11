---
title: IMetaDataEmit::DefineEvent 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba35cd678d88389854ca2e866020ea3a9364c923
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777670"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="09ee2-102">IMetaDataEmit::DefineEvent 方法</span><span class="sxs-lookup"><span data-stu-id="09ee2-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="09ee2-103">建立事件的定義，具有指定之中繼資料簽章，並取得該事件定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09ee2-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ee2-104">語法</span><span class="sxs-lookup"><span data-stu-id="09ee2-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ee2-105">參數</span><span class="sxs-lookup"><span data-stu-id="09ee2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="09ee2-106">[in]目標類別或介面之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09ee2-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="09ee2-107">這是`mdTypeDef`或`mdTypeDefNil`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09ee2-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="09ee2-108">[in]事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="09ee2-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="09ee2-109">[in]事件的旗標。</span><span class="sxs-lookup"><span data-stu-id="09ee2-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="09ee2-110">[in]事件類別之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09ee2-110">[in] The token for the event class.</span></span> <span data-ttu-id="09ee2-111">這是`mdTypeDef`，則`mdTypeRef`，或`mdTokenNil`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09ee2-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="09ee2-112">[in]若要訂閱事件或 null 所用的方法。</span><span class="sxs-lookup"><span data-stu-id="09ee2-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="09ee2-113">[in]用來取消訂閱事件，則為 null 的方法。</span><span class="sxs-lookup"><span data-stu-id="09ee2-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="09ee2-114">[in]（藉由衍生類別） 用來引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="09ee2-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="09ee2-115">[in]如需其他方法與事件相關聯的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="09ee2-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="09ee2-116">陣列結尾`mdMethodDefNil`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09ee2-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="09ee2-117">[out]指派給事件的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09ee2-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ee2-118">需求</span><span class="sxs-lookup"><span data-stu-id="09ee2-118">Requirements</span></span>  
 <span data-ttu-id="09ee2-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09ee2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ee2-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="09ee2-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09ee2-121">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="09ee2-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09ee2-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ee2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ee2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09ee2-123">See also</span></span>

- [<span data-ttu-id="09ee2-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="09ee2-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="09ee2-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="09ee2-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
