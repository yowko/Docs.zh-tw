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
ms.openlocfilehash: 213cbd955e3d47a49abde579a54af48641e225ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491910"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="ad7a4-102">IMetaDataImport::EnumMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="ad7a4-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="ad7a4-103">列舉和指定方法相關的屬性及屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad7a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad7a4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad7a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad7a4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ad7a4-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ad7a4-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="ad7a4-108">在會限制列舉範圍的 MethodDef token。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="ad7a4-109">脫銷用來儲存事件或屬性的陣列。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ad7a4-110">[in] `rEventProp` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="ad7a4-111">脫銷在中傳回的事件或屬性數目 `rEventProp` 。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad7a4-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="ad7a4-112">Return Value</span></span>  
  
|<span data-ttu-id="ad7a4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad7a4-113">HRESULT</span></span>|<span data-ttu-id="ad7a4-114">說明</span><span class="sxs-lookup"><span data-stu-id="ad7a4-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ad7a4-115">`EnumMethodSemantics`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ad7a4-116">沒有要列舉的事件或屬性。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="ad7a4-117">在此情況下， `pcEventProp` 是零。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad7a4-118">備註</span><span class="sxs-lookup"><span data-stu-id="ad7a4-118">Remarks</span></span>  
 <span data-ttu-id="ad7a4-119">許多 common language runtime 型別會定義與屬性相關的*屬性* `Changed` 事件和 `On` *屬性* `Changed` 方法。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="ad7a4-120">例如，型別會 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> 定義 <xref:System.Windows.Forms.Control.Font%2A> 屬性、 <xref:System.Windows.Forms.Control.FontChanged> 事件和 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="ad7a4-121">屬性的 set 存取子方法會 <xref:System.Windows.Forms.Control.Font%2A> 呼叫 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法，後者接著會引發 <xref:System.Windows.Forms.Control.FontChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="ad7a4-122">您可以 `EnumMethodSemantics` 使用的 MethodDef 呼叫 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 來取得 <xref:System.Windows.Forms.Control.Font%2A> 屬性和事件的參考 <xref:System.Windows.Forms.Control.FontChanged> 。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad7a4-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="ad7a4-123">Requirements</span></span>  
 <span data-ttu-id="ad7a4-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad7a4-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad7a4-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ad7a4-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad7a4-126">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ad7a4-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad7a4-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad7a4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7a4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad7a4-128">See also</span></span>

- [<span data-ttu-id="ad7a4-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ad7a4-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ad7a4-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ad7a4-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
