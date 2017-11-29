---
title: "ICorPublish 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8eb3bd2da9529a681f7f3a09ef7eb78c776cc302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublish-interface"></a><span data-ttu-id="2fbcf-102">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="2fbcf-102">ICorPublish Interface</span></span>
<span data-ttu-id="2fbcf-103">當做發行處理序的資訊和應用程式定義域的相關資訊，這些處理序中的一般介面。</span><span class="sxs-lookup"><span data-stu-id="2fbcf-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2fbcf-104">方法</span><span class="sxs-lookup"><span data-stu-id="2fbcf-104">Methods</span></span>  
  
|<span data-ttu-id="2fbcf-105">方法</span><span class="sxs-lookup"><span data-stu-id="2fbcf-105">Method</span></span>|<span data-ttu-id="2fbcf-106">說明</span><span class="sxs-lookup"><span data-stu-id="2fbcf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2fbcf-107">EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="2fbcf-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="2fbcf-108">取得[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)包含此電腦上執行的受管理處理程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2fbcf-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="2fbcf-109">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="2fbcf-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="2fbcf-110">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)代表具有指定識別碼的程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2fbcf-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fbcf-111">需求</span><span class="sxs-lookup"><span data-stu-id="2fbcf-111">Requirements</span></span>  
 <span data-ttu-id="2fbcf-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2fbcf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fbcf-113">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2fbcf-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2fbcf-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fbcf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fbcf-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fbcf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fbcf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fbcf-116">See Also</span></span>  
 [<span data-ttu-id="2fbcf-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2fbcf-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2fbcf-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="2fbcf-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
