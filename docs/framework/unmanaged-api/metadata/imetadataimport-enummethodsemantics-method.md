---
title: IMetaDataImport::EnumMethodSemantics 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 715e53ae04532214d4011d4a40503b2ade5a014d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782079"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="5b11d-102">IMetaDataImport::EnumMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="5b11d-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="5b11d-103">列舉和指定方法相關的屬性及屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="5b11d-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b11d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b11d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b11d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b11d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5b11d-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="5b11d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5b11d-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="5b11d-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="5b11d-108">[in]列舉的範圍限制 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5b11d-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="5b11d-109">[out]用來儲存事件或屬性的陣列。</span><span class="sxs-lookup"><span data-stu-id="5b11d-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5b11d-110">[in] `rEventProp` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="5b11d-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="5b11d-111">[out]事件或傳入的屬性數目`rEventProp`。</span><span class="sxs-lookup"><span data-stu-id="5b11d-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b11d-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="5b11d-112">Return Value</span></span>  
  
|<span data-ttu-id="5b11d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b11d-113">HRESULT</span></span>|<span data-ttu-id="5b11d-114">描述</span><span class="sxs-lookup"><span data-stu-id="5b11d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5b11d-115">`EnumMethodSemantics` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5b11d-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5b11d-116">沒有任何事件或列舉的屬性。</span><span class="sxs-lookup"><span data-stu-id="5b11d-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="5b11d-117">在此情況下，`pcEventProp`為零。</span><span class="sxs-lookup"><span data-stu-id="5b11d-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b11d-118">備註</span><span class="sxs-lookup"><span data-stu-id="5b11d-118">Remarks</span></span>  
 <span data-ttu-id="5b11d-119">許多 common language runtime 類型定義*屬性*`Changed`事件並`On`*屬性*`Changed`方法與它們的屬性。</span><span class="sxs-lookup"><span data-stu-id="5b11d-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="5b11d-120">例如，<xref:System.Windows.Forms.Control?displayProperty=nameWithType>型別會定義<xref:System.Windows.Forms.Control.Font%2A>屬性，<xref:System.Windows.Forms.Control.FontChanged>事件，和<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5b11d-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="5b11d-121">Set 存取子方法<xref:System.Windows.Forms.Control.Font%2A>屬性呼叫<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法，進而引發<xref:System.Windows.Forms.Control.FontChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="5b11d-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="5b11d-122">您可以呼叫`EnumMethodSemantics`使用的 MethodDef<xref:System.Windows.Forms.Control.OnFontChanged%2A>來取得參考<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.Control.FontChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="5b11d-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b11d-123">需求</span><span class="sxs-lookup"><span data-stu-id="5b11d-123">Requirements</span></span>  
 <span data-ttu-id="5b11d-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b11d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b11d-125">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5b11d-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b11d-126">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5b11d-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b11d-127">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b11d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b11d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b11d-128">See also</span></span>

- [<span data-ttu-id="5b11d-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5b11d-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5b11d-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5b11d-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
