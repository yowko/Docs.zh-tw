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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e4affa363083ce55ac3764c26412a0d60ba3f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763577"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="3338a-102">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3338a-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="3338a-103">定義方法，可讓主應用程式取得要求的工作的相關資訊，以及偵測死結的同步處理實作中。</span><span class="sxs-lookup"><span data-stu-id="3338a-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3338a-104">方法</span><span class="sxs-lookup"><span data-stu-id="3338a-104">Methods</span></span>  
  
|<span data-ttu-id="3338a-105">方法</span><span class="sxs-lookup"><span data-stu-id="3338a-105">Method</span></span>|<span data-ttu-id="3338a-106">描述</span><span class="sxs-lookup"><span data-stu-id="3338a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3338a-107">CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="3338a-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="3338a-108">Common language runtime (CLR) 建立迭代器，用來判斷一組工作正在等候讀取器-寫入器鎖定主機的要求。</span><span class="sxs-lookup"><span data-stu-id="3338a-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="3338a-109">DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="3338a-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="3338a-110">要求的 CLR，損毀的呼叫所建立的迭代器`CreateRWLockOwnerIterator`。</span><span class="sxs-lookup"><span data-stu-id="3338a-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="3338a-111">GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="3338a-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="3338a-112">取得擁有指定的監視的工作。</span><span class="sxs-lookup"><span data-stu-id="3338a-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="3338a-113">GetRWLockOwnerNext 方法</span><span class="sxs-lookup"><span data-stu-id="3338a-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="3338a-114">取得正在等候目前的讀取器-寫入器鎖定下一個工作。</span><span class="sxs-lookup"><span data-stu-id="3338a-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3338a-115">需求</span><span class="sxs-lookup"><span data-stu-id="3338a-115">Requirements</span></span>  
 <span data-ttu-id="3338a-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3338a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3338a-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3338a-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3338a-118">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3338a-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3338a-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3338a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3338a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3338a-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="3338a-121">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3338a-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="3338a-122">[Managed 和 Unmanaged 執行緒處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3338a-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="3338a-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="3338a-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
