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
ms.openlocfilehash: 255fe51f86157842a5807145bf7c58ae1ff5ba8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720018"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="f75ed-102">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="f75ed-102">INotifySink2 Interface</span></span>

<span data-ttu-id="f75ed-103">宣告接收通知的方法。</span><span class="sxs-lookup"><span data-stu-id="f75ed-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f75ed-104">方法</span><span class="sxs-lookup"><span data-stu-id="f75ed-104">Methods</span></span>  
  
|<span data-ttu-id="f75ed-105">方法</span><span class="sxs-lookup"><span data-stu-id="f75ed-105">Method</span></span>|<span data-ttu-id="f75ed-106">描述</span><span class="sxs-lookup"><span data-stu-id="f75ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f75ed-107">OnSyncCallEnter 方法</span><span class="sxs-lookup"><span data-stu-id="f75ed-107">OnSyncCallEnter Method</span></span>](inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="f75ed-108">在輸入呼叫時叫用。</span><span class="sxs-lookup"><span data-stu-id="f75ed-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="f75ed-109">OnSyncCallExit 方法</span><span class="sxs-lookup"><span data-stu-id="f75ed-109">OnSyncCallExit Method</span></span>](inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="f75ed-110">在結束呼叫時叫用。</span><span class="sxs-lookup"><span data-stu-id="f75ed-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="f75ed-111">OnSyncCallOut 方法</span><span class="sxs-lookup"><span data-stu-id="f75ed-111">OnSyncCallOut Method</span></span>](inotifysink2-onsynccallout-method.md)|<span data-ttu-id="f75ed-112">在呼叫超時時叫用。</span><span class="sxs-lookup"><span data-stu-id="f75ed-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="f75ed-113">OnSyncCallReturn 方法</span><span class="sxs-lookup"><span data-stu-id="f75ed-113">OnSyncCallReturn Method</span></span>](inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="f75ed-114">當呼叫傳回時，就會叫用。</span><span class="sxs-lookup"><span data-stu-id="f75ed-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f75ed-115">需求</span><span class="sxs-lookup"><span data-stu-id="f75ed-115">Requirements</span></span>  

 <span data-ttu-id="f75ed-116">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="f75ed-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f75ed-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f75ed-117">See also</span></span>

- [<span data-ttu-id="f75ed-118">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="f75ed-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="f75ed-119">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="f75ed-119">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="f75ed-120">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="f75ed-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
