---
title: ICorPublishAppDomainEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f6d4af7c01f91dff77d6ba715ef845f523c7fb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090026"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="2185c-102">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2185c-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="2185c-103">子類別[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面會提供方法來周遊集合[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)目前存在於同一個處理序的物件。</span><span class="sxs-lookup"><span data-stu-id="2185c-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2185c-104">方法</span><span class="sxs-lookup"><span data-stu-id="2185c-104">Methods</span></span>  
  
|<span data-ttu-id="2185c-105">方法</span><span class="sxs-lookup"><span data-stu-id="2185c-105">Method</span></span>|<span data-ttu-id="2185c-106">描述</span><span class="sxs-lookup"><span data-stu-id="2185c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2185c-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="2185c-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="2185c-108">取得指定的數目`ICorPublishAppDomain`從集合中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2185c-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2185c-109">備註</span><span class="sxs-lookup"><span data-stu-id="2185c-109">Remarks</span></span>  
 <span data-ttu-id="2185c-110">`ICorPublishAppDomainEnum`介面實作的抽象的介面，方法[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="2185c-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2185c-111">需求</span><span class="sxs-lookup"><span data-stu-id="2185c-111">Requirements</span></span>  
 <span data-ttu-id="2185c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2185c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2185c-113">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2185c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2185c-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2185c-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2185c-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="2185c-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2185c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2185c-116">See also</span></span>

- [<span data-ttu-id="2185c-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2185c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2185c-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="2185c-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
