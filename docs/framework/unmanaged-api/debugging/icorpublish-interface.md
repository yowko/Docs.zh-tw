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
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790720"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="a59ed-102">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="a59ed-102">ICorPublish Interface</span></span>
<span data-ttu-id="a59ed-103">作為一般介面，用來發行進程的相關資訊，以及這些進程中應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a59ed-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a59ed-104">方法</span><span class="sxs-lookup"><span data-stu-id="a59ed-104">Methods</span></span>  
  
|<span data-ttu-id="a59ed-105">方法</span><span class="sxs-lookup"><span data-stu-id="a59ed-105">Method</span></span>|<span data-ttu-id="a59ed-106">描述</span><span class="sxs-lookup"><span data-stu-id="a59ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a59ed-107">EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="a59ed-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="a59ed-108">取得[ICorPublishProcessEnum](icorpublishprocessenum-interface.md)實例，其中包含在這部電腦上執行的 managed 進程。</span><span class="sxs-lookup"><span data-stu-id="a59ed-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="a59ed-109">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="a59ed-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="a59ed-110">取得[ICorPublishProcess](icorpublishprocess-interface.md)實例，表示具有指定之識別碼的進程。</span><span class="sxs-lookup"><span data-stu-id="a59ed-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a59ed-111">需求</span><span class="sxs-lookup"><span data-stu-id="a59ed-111">Requirements</span></span>  
 <span data-ttu-id="a59ed-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a59ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59ed-113">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="a59ed-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a59ed-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a59ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a59ed-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59ed-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a59ed-116">See also</span></span>

- [<span data-ttu-id="a59ed-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a59ed-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a59ed-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="a59ed-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
