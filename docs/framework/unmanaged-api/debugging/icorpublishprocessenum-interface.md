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
ms.openlocfilehash: 3a7267548a957d403cfe02aa3d800a410c14b82a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103422"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="e9f78-102">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e9f78-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="e9f78-103">[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面的子類別，提供方法來流覽[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件的集合。</span><span class="sxs-lookup"><span data-stu-id="e9f78-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9f78-104">方法</span><span class="sxs-lookup"><span data-stu-id="e9f78-104">Methods</span></span>  
  
|<span data-ttu-id="e9f78-105">方法</span><span class="sxs-lookup"><span data-stu-id="e9f78-105">Method</span></span>|<span data-ttu-id="e9f78-106">描述</span><span class="sxs-lookup"><span data-stu-id="e9f78-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9f78-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="e9f78-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="e9f78-108">從目前位置開始，取得集合中指定數目的 `ICorPublishProcess` 實例。</span><span class="sxs-lookup"><span data-stu-id="e9f78-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9f78-109">備註</span><span class="sxs-lookup"><span data-stu-id="e9f78-109">Remarks</span></span>  
 <span data-ttu-id="e9f78-110">`ICorPublishProcessEnum` 介面會實[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)抽象介面的方法。</span><span class="sxs-lookup"><span data-stu-id="e9f78-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="e9f78-111">`ICorPublishProcessEnum` 實例是由[ICorPublish：： EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)方法所建立。</span><span class="sxs-lookup"><span data-stu-id="e9f78-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="e9f78-112">`ICorPublishProcess` 物件集合的遍歷是以建立 `ICorPublishProcessEnum` 實例時所指定的篩選準則為基礎。</span><span class="sxs-lookup"><span data-stu-id="e9f78-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9f78-113">需求</span><span class="sxs-lookup"><span data-stu-id="e9f78-113">Requirements</span></span>  
 <span data-ttu-id="e9f78-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f78-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f78-115">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="e9f78-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e9f78-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9f78-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9f78-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f78-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f78-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f78-118">See also</span></span>

- [<span data-ttu-id="e9f78-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e9f78-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e9f78-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="e9f78-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
