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
ms.openlocfilehash: 1b87ccc3d6c3e957d0384499048032e35247093a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436477"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="846c3-102">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="846c3-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="846c3-103">定義方法，讓主應用程式取得要求的工作的相關資訊，並在同步處理實作偵測死結。</span><span class="sxs-lookup"><span data-stu-id="846c3-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="846c3-104">方法</span><span class="sxs-lookup"><span data-stu-id="846c3-104">Methods</span></span>  
  
|<span data-ttu-id="846c3-105">方法</span><span class="sxs-lookup"><span data-stu-id="846c3-105">Method</span></span>|<span data-ttu-id="846c3-106">描述</span><span class="sxs-lookup"><span data-stu-id="846c3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="846c3-107">CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="846c3-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="846c3-108">Common language runtime (CLR) 建立的主機可用來判斷一組工作正在等候讀取器-寫入器鎖定之迭代器的要求。</span><span class="sxs-lookup"><span data-stu-id="846c3-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="846c3-109">DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="846c3-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="846c3-110">要求 CLR 終結迭代器所建立的呼叫`CreateRWLockOwnerIterator`。</span><span class="sxs-lookup"><span data-stu-id="846c3-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="846c3-111">GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="846c3-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="846c3-112">取得擁有指定的監視的工作。</span><span class="sxs-lookup"><span data-stu-id="846c3-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="846c3-113">GetRWLockOwnerNext 方法</span><span class="sxs-lookup"><span data-stu-id="846c3-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="846c3-114">取得正在等候目前的讀取器-寫入器鎖定下一個工作。</span><span class="sxs-lookup"><span data-stu-id="846c3-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="846c3-115">需求</span><span class="sxs-lookup"><span data-stu-id="846c3-115">Requirements</span></span>  
 <span data-ttu-id="846c3-116">**平台：** 看到[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="846c3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="846c3-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="846c3-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="846c3-118">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="846c3-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="846c3-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846c3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846c3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="846c3-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="846c3-121">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="846c3-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="846c3-122">[Managed 和 Unmanaged 執行緒處理](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="846c3-122">[Managed and Unmanaged Threading](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span></span>  
 [<span data-ttu-id="846c3-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="846c3-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
