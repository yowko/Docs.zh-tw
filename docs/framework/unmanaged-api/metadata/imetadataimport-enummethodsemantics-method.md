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
ms.openlocfilehash: 3d14aea92633c944d21d867c8152767ae6f1f291
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720967"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="ffdff-102">IMetaDataImport::EnumMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="ffdff-102">IMetaDataImport::EnumMethodSemantics Method</span></span>

<span data-ttu-id="ffdff-103">列舉和指定方法相關的屬性及屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="ffdff-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdff-104">語法</span><span class="sxs-lookup"><span data-stu-id="ffdff-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffdff-105">參數</span><span class="sxs-lookup"><span data-stu-id="ffdff-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="ffdff-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="ffdff-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ffdff-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="ffdff-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="ffdff-108">在限制列舉範圍的 MethodDef 標記。</span><span class="sxs-lookup"><span data-stu-id="ffdff-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="ffdff-109">擴展用來儲存事件或屬性的陣列。</span><span class="sxs-lookup"><span data-stu-id="ffdff-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ffdff-110">[in] `rEventProp` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ffdff-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="ffdff-111">擴展中傳回的事件或屬性數目 `rEventProp` 。</span><span class="sxs-lookup"><span data-stu-id="ffdff-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffdff-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="ffdff-112">Return Value</span></span>  
  
|<span data-ttu-id="ffdff-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffdff-113">HRESULT</span></span>|<span data-ttu-id="ffdff-114">描述</span><span class="sxs-lookup"><span data-stu-id="ffdff-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ffdff-115">`EnumMethodSemantics` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="ffdff-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ffdff-116">沒有要列舉的事件或屬性。</span><span class="sxs-lookup"><span data-stu-id="ffdff-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="ffdff-117">在此情況下， `pcEventProp` 是零。</span><span class="sxs-lookup"><span data-stu-id="ffdff-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffdff-118">備註</span><span class="sxs-lookup"><span data-stu-id="ffdff-118">Remarks</span></span>  

 <span data-ttu-id="ffdff-119">許多通用語言執行時間類型會定義與屬性相關的 *屬性* `Changed` 事件和 `On` *屬性* `Changed` 方法。</span><span class="sxs-lookup"><span data-stu-id="ffdff-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="ffdff-120">例如，型別會 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> 定義 <xref:System.Windows.Forms.Control.Font%2A> 屬性、 <xref:System.Windows.Forms.Control.FontChanged> 事件和 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffdff-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="ffdff-121">屬性的 set 存取子方法會 <xref:System.Windows.Forms.Control.Font%2A> 呼叫 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法，而這個方法接著會引發 <xref:System.Windows.Forms.Control.FontChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="ffdff-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="ffdff-122">您可以 `EnumMethodSemantics` 使用的 MethodDef 呼叫 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 來取得 <xref:System.Windows.Forms.Control.Font%2A> 屬性和事件的參考 <xref:System.Windows.Forms.Control.FontChanged> 。</span><span class="sxs-lookup"><span data-stu-id="ffdff-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffdff-123">需求</span><span class="sxs-lookup"><span data-stu-id="ffdff-123">Requirements</span></span>  

 <span data-ttu-id="ffdff-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffdff-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffdff-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ffdff-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffdff-126">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ffdff-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffdff-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffdff-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdff-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffdff-128">See also</span></span>

- [<span data-ttu-id="ffdff-129">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ffdff-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ffdff-130">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ffdff-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
