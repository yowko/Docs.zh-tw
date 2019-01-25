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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e0477adb4958a53289cd0a64f39259403fa7dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656930"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="52fe2-102">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="52fe2-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="52fe2-103">擴充[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面主要是為了讓您能夠使用泛型型別。</span><span class="sxs-lookup"><span data-stu-id="52fe2-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52fe2-104">方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-104">Methods</span></span>  
  
|<span data-ttu-id="52fe2-105">方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-105">Method</span></span>|<span data-ttu-id="52fe2-106">描述</span><span class="sxs-lookup"><span data-stu-id="52fe2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52fe2-107">DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="52fe2-108">建立泛型類型參數的定義，並取得該泛型型別參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="52fe2-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="52fe2-109">DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="52fe2-110">建立泛型方法的執行個體，並取得定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="52fe2-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="52fe2-111">GetDeltaSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="52fe2-112">取得值，指出所需的 express 所做的變更目前的編輯和繼續工作階段的資料大小的差異。</span><span class="sxs-lookup"><span data-stu-id="52fe2-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="52fe2-113">ResetENCLog 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="52fe2-114">重設的編輯後繼續的記錄檔，並啟動新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="52fe2-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="52fe2-115">SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="52fe2-116">將目前的編輯和繼續工作階段的變更儲存至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="52fe2-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="52fe2-117">SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="52fe2-118">將目前的編輯和繼續工作階段的變更儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="52fe2-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="52fe2-119">SaveDeltaToStream 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="52fe2-120">將變更儲存從目前的編輯和繼續工作階段指定的資料流。</span><span class="sxs-lookup"><span data-stu-id="52fe2-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="52fe2-121">SetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="52fe2-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="52fe2-122">設定指定的語彙基元所參考的泛型參數定義的屬性值。</span><span class="sxs-lookup"><span data-stu-id="52fe2-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52fe2-123">需求</span><span class="sxs-lookup"><span data-stu-id="52fe2-123">Requirements</span></span>  
 <span data-ttu-id="52fe2-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52fe2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52fe2-125">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52fe2-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52fe2-126">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="52fe2-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52fe2-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52fe2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52fe2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52fe2-128">See also</span></span>
- [<span data-ttu-id="52fe2-129">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="52fe2-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="52fe2-130">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="52fe2-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
