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
ms.openlocfilehash: c7afe074afb9b38d6fefa1192799120dbb50b403
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442055"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="d4afd-102">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="d4afd-102">INotifySink2 Interface</span></span>
<span data-ttu-id="d4afd-103">宣告接收器通知的方法。</span><span class="sxs-lookup"><span data-stu-id="d4afd-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4afd-104">方法</span><span class="sxs-lookup"><span data-stu-id="d4afd-104">Methods</span></span>  
  
|<span data-ttu-id="d4afd-105">方法</span><span class="sxs-lookup"><span data-stu-id="d4afd-105">Method</span></span>|<span data-ttu-id="d4afd-106">描述</span><span class="sxs-lookup"><span data-stu-id="d4afd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4afd-107">OnSyncCallEnter 方法</span><span class="sxs-lookup"><span data-stu-id="d4afd-107">OnSyncCallEnter Method</span></span>](inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="d4afd-108">在輸入呼叫時叫用。</span><span class="sxs-lookup"><span data-stu-id="d4afd-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="d4afd-109">OnSyncCallExit 方法</span><span class="sxs-lookup"><span data-stu-id="d4afd-109">OnSyncCallExit Method</span></span>](inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="d4afd-110">會在結束呼叫時叫用。</span><span class="sxs-lookup"><span data-stu-id="d4afd-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="d4afd-111">OnSyncCallOut 方法</span><span class="sxs-lookup"><span data-stu-id="d4afd-111">OnSyncCallOut Method</span></span>](inotifysink2-onsynccallout-method.md)|<span data-ttu-id="d4afd-112">當呼叫完成時，就會叫用。</span><span class="sxs-lookup"><span data-stu-id="d4afd-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="d4afd-113">OnSyncCallReturn 方法</span><span class="sxs-lookup"><span data-stu-id="d4afd-113">OnSyncCallReturn Method</span></span>](inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="d4afd-114">當呼叫傳回時，就會叫用。</span><span class="sxs-lookup"><span data-stu-id="d4afd-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4afd-115">需求</span><span class="sxs-lookup"><span data-stu-id="d4afd-115">Requirements</span></span>  
 <span data-ttu-id="d4afd-116">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="d4afd-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4afd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4afd-117">See also</span></span>

- [<span data-ttu-id="d4afd-118">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="d4afd-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="d4afd-119">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="d4afd-119">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="d4afd-120">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="d4afd-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
