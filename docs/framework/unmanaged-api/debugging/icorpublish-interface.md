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
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121774"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="9de15-102">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="9de15-102">ICorPublish Interface</span></span>
<span data-ttu-id="9de15-103">作為一般介面，用來發行進程的相關資訊，以及這些進程中應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9de15-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9de15-104">方法</span><span class="sxs-lookup"><span data-stu-id="9de15-104">Methods</span></span>  
  
|<span data-ttu-id="9de15-105">方法</span><span class="sxs-lookup"><span data-stu-id="9de15-105">Method</span></span>|<span data-ttu-id="9de15-106">描述</span><span class="sxs-lookup"><span data-stu-id="9de15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9de15-107">EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="9de15-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="9de15-108">取得[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)實例，其中包含在這部電腦上執行的 managed 進程。</span><span class="sxs-lookup"><span data-stu-id="9de15-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="9de15-109">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="9de15-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="9de15-110">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)實例，表示具有指定之識別碼的進程。</span><span class="sxs-lookup"><span data-stu-id="9de15-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9de15-111">需求</span><span class="sxs-lookup"><span data-stu-id="9de15-111">Requirements</span></span>  
 <span data-ttu-id="9de15-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9de15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9de15-113">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="9de15-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9de15-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9de15-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9de15-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9de15-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de15-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="9de15-116">See also</span></span>

- [<span data-ttu-id="9de15-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9de15-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9de15-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="9de15-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
