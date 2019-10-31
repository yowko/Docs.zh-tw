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
ms.openlocfilehash: 9a2f513d40d722f1b0aad823ac7c0d93bda5615f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123265"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="c49dc-102">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="c49dc-102">MDAInfo Structure</span></span>
<span data-ttu-id="c49dc-103">提供 `Event_MDAFired` 事件的詳細資料，這會觸發建立 managed 偵錯工具（MDA）。</span><span class="sxs-lookup"><span data-stu-id="c49dc-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c49dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="c49dc-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="c49dc-105">Members</span><span class="sxs-lookup"><span data-stu-id="c49dc-105">Members</span></span>  
  
|<span data-ttu-id="c49dc-106">成員</span><span class="sxs-lookup"><span data-stu-id="c49dc-106">Member</span></span>|<span data-ttu-id="c49dc-107">描述</span><span class="sxs-lookup"><span data-stu-id="c49dc-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="c49dc-108">目前 MDA 的標題。</span><span class="sxs-lookup"><span data-stu-id="c49dc-108">The title of the current MDA.</span></span> <span data-ttu-id="c49dc-109">標題描述觸發 `Event_MDAFired` 事件的失敗類型。</span><span class="sxs-lookup"><span data-stu-id="c49dc-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="c49dc-110">目前 MDA 所提供的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="c49dc-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c49dc-111">備註</span><span class="sxs-lookup"><span data-stu-id="c49dc-111">Remarks</span></span>  
 <span data-ttu-id="c49dc-112">Managed 偵錯工具（Mda）是與 common language runtime （CLR）搭配使用的偵錯工具，可執行工作，例如識別執行時間執行引擎中的無效條件，或傾印有關的狀態的其他資訊。搜尋引擎優化.</span><span class="sxs-lookup"><span data-stu-id="c49dc-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="c49dc-113">Mda 會產生有關事件的 XML 訊息，而這種情況很容易被陷阱。</span><span class="sxs-lookup"><span data-stu-id="c49dc-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="c49dc-114">它們特別適用于在 managed 和非受控碼之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="c49dc-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="c49dc-115">當觸發建立 MDA 的事件引發時，執行時間會採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c49dc-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="c49dc-116">如果主機未藉由呼叫[ICLROnEventManager：： RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)來註冊[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)實例，以便收到 `Event_MDAFired` 事件的通知，則執行時間會繼續執行其預設的非裝載行為。</span><span class="sxs-lookup"><span data-stu-id="c49dc-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="c49dc-117">如果主機已註冊此事件的處理常式，執行時間會檢查偵錯工具是否已附加至進程。</span><span class="sxs-lookup"><span data-stu-id="c49dc-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="c49dc-118">如果是，執行時間會中斷偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c49dc-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="c49dc-119">當偵錯工具繼續時，它會呼叫主機。</span><span class="sxs-lookup"><span data-stu-id="c49dc-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="c49dc-120">如果未附加任何偵錯工具，執行時間會呼叫 `IActionOnCLREvent::OnEvent` 並將指標傳遞至 `MDAInfo` 實例，做為 `data` 參數。</span><span class="sxs-lookup"><span data-stu-id="c49dc-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="c49dc-121">主機可以選擇啟動 Mda，並在啟用 MDA 時收到通知。</span><span class="sxs-lookup"><span data-stu-id="c49dc-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="c49dc-122">這可讓主機有機會覆寫預設行為，並中止引發事件的 managed 執行緒，以防止它損毀進程狀態。</span><span class="sxs-lookup"><span data-stu-id="c49dc-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="c49dc-123">如需使用 Mda 的詳細資訊，請參閱[診斷 Managed 偵錯工具的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="c49dc-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c49dc-124">需求</span><span class="sxs-lookup"><span data-stu-id="c49dc-124">Requirements</span></span>  
 <span data-ttu-id="c49dc-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c49dc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c49dc-126">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="c49dc-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c49dc-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c49dc-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c49dc-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c49dc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49dc-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="c49dc-129">See also</span></span>

- [<span data-ttu-id="c49dc-130">裝載結構</span><span class="sxs-lookup"><span data-stu-id="c49dc-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="c49dc-131">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="c49dc-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
