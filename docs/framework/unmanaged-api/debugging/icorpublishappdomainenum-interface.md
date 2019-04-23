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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090026"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="29d4a-102">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="29d4a-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="29d4a-103">子類別[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面會提供方法來周遊集合[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)目前存在於同一個處理序的物件。</span><span class="sxs-lookup"><span data-stu-id="29d4a-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29d4a-104">方法</span><span class="sxs-lookup"><span data-stu-id="29d4a-104">Methods</span></span>  
  
|<span data-ttu-id="29d4a-105">方法</span><span class="sxs-lookup"><span data-stu-id="29d4a-105">Method</span></span>|<span data-ttu-id="29d4a-106">描述</span><span class="sxs-lookup"><span data-stu-id="29d4a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29d4a-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="29d4a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="29d4a-108">取得指定的數目`ICorPublishAppDomain`從集合中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29d4a-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29d4a-109">備註</span><span class="sxs-lookup"><span data-stu-id="29d4a-109">Remarks</span></span>  
 <span data-ttu-id="29d4a-110">`ICorPublishAppDomainEnum`介面實作的抽象的介面，方法[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="29d4a-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d4a-111">需求</span><span class="sxs-lookup"><span data-stu-id="29d4a-111">Requirements</span></span>  
 <span data-ttu-id="29d4a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29d4a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d4a-113">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="29d4a-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="29d4a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29d4a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29d4a-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d4a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d4a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29d4a-116">See also</span></span>

- [<span data-ttu-id="29d4a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="29d4a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="29d4a-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="29d4a-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
