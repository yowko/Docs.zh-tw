---
title: "ICorPublishProcessEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcessEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcessEnum
helpviewer_keywords: ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66e31911289d1ef8b590a0b7e7896adfa4998adc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="6c8b3-102">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="6c8b3-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="6c8b3-103">子類別[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面會提供方法來周遊的集合[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="6c8b3-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c8b3-104">方法</span><span class="sxs-lookup"><span data-stu-id="6c8b3-104">Methods</span></span>  
  
|<span data-ttu-id="6c8b3-105">方法</span><span class="sxs-lookup"><span data-stu-id="6c8b3-105">Method</span></span>|<span data-ttu-id="6c8b3-106">說明</span><span class="sxs-lookup"><span data-stu-id="6c8b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c8b3-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="6c8b3-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="6c8b3-108">取得指定的數目`ICorPublishProcess`從集合中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c8b3-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c8b3-109">備註</span><span class="sxs-lookup"><span data-stu-id="6c8b3-109">Remarks</span></span>  
 <span data-ttu-id="6c8b3-110">`ICorPublishProcessEnum`介面實作方法的抽象介面， [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6c8b3-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="6c8b3-111">`ICorPublishProcessEnum`會建立執行個體[icorpublish:: Enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="6c8b3-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="6c8b3-112">集合中的周遊`ICorPublishProcess`物件為基礎時指定的篩選準則`ICorPublishProcessEnum`建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c8b3-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c8b3-113">需求</span><span class="sxs-lookup"><span data-stu-id="6c8b3-113">Requirements</span></span>  
 <span data-ttu-id="6c8b3-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c8b3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c8b3-115">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6c8b3-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6c8b3-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c8b3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c8b3-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c8b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c8b3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c8b3-118">See Also</span></span>  
 [<span data-ttu-id="6c8b3-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6c8b3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6c8b3-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="6c8b3-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
