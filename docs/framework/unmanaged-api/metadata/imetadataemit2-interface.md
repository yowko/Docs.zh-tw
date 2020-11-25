---
title: IMetaDataEmit2 介面
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: b8ad159dace734c343297b256092162f17ab829b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726479"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="9d685-102">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9d685-102">IMetaDataEmit2 Interface</span></span>

<span data-ttu-id="9d685-103">擴充 [IMetaDataEmit](imetadataemit-interface.md) 介面，主要是為了提供使用泛型型別的能力。</span><span class="sxs-lookup"><span data-stu-id="9d685-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d685-104">方法</span><span class="sxs-lookup"><span data-stu-id="9d685-104">Methods</span></span>  
  
|<span data-ttu-id="9d685-105">方法</span><span class="sxs-lookup"><span data-stu-id="9d685-105">Method</span></span>|<span data-ttu-id="9d685-106">描述</span><span class="sxs-lookup"><span data-stu-id="9d685-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d685-107">DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="9d685-108">建立泛型型別參數的定義，並取得該泛型型別參數的標記。</span><span class="sxs-lookup"><span data-stu-id="9d685-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="9d685-109">DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="9d685-110">建立方法的泛型實例，並取得定義的標記。</span><span class="sxs-lookup"><span data-stu-id="9d685-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="9d685-111">GetDeltaSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="9d685-112">取得值，指出表示目前編輯後繼續會話變更所需的資料大小差異。</span><span class="sxs-lookup"><span data-stu-id="9d685-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="9d685-113">ResetENCLog 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="9d685-114">重設編輯後繼續記錄，並啟動新的會話。</span><span class="sxs-lookup"><span data-stu-id="9d685-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="9d685-115">SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="9d685-116">將目前的編輯後繼續會話的變更儲存至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d685-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="9d685-117">SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="9d685-118">將目前的編輯後繼續會話的變更儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="9d685-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="9d685-119">SaveDeltaToStream 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="9d685-120">將目前的編輯後繼續會話的變更儲存至指定的資料流程。</span><span class="sxs-lookup"><span data-stu-id="9d685-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="9d685-121">SetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="9d685-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="9d685-122">設定指定之標記所參考之泛型參數定義的屬性值。</span><span class="sxs-lookup"><span data-stu-id="9d685-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d685-123">需求</span><span class="sxs-lookup"><span data-stu-id="9d685-123">Requirements</span></span>  

 <span data-ttu-id="9d685-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d685-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d685-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="9d685-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d685-126">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="9d685-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d685-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d685-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d685-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d685-128">See also</span></span>

- [<span data-ttu-id="9d685-129">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="9d685-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="9d685-130">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9d685-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
