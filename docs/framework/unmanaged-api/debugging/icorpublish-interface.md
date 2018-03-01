---
title: "ICorPublish 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7769d26d65a97ea8d1b109e0098eae7e7d51ed10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublish-interface"></a><span data-ttu-id="2a6f8-102">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="2a6f8-102">ICorPublish Interface</span></span>
<span data-ttu-id="2a6f8-103">當做發行處理序的資訊和應用程式定義域的相關資訊，這些處理序中的一般介面。</span><span class="sxs-lookup"><span data-stu-id="2a6f8-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a6f8-104">方法</span><span class="sxs-lookup"><span data-stu-id="2a6f8-104">Methods</span></span>  
  
|<span data-ttu-id="2a6f8-105">方法</span><span class="sxs-lookup"><span data-stu-id="2a6f8-105">Method</span></span>|<span data-ttu-id="2a6f8-106">描述</span><span class="sxs-lookup"><span data-stu-id="2a6f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a6f8-107">EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="2a6f8-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="2a6f8-108">取得[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)包含此電腦上執行的受管理處理程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6f8-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="2a6f8-109">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="2a6f8-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="2a6f8-110">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)代表具有指定識別碼的程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6f8-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a6f8-111">需求</span><span class="sxs-lookup"><span data-stu-id="2a6f8-111">Requirements</span></span>  
 <span data-ttu-id="2a6f8-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a6f8-113">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2a6f8-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2a6f8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a6f8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a6f8-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a6f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a6f8-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a6f8-116">See Also</span></span>  
 [<span data-ttu-id="2a6f8-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2a6f8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2a6f8-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="2a6f8-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
