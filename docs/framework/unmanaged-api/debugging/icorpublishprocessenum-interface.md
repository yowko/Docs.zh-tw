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
ms.openlocfilehash: ebf484524b32d8e917d88c21425fab314dfc41be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692614"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="b8eb1-102">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b8eb1-102">ICorPublishProcessEnum Interface</span></span>

<span data-ttu-id="b8eb1-103">[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，可提供方法來遍歷[ICorPublishProcess](icorpublishprocess-interface.md)物件的集合。</span><span class="sxs-lookup"><span data-stu-id="b8eb1-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8eb1-104">方法</span><span class="sxs-lookup"><span data-stu-id="b8eb1-104">Methods</span></span>  
  
|<span data-ttu-id="b8eb1-105">方法</span><span class="sxs-lookup"><span data-stu-id="b8eb1-105">Method</span></span>|<span data-ttu-id="b8eb1-106">描述</span><span class="sxs-lookup"><span data-stu-id="b8eb1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8eb1-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="b8eb1-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="b8eb1-108">`ICorPublishProcess`從目前位置開始，取得集合中指定的實例數目。</span><span class="sxs-lookup"><span data-stu-id="b8eb1-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8eb1-109">備註</span><span class="sxs-lookup"><span data-stu-id="b8eb1-109">Remarks</span></span>  

 <span data-ttu-id="b8eb1-110">介面會實 `ICorPublishProcessEnum` [ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。</span><span class="sxs-lookup"><span data-stu-id="b8eb1-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="b8eb1-111">`ICorPublishProcessEnum`實例是由[ICorPublish：： EnumProcesses](icorpublish-enumprocesses-method.md)方法建立。</span><span class="sxs-lookup"><span data-stu-id="b8eb1-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="b8eb1-112">物件集合的遍歷 `ICorPublishProcess` 是根據建立實例時所指定的篩選準則 `ICorPublishProcessEnum` 。</span><span class="sxs-lookup"><span data-stu-id="b8eb1-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8eb1-113">需求</span><span class="sxs-lookup"><span data-stu-id="b8eb1-113">Requirements</span></span>  

 <span data-ttu-id="b8eb1-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8eb1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8eb1-115">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="b8eb1-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b8eb1-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8eb1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8eb1-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8eb1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8eb1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8eb1-118">See also</span></span>

- [<span data-ttu-id="b8eb1-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b8eb1-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b8eb1-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="b8eb1-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
