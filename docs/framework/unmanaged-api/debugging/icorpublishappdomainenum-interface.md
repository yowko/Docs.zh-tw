---
title: "ICorPublishAppDomainEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomainEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomainEnum
helpviewer_keywords: ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f84a93053744f059eb3fdd06e2fb69e098e24ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="af7ce-102">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="af7ce-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="af7ce-103">子類別[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面會提供方法來周遊的集合[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)目前存在於處理序中的物件。</span><span class="sxs-lookup"><span data-stu-id="af7ce-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af7ce-104">方法</span><span class="sxs-lookup"><span data-stu-id="af7ce-104">Methods</span></span>  
  
|<span data-ttu-id="af7ce-105">方法</span><span class="sxs-lookup"><span data-stu-id="af7ce-105">Method</span></span>|<span data-ttu-id="af7ce-106">描述</span><span class="sxs-lookup"><span data-stu-id="af7ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af7ce-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="af7ce-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="af7ce-108">取得指定的數目`ICorPublishAppDomain`從集合中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="af7ce-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af7ce-109">備註</span><span class="sxs-lookup"><span data-stu-id="af7ce-109">Remarks</span></span>  
 <span data-ttu-id="af7ce-110">`ICorPublishAppDomainEnum`介面實作方法的抽象介面， [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="af7ce-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af7ce-111">需求</span><span class="sxs-lookup"><span data-stu-id="af7ce-111">Requirements</span></span>  
 <span data-ttu-id="af7ce-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af7ce-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af7ce-113">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="af7ce-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="af7ce-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af7ce-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af7ce-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af7ce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7ce-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="af7ce-116">See Also</span></span>  
 [<span data-ttu-id="af7ce-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="af7ce-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="af7ce-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="af7ce-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
