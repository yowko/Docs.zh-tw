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
ms.openlocfilehash: 3ff4efe8b3e2932da7f65246bf4ad614a4dd86cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694403"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="7f9cc-102">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="7f9cc-102">ICorPublish Interface</span></span>

<span data-ttu-id="7f9cc-103">作為一般介面，用來發佈有關進程的資訊，以及有關這些進程中應用程式域的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f9cc-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f9cc-104">方法</span><span class="sxs-lookup"><span data-stu-id="7f9cc-104">Methods</span></span>  
  
|<span data-ttu-id="7f9cc-105">方法</span><span class="sxs-lookup"><span data-stu-id="7f9cc-105">Method</span></span>|<span data-ttu-id="7f9cc-106">描述</span><span class="sxs-lookup"><span data-stu-id="7f9cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f9cc-107">EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="7f9cc-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="7f9cc-108">取得 [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) 實例，其中包含在這部電腦上執行的受管理進程。</span><span class="sxs-lookup"><span data-stu-id="7f9cc-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="7f9cc-109">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="7f9cc-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="7f9cc-110">取得 [ICorPublishProcess](icorpublishprocess-interface.md) 實例，表示具有指定之識別碼的進程。</span><span class="sxs-lookup"><span data-stu-id="7f9cc-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f9cc-111">需求</span><span class="sxs-lookup"><span data-stu-id="7f9cc-111">Requirements</span></span>  

 <span data-ttu-id="7f9cc-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f9cc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f9cc-113">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="7f9cc-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7f9cc-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f9cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f9cc-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f9cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9cc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f9cc-116">See also</span></span>

- [<span data-ttu-id="7f9cc-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7f9cc-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7f9cc-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="7f9cc-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
