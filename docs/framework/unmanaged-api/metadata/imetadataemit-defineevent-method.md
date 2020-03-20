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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175846"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="a925e-102">IMetaDataEmit::DefineEvent 方法</span><span class="sxs-lookup"><span data-stu-id="a925e-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="a925e-103">為具有指定中繼資料簽名的事件創建定義，並獲取該事件定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="a925e-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a925e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a925e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a925e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a925e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a925e-106">[在]目標類或介面的權杖。</span><span class="sxs-lookup"><span data-stu-id="a925e-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="a925e-107">這是 或`mdTypeDef``mdTypeDefNil`標記。</span><span class="sxs-lookup"><span data-stu-id="a925e-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="a925e-108">[在]事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a925e-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="a925e-109">[在]事件標誌。</span><span class="sxs-lookup"><span data-stu-id="a925e-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="a925e-110">[在]事件類的權杖。</span><span class="sxs-lookup"><span data-stu-id="a925e-110">[in] The token for the event class.</span></span> <span data-ttu-id="a925e-111">這是 一`mdTypeDef`個`mdTypeRef`、或`mdTokenNil`標記。</span><span class="sxs-lookup"><span data-stu-id="a925e-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="a925e-112">[在]用於訂閱事件或 null 的方法。</span><span class="sxs-lookup"><span data-stu-id="a925e-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="a925e-113">[在]用於取消訂閱事件或 null 的方法。</span><span class="sxs-lookup"><span data-stu-id="a925e-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="a925e-114">[在]用於（由派生類）引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="a925e-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="a925e-115">[在]與事件關聯的其他方法的權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="a925e-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="a925e-116">陣列用`mdMethodDefNil`權杖終止。</span><span class="sxs-lookup"><span data-stu-id="a925e-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="a925e-117">[出]分配給事件的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="a925e-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a925e-118">需求</span><span class="sxs-lookup"><span data-stu-id="a925e-118">Requirements</span></span>  
 <span data-ttu-id="a925e-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a925e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a925e-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="a925e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a925e-121">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a925e-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a925e-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a925e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a925e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a925e-123">See also</span></span>

- [<span data-ttu-id="a925e-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a925e-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a925e-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a925e-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
