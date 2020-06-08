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
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493017"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="3b511-102">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3b511-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="3b511-103">延伸[IMetaDataEmit](imetadataemit-interface.md)介面，主要是為了提供使用泛型型別的能力。</span><span class="sxs-lookup"><span data-stu-id="3b511-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b511-104">方法</span><span class="sxs-lookup"><span data-stu-id="3b511-104">Methods</span></span>  
  
|<span data-ttu-id="3b511-105">方法</span><span class="sxs-lookup"><span data-stu-id="3b511-105">Method</span></span>|<span data-ttu-id="3b511-106">描述</span><span class="sxs-lookup"><span data-stu-id="3b511-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b511-107">DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="3b511-108">建立泛型型別參數的定義，並取得該泛型型別參數的 token。</span><span class="sxs-lookup"><span data-stu-id="3b511-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="3b511-109">DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="3b511-110">建立方法的泛型實例，並取得定義的 token。</span><span class="sxs-lookup"><span data-stu-id="3b511-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="3b511-111">GetDeltaSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="3b511-112">取得值，表示為目前的「編輯後繼續」會話表示所需的資料大小差異。</span><span class="sxs-lookup"><span data-stu-id="3b511-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="3b511-113">ResetENCLog 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="3b511-114">重設 [編輯後繼續] 記錄並啟動新的會話。</span><span class="sxs-lookup"><span data-stu-id="3b511-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="3b511-115">SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="3b511-116">將目前的「編輯後繼續」會話的變更儲存至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="3b511-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="3b511-117">SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="3b511-118">將目前的「編輯後繼續」會話的變更儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="3b511-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="3b511-119">SaveDeltaToStream 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="3b511-120">將目前的「編輯後繼續」會話的變更儲存至指定的資料流程。</span><span class="sxs-lookup"><span data-stu-id="3b511-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="3b511-121">SetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="3b511-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="3b511-122">針對指定之標記所參考的泛型參數定義，設定屬性值。</span><span class="sxs-lookup"><span data-stu-id="3b511-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b511-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="3b511-123">Requirements</span></span>  
 <span data-ttu-id="3b511-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b511-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b511-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3b511-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b511-126">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3b511-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b511-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b511-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b511-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b511-128">See also</span></span>

- [<span data-ttu-id="3b511-129">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="3b511-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="3b511-130">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3b511-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
