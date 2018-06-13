---
title: MDAInfo 結構
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5164e85ecc97de99dcc493c2ba5efa8fc3468471
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443176"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="39f9d-102">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="39f9d-102">MDAInfo Structure</span></span>
<span data-ttu-id="39f9d-103">提供有關的詳細資料`Event_MDAFired`事件，以觸發建立的 managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="39f9d-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="39f9d-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="39f9d-105">成員</span><span class="sxs-lookup"><span data-stu-id="39f9d-105">Members</span></span>  
  
|<span data-ttu-id="39f9d-106">成員</span><span class="sxs-lookup"><span data-stu-id="39f9d-106">Member</span></span>|<span data-ttu-id="39f9d-107">描述</span><span class="sxs-lookup"><span data-stu-id="39f9d-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="39f9d-108">目前的 MDA 的標題。</span><span class="sxs-lookup"><span data-stu-id="39f9d-108">The title of the current MDA.</span></span> <span data-ttu-id="39f9d-109">標題描述觸發失敗種類`Event_MDAFired`事件。</span><span class="sxs-lookup"><span data-stu-id="39f9d-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="39f9d-110">提供目前 MDA 的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="39f9d-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39f9d-111">備註</span><span class="sxs-lookup"><span data-stu-id="39f9d-111">Remarks</span></span>  
 <span data-ttu-id="39f9d-112">Managed 偵錯助理 (Mda) runtime 執行引擎中的偵錯輔助工具，搭配使用與 common language runtime (CLR) 執行工作，例如識別無效的條件或傾印的狀態相關的其他資訊引擎。</span><span class="sxs-lookup"><span data-stu-id="39f9d-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="39f9d-113">Mda 會產生有關否則很難設陷事件的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="39f9d-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="39f9d-114">它們是特別適用於偵錯 managed 和 unmanaged 程式碼之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="39f9d-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="39f9d-115">觸發程序建立 MDA 事件引發時，執行階段會採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="39f9d-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="39f9d-116">如果主機尚未註冊[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)藉由呼叫的執行個體[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)的通知`Event_MDAFired`事件，執行階段會繼續進行其預設值，非裝載的行為。</span><span class="sxs-lookup"><span data-stu-id="39f9d-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="39f9d-117">如果此事件處理常式註冊的主機，執行階段會檢查是否要將偵錯工具附加至處理程序。</span><span class="sxs-lookup"><span data-stu-id="39f9d-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="39f9d-118">如果是，執行階段就會中斷偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="39f9d-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="39f9d-119">當偵錯工具會繼續時，它會呼叫主應用程式。</span><span class="sxs-lookup"><span data-stu-id="39f9d-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="39f9d-120">如果偵錯工具未附加時，執行階段會呼叫`IActionOnCLREvent::OnEvent`並傳遞指標`MDAInfo`執行個體做為`data`參數。</span><span class="sxs-lookup"><span data-stu-id="39f9d-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="39f9d-121">若要啟用 Mda 並啟動 MDA 時收到通知，可以選擇主應用程式。</span><span class="sxs-lookup"><span data-stu-id="39f9d-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="39f9d-122">這可讓主應用程式覆寫預設行為，並中止的 managed 的執行緒引發事件，以避免損毀處理序狀態。</span><span class="sxs-lookup"><span data-stu-id="39f9d-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="39f9d-123">如需使用 Mda 的詳細資訊，請參閱[診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="39f9d-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39f9d-124">需求</span><span class="sxs-lookup"><span data-stu-id="39f9d-124">Requirements</span></span>  
 <span data-ttu-id="39f9d-125">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39f9d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39f9d-126">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="39f9d-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="39f9d-127">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="39f9d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39f9d-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39f9d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f9d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39f9d-129">See Also</span></span>  
 [<span data-ttu-id="39f9d-130">裝載結構</span><span class="sxs-lookup"><span data-stu-id="39f9d-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="39f9d-131">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="39f9d-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
