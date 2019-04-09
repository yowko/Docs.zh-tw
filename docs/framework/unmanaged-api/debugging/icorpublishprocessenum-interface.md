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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5186df61eb82b29fcfa9776408498b748068e122
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173650"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="e6f71-102">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e6f71-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="e6f71-103">子類別[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面會提供方法來周遊集合[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="e6f71-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6f71-104">方法</span><span class="sxs-lookup"><span data-stu-id="e6f71-104">Methods</span></span>  
  
|<span data-ttu-id="e6f71-105">方法</span><span class="sxs-lookup"><span data-stu-id="e6f71-105">Method</span></span>|<span data-ttu-id="e6f71-106">描述</span><span class="sxs-lookup"><span data-stu-id="e6f71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6f71-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="e6f71-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="e6f71-108">取得指定的數目`ICorPublishProcess`從集合中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6f71-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f71-109">備註</span><span class="sxs-lookup"><span data-stu-id="e6f71-109">Remarks</span></span>  
 <span data-ttu-id="e6f71-110">`ICorPublishProcessEnum`介面實作的抽象的介面，方法[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f71-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="e6f71-111">`ICorPublishProcessEnum`執行個體由[icorpublish:: Enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e6f71-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="e6f71-112">集合的周遊`ICorPublishProcess`物件根據篩選準則時提供`ICorPublishProcessEnum`建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6f71-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6f71-113">需求</span><span class="sxs-lookup"><span data-stu-id="e6f71-113">Requirements</span></span>  
 <span data-ttu-id="e6f71-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f71-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f71-115">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e6f71-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e6f71-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6f71-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e6f71-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e6f71-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6f71-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f71-118">See also</span></span>

- [<span data-ttu-id="e6f71-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e6f71-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e6f71-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="e6f71-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
