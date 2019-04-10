---
title: INotifySink2 介面
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f5307ce00160bb4151a7559daac4724367c6497
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157730"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="a27f9-102">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="a27f9-102">INotifySink2 Interface</span></span>
<span data-ttu-id="a27f9-103">宣告接收通知的方法。</span><span class="sxs-lookup"><span data-stu-id="a27f9-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a27f9-104">方法</span><span class="sxs-lookup"><span data-stu-id="a27f9-104">Methods</span></span>  
  
|<span data-ttu-id="a27f9-105">方法</span><span class="sxs-lookup"><span data-stu-id="a27f9-105">Method</span></span>|<span data-ttu-id="a27f9-106">描述</span><span class="sxs-lookup"><span data-stu-id="a27f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a27f9-107">OnSyncCallEnter 方法</span><span class="sxs-lookup"><span data-stu-id="a27f9-107">OnSyncCallEnter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="a27f9-108">取得叫用時進入呼叫。</span><span class="sxs-lookup"><span data-stu-id="a27f9-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="a27f9-109">OnSyncCallExit 方法</span><span class="sxs-lookup"><span data-stu-id="a27f9-109">OnSyncCallExit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="a27f9-110">結束呼叫時叫用。</span><span class="sxs-lookup"><span data-stu-id="a27f9-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="a27f9-111">OnSyncCallOut 方法</span><span class="sxs-lookup"><span data-stu-id="a27f9-111">OnSyncCallOut Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)|<span data-ttu-id="a27f9-112">取得叫用時呼叫已推出。</span><span class="sxs-lookup"><span data-stu-id="a27f9-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="a27f9-113">OnSyncCallReturn 方法</span><span class="sxs-lookup"><span data-stu-id="a27f9-113">OnSyncCallReturn Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="a27f9-114">取得叫用呼叫傳回時。</span><span class="sxs-lookup"><span data-stu-id="a27f9-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a27f9-115">需求</span><span class="sxs-lookup"><span data-stu-id="a27f9-115">Requirements</span></span>  
 <span data-ttu-id="a27f9-116">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a27f9-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27f9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a27f9-117">See also</span></span>

- [<span data-ttu-id="a27f9-118">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="a27f9-118">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="a27f9-119">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="a27f9-119">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="a27f9-120">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="a27f9-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
