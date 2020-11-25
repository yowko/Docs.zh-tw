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
ms.openlocfilehash: 8e88d90e3291d21888fae7aa162f84b6377658c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730015"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="5800a-102">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="5800a-102">MDAInfo Structure</span></span>

<span data-ttu-id="5800a-103">提供事件的詳細資料 `Event_MDAFired` ，這會觸發 (MDA) 的 managed 偵錯工具建立。</span><span class="sxs-lookup"><span data-stu-id="5800a-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5800a-104">語法</span><span class="sxs-lookup"><span data-stu-id="5800a-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="5800a-105">成員</span><span class="sxs-lookup"><span data-stu-id="5800a-105">Members</span></span>  
  
|<span data-ttu-id="5800a-106">member</span><span class="sxs-lookup"><span data-stu-id="5800a-106">Member</span></span>|<span data-ttu-id="5800a-107">描述</span><span class="sxs-lookup"><span data-stu-id="5800a-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="5800a-108">目前 MDA 的標題。</span><span class="sxs-lookup"><span data-stu-id="5800a-108">The title of the current MDA.</span></span> <span data-ttu-id="5800a-109">標題描述觸發事件的失敗類型 `Event_MDAFired` 。</span><span class="sxs-lookup"><span data-stu-id="5800a-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="5800a-110">目前的 MDA 所提供的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="5800a-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5800a-111">備註</span><span class="sxs-lookup"><span data-stu-id="5800a-111">Remarks</span></span>  

 <span data-ttu-id="5800a-112">Managed 偵錯工具 (Mda) 是與 common language runtime 搭配使用的偵錯工具， (CLR) 來執行工作，例如在執行時間執行引擎中找出不正確條件，或是傾印引擎狀態的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5800a-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="5800a-113">Mda 會產生有關事件的 XML 訊息，而這種情況很難進行陷阱。</span><span class="sxs-lookup"><span data-stu-id="5800a-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="5800a-114">它們特別適用于在 managed 和非受控碼之間的轉換進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5800a-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="5800a-115">引發觸發建立 MDA 的事件時，執行時間會採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5800a-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="5800a-116">如果主機尚未藉由呼叫[ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)註冊[IActionOnCLREvent](iactiononclrevent-interface.md)實例來通知 `Event_MDAFired` 事件，執行時間會繼續其預設的非裝載行為。</span><span class="sxs-lookup"><span data-stu-id="5800a-116">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="5800a-117">如果主機已註冊這個事件的處理常式，執行時間會檢查偵錯工具是否已附加至進程。</span><span class="sxs-lookup"><span data-stu-id="5800a-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="5800a-118">如果是，執行時間會中斷進入偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5800a-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="5800a-119">當偵錯工具繼續時，它會呼叫主機。</span><span class="sxs-lookup"><span data-stu-id="5800a-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="5800a-120">如果未附加任何偵錯工具，執行時間會呼叫 `IActionOnCLREvent::OnEvent` ，並將指標傳遞至 `MDAInfo` 實例作為 `data` 參數。</span><span class="sxs-lookup"><span data-stu-id="5800a-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="5800a-121">主機可以選擇啟用 Mda，並且在啟用 MDA 時收到通知。</span><span class="sxs-lookup"><span data-stu-id="5800a-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="5800a-122">這可讓主機有機會覆寫預設行為，並中止引發事件的 managed 執行緒，以防止它損毀進程狀態。</span><span class="sxs-lookup"><span data-stu-id="5800a-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="5800a-123">如需使用 Mda 的詳細資訊，請參閱 [診斷 Managed 偵錯工具的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="5800a-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5800a-124">需求</span><span class="sxs-lookup"><span data-stu-id="5800a-124">Requirements</span></span>  

 <span data-ttu-id="5800a-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5800a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5800a-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5800a-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5800a-127">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5800a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5800a-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5800a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5800a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5800a-129">See also</span></span>

- [<span data-ttu-id="5800a-130">裝載結構</span><span class="sxs-lookup"><span data-stu-id="5800a-130">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="5800a-131">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="5800a-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
