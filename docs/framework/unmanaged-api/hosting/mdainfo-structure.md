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
ms.openlocfilehash: 517e0ae7fb5d5151f94f82d9146ebbf40bad2ef9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503857"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="c4af7-102">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="c4af7-102">MDAInfo Structure</span></span>
<span data-ttu-id="c4af7-103">提供事件的相關詳細資料 `Event_MDAFired` ，這會觸發建立 managed 偵錯工具（MDA）。</span><span class="sxs-lookup"><span data-stu-id="c4af7-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4af7-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4af7-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="c4af7-105">成員</span><span class="sxs-lookup"><span data-stu-id="c4af7-105">Members</span></span>  
  
|<span data-ttu-id="c4af7-106">成員</span><span class="sxs-lookup"><span data-stu-id="c4af7-106">Member</span></span>|<span data-ttu-id="c4af7-107">說明</span><span class="sxs-lookup"><span data-stu-id="c4af7-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="c4af7-108">目前 MDA 的標題。</span><span class="sxs-lookup"><span data-stu-id="c4af7-108">The title of the current MDA.</span></span> <span data-ttu-id="c4af7-109">標題描述觸發事件的失敗類型 `Event_MDAFired` 。</span><span class="sxs-lookup"><span data-stu-id="c4af7-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="c4af7-110">目前 MDA 所提供的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="c4af7-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4af7-111">備註</span><span class="sxs-lookup"><span data-stu-id="c4af7-111">Remarks</span></span>  
 <span data-ttu-id="c4af7-112">Managed 偵錯工具（Mda）是與 common language runtime （CLR）搭配使用的偵錯工具，可執行工作，例如識別執行時間執行引擎中的無效條件，或傾印引擎狀態的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c4af7-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="c4af7-113">Mda 會產生有關事件的 XML 訊息，而這種情況很容易被陷阱。</span><span class="sxs-lookup"><span data-stu-id="c4af7-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="c4af7-114">它們特別適用于在 managed 和非受控碼之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="c4af7-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="c4af7-115">當觸發建立 MDA 的事件引發時，執行時間會採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c4af7-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="c4af7-116">如果主機未藉由呼叫[ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)來註冊[IActionOnCLREvent](iactiononclrevent-interface.md)實例以收到事件的通知 `Event_MDAFired` ，執行時間會繼續執行其預設的非裝載行為。</span><span class="sxs-lookup"><span data-stu-id="c4af7-116">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="c4af7-117">如果主機已註冊此事件的處理常式，執行時間會檢查偵錯工具是否已附加至進程。</span><span class="sxs-lookup"><span data-stu-id="c4af7-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="c4af7-118">如果是，執行時間會中斷偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c4af7-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="c4af7-119">當偵錯工具繼續時，它會呼叫主機。</span><span class="sxs-lookup"><span data-stu-id="c4af7-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="c4af7-120">如果未附加任何偵錯工具，執行時間會呼叫 `IActionOnCLREvent::OnEvent` ，並將實例的指標當做 `MDAInfo` 參數傳遞 `data` 。</span><span class="sxs-lookup"><span data-stu-id="c4af7-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="c4af7-121">主機可以選擇啟動 Mda，並在啟用 MDA 時收到通知。</span><span class="sxs-lookup"><span data-stu-id="c4af7-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="c4af7-122">這可讓主機有機會覆寫預設行為，並中止引發事件的 managed 執行緒，以防止它損毀進程狀態。</span><span class="sxs-lookup"><span data-stu-id="c4af7-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="c4af7-123">如需使用 Mda 的詳細資訊，請參閱[診斷 Managed 偵錯工具的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="c4af7-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4af7-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="c4af7-124">Requirements</span></span>  
 <span data-ttu-id="c4af7-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4af7-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4af7-126">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="c4af7-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c4af7-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c4af7-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4af7-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4af7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4af7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4af7-129">See also</span></span>

- [<span data-ttu-id="c4af7-130">裝載結構</span><span class="sxs-lookup"><span data-stu-id="c4af7-130">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="c4af7-131">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="c4af7-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
