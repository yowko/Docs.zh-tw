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
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175456"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="3ae68-102">IMetaDataImport::EnumMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="3ae68-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="3ae68-103">列舉和指定方法相關的屬性及屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="3ae68-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae68-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ae68-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ae68-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ae68-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3ae68-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="3ae68-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3ae68-107">對於此方法的第一次調用，這必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="3ae68-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="3ae68-108">[在]限制枚舉範圍的 MethodDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="3ae68-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="3ae68-109">[出]用於存儲事件或屬性的陣列。</span><span class="sxs-lookup"><span data-stu-id="3ae68-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3ae68-110">[in] `rEventProp` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="3ae68-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="3ae68-111">[出]在 中`rEventProp`返回的事件或屬性數。</span><span class="sxs-lookup"><span data-stu-id="3ae68-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ae68-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ae68-112">Return Value</span></span>  
  
|<span data-ttu-id="3ae68-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ae68-113">HRESULT</span></span>|<span data-ttu-id="3ae68-114">描述</span><span class="sxs-lookup"><span data-stu-id="3ae68-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3ae68-115">`EnumMethodSemantics`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="3ae68-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3ae68-116">沒有要枚舉的事件或屬性。</span><span class="sxs-lookup"><span data-stu-id="3ae68-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="3ae68-117">在這種情況下，`pcEventProp`為零。</span><span class="sxs-lookup"><span data-stu-id="3ae68-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ae68-118">備註</span><span class="sxs-lookup"><span data-stu-id="3ae68-118">Remarks</span></span>  
 <span data-ttu-id="3ae68-119">許多通用語言運行時類型定義與其屬性相關的*屬性*`Changed`事件和`On`*屬性*`Changed`方法。</span><span class="sxs-lookup"><span data-stu-id="3ae68-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="3ae68-120">例如，<xref:System.Windows.Forms.Control?displayProperty=nameWithType>類型定義<xref:System.Windows.Forms.Control.Font%2A>屬性、<xref:System.Windows.Forms.Control.FontChanged>事件和方法。 <xref:System.Windows.Forms.Control.OnFontChanged%2A></span><span class="sxs-lookup"><span data-stu-id="3ae68-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="3ae68-121">屬性調用<xref:System.Windows.Forms.Control.Font%2A><xref:System.Windows.Forms.Control.OnFontChanged%2A>方法的集訪問器方法，該方法反過來引發事件<xref:System.Windows.Forms.Control.FontChanged>。</span><span class="sxs-lookup"><span data-stu-id="3ae68-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="3ae68-122">您將使用`EnumMethodSemantics`MethodDef 調用，<xref:System.Windows.Forms.Control.OnFontChanged%2A>以獲得對<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.Control.FontChanged>事件的引用。</span><span class="sxs-lookup"><span data-stu-id="3ae68-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae68-123">需求</span><span class="sxs-lookup"><span data-stu-id="3ae68-123">Requirements</span></span>  
 <span data-ttu-id="3ae68-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ae68-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ae68-125">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="3ae68-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ae68-126">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3ae68-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ae68-127">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ae68-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae68-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae68-128">See also</span></span>

- [<span data-ttu-id="3ae68-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3ae68-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3ae68-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3ae68-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
