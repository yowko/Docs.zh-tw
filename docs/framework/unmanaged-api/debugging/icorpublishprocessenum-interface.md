---
title: ICorPublishProcessEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421068"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="62b4a-102">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="62b4a-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="62b4a-103">[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，提供方法來流覽[ICorPublishProcess](icorpublishprocess-interface.md)物件的集合。</span><span class="sxs-lookup"><span data-stu-id="62b4a-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62b4a-104">方法</span><span class="sxs-lookup"><span data-stu-id="62b4a-104">Methods</span></span>  
  
|<span data-ttu-id="62b4a-105">方法</span><span class="sxs-lookup"><span data-stu-id="62b4a-105">Method</span></span>|<span data-ttu-id="62b4a-106">描述</span><span class="sxs-lookup"><span data-stu-id="62b4a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62b4a-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="62b4a-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="62b4a-108">`ICorPublishProcess`從目前位置開始，取得集合中指定數目的實例。</span><span class="sxs-lookup"><span data-stu-id="62b4a-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62b4a-109">備註</span><span class="sxs-lookup"><span data-stu-id="62b4a-109">Remarks</span></span>  
 <span data-ttu-id="62b4a-110">介面會實 `ICorPublishProcessEnum` [ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。</span><span class="sxs-lookup"><span data-stu-id="62b4a-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="62b4a-111">`ICorPublishProcessEnum`實例是由[ICorPublish：： EnumProcesses](icorpublish-enumprocesses-method.md)方法所建立。</span><span class="sxs-lookup"><span data-stu-id="62b4a-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="62b4a-112">物件集合的遍歷 `ICorPublishProcess` 是以建立實例時所指定的篩選準則為基礎 `ICorPublishProcessEnum` 。</span><span class="sxs-lookup"><span data-stu-id="62b4a-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62b4a-113">需求</span><span class="sxs-lookup"><span data-stu-id="62b4a-113">Requirements</span></span>  
 <span data-ttu-id="62b4a-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62b4a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b4a-115">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="62b4a-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="62b4a-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62b4a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62b4a-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62b4a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b4a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62b4a-118">See also</span></span>

- [<span data-ttu-id="62b4a-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="62b4a-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="62b4a-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="62b4a-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
