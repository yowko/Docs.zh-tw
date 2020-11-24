---
title: ICLRSyncManager 介面
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: 5bfab21a36becf943b1813f266cf70c4b5e5b1d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690989"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="a7090-102">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a7090-102">ICLRSyncManager Interface</span></span>

<span data-ttu-id="a7090-103">定義方法，可讓主機取得所要求之工作的相關資訊，並偵測其同步處理執行中的鎖死。</span><span class="sxs-lookup"><span data-stu-id="a7090-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7090-104">方法</span><span class="sxs-lookup"><span data-stu-id="a7090-104">Methods</span></span>  
  
|<span data-ttu-id="a7090-105">方法</span><span class="sxs-lookup"><span data-stu-id="a7090-105">Method</span></span>|<span data-ttu-id="a7090-106">描述</span><span class="sxs-lookup"><span data-stu-id="a7090-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7090-107">CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="a7090-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="a7090-108">要求 common language runtime (CLR) 為主機建立反覆運算器，以用來判斷等候讀取器寫入器鎖定的工作集。</span><span class="sxs-lookup"><span data-stu-id="a7090-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="a7090-109">DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="a7090-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="a7090-110">要求 CLR 終結由的呼叫所建立的反覆運算器 `CreateRWLockOwnerIterator` 。</span><span class="sxs-lookup"><span data-stu-id="a7090-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="a7090-111">GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="a7090-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="a7090-112">取得擁有指定之監視的工作。</span><span class="sxs-lookup"><span data-stu-id="a7090-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="a7090-113">GetRWLockOwnerNext 方法</span><span class="sxs-lookup"><span data-stu-id="a7090-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="a7090-114">取得正在等候目前讀取器寫入器鎖定的下一個工作。</span><span class="sxs-lookup"><span data-stu-id="a7090-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7090-115">需求</span><span class="sxs-lookup"><span data-stu-id="a7090-115">Requirements</span></span>  

 <span data-ttu-id="a7090-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7090-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7090-117">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a7090-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7090-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a7090-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7090-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7090-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7090-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7090-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="a7090-121">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a7090-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="a7090-122">[Managed 和 Unmanaged 執行緒](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a7090-122">[Managed and Unmanaged Threading](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="a7090-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a7090-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
