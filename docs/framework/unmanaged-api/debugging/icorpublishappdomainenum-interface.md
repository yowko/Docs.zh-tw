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
ms.openlocfilehash: 8359eda5432a9b3818fd58f6adc18570e4c5f154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="334e1-102">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="334e1-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="334e1-103">子類別[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面會提供方法來周遊的集合[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)目前存在於處理序中的物件。</span><span class="sxs-lookup"><span data-stu-id="334e1-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="334e1-104">方法</span><span class="sxs-lookup"><span data-stu-id="334e1-104">Methods</span></span>  
  
|<span data-ttu-id="334e1-105">方法</span><span class="sxs-lookup"><span data-stu-id="334e1-105">Method</span></span>|<span data-ttu-id="334e1-106">說明</span><span class="sxs-lookup"><span data-stu-id="334e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="334e1-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="334e1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="334e1-108">取得指定的數目`ICorPublishAppDomain`從集合中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="334e1-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="334e1-109">備註</span><span class="sxs-lookup"><span data-stu-id="334e1-109">Remarks</span></span>  
 <span data-ttu-id="334e1-110">`ICorPublishAppDomainEnum`介面實作方法的抽象介面， [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="334e1-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="334e1-111">需求</span><span class="sxs-lookup"><span data-stu-id="334e1-111">Requirements</span></span>  
 <span data-ttu-id="334e1-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="334e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="334e1-113">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="334e1-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="334e1-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="334e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="334e1-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="334e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="334e1-116">See Also</span></span>  
 [<span data-ttu-id="334e1-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="334e1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="334e1-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="334e1-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
