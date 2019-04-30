---
title: ICorPublish 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7581d68f5c2b575403ddc84d06147f012e7ab39e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993567"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="98a0a-102">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="98a0a-102">ICorPublish Interface</span></span>
<span data-ttu-id="98a0a-103">當做發行處理序的相關資訊和應用程式定義域的相關資訊，這些處理序中的一般介面。</span><span class="sxs-lookup"><span data-stu-id="98a0a-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98a0a-104">方法</span><span class="sxs-lookup"><span data-stu-id="98a0a-104">Methods</span></span>  
  
|<span data-ttu-id="98a0a-105">方法</span><span class="sxs-lookup"><span data-stu-id="98a0a-105">Method</span></span>|<span data-ttu-id="98a0a-106">描述</span><span class="sxs-lookup"><span data-stu-id="98a0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98a0a-107">EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="98a0a-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="98a0a-108">取得[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)包含此電腦上執行的受管理處理程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="98a0a-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="98a0a-109">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="98a0a-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="98a0a-110">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)執行個體，表示具有指定識別碼的程序。</span><span class="sxs-lookup"><span data-stu-id="98a0a-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98a0a-111">需求</span><span class="sxs-lookup"><span data-stu-id="98a0a-111">Requirements</span></span>  
 <span data-ttu-id="98a0a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98a0a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a0a-113">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="98a0a-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="98a0a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a0a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98a0a-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a0a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a0a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a0a-116">See also</span></span>

- [<span data-ttu-id="98a0a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="98a0a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="98a0a-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="98a0a-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
